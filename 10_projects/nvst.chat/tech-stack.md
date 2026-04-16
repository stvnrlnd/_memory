---
title: nvst.chat — Tech Stack
type: project
created: 2026-04-15
---

# nvst.chat — Tech Stack

## Core

| Layer | Technology |
|---|---|
| Framework | Laravel 13 / PHP 8.5 |
| Frontend | Livewire 4 + Flux UI v2 (SFC components) |
| Styling | Tailwind CSS v4 |
| Queue | Laravel Queue (Redis via Sail) |
| Scheduler | Laravel Scheduler via `routes/console.php` |
| Database | MySQL (Laravel Sail / Docker) |
| Dev Environment | Laravel Sail (Docker) |

## External APIs

| API | Purpose |
|---|---|
| [Alpaca Markets](https://alpaca.markets) | Broker API — account data, positions, market data, order submission |
| Anthropic (Claude Haiku) | AI signal strategy (optional, `ALPACA_STRATEGY=ai`) |

## Application Architecture

```
AlpacaService          — Low-level REST wrapper for Alpaca (trading + data endpoints)
MarketDataService      — Price lookups, bar history, SMA calculation, position price sync
SignalService          — Strategy dispatcher → SMA crossover or AI via Claude Haiku
TradingService         — Portfolio sync, position sizing, order execution, pending order polling
```

## Jobs

| Job | Purpose |
|---|---|
| `SyncPortfolioJob` | Syncs positions from Alpaca every minute during market hours |
| `FetchMarketDataJob` | On-demand market data fetch (used in pipeline) |
| `GenerateSignalJob` | Generates a signal for a given symbol |
| `ExecuteTradeJob` | Submits a market order to Alpaca for a given signal |

## Artisan Commands

| Command | Purpose |
|---|---|
| `trading:run` | Orchestrates the full cycle: sync → generate signals → dispatch trades |

## Schedule

```
trading:run        every 5 min  weekdays  9:30–16:00 ET  withoutOverlapping
SyncPortfolioJob   every 1 min  weekdays  9:30–16:05 ET  withoutOverlapping
```

## Data Models

| Model | Key Fields |
|---|---|
| `Stock` | symbol, name, is_active, notes |
| `Position` | symbol, qty, avg_entry_price, current_price, market_value, unrealized_pl, synced_at |
| `Signal` | symbol, action (buy/sell/hold), price_at_signal, confidence, reason, executed |
| `Trade` | symbol, side, qty, order_type, status, filled_avg_price, alpaca_order_id, signal_id |

## Environment Variables

```env
ALPACA_KEY=
ALPACA_SECRET=
ALPACA_PAPER=true
ALPACA_TRADING_ENABLED=false
ALPACA_STRATEGY=sma_crossover
ALPACA_SMA_SHORT=5
ALPACA_SMA_LONG=20
ALPACA_POSITION_SIZE_PCT=0.05
ALPACA_MAX_POSITION_PCT=0.20
ANTHROPIC_API_KEY=          # only needed for ALPACA_STRATEGY=ai
```

## Code Location

`~/Work/_code/nvst.chat/` — Laravel app, own git repo.
