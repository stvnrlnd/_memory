---
title: nvst.chat
type: project
area: "[[steven-roland]]"
status: in-development
tags:
  - trading
  - automation
  - ai
  - personal
created: 2026-04-15
---

# nvst.chat — Overview

## What It Is

nvst.chat is a personal automated stock trading bot built in Laravel. It connects to [Alpaca Markets](https://alpaca.markets) to generate trading signals and execute orders automatically during US market hours. The bot is designed to run with a modest budget (~$100) and makes position sizing decisions as a percentage of portfolio value.

The project lives outside Segment Holdings — it is strictly personal, under Steven Roland's own name. Code lives at `~/Work/_code/nvst.chat/` (the original directory name).

## How It Works

1. **Signal Generation** — Every 5 minutes during market hours, the bot runs `trading:run`. For each active symbol on the watchlist, it generates a Buy, Sell, or Hold signal using the configured strategy.
2. **Execution** — Non-Hold signals are dispatched to `ExecuteTradeJob`, which submits a market order to Alpaca if `ALPACA_TRADING_ENABLED=true`.
3. **Portfolio Sync** — `SyncPortfolioJob` runs every minute during market hours to keep local position state current from Alpaca.

## Strategies

| Strategy | Key | Description |
|---|---|---|
| SMA Crossover | `sma_crossover` (default) | 5-period vs 20-period simple moving average crossover. No API cost. |
| AI (Claude Haiku) | `ai` | Sends recent price history to Claude Haiku, which returns a JSON signal with action, confidence, and reasoning. Requires `ANTHROPIC_API_KEY`. |

## Position Sizing

- **Per trade:** 5% of portfolio value (`ALPACA_POSITION_SIZE_PCT=0.05`)
- **Max per symbol:** 20% of portfolio value (`ALPACA_MAX_POSITION_PCT=0.20`)
- The bot checks the existing position before adding to avoid exceeding the max.

## Safety Controls

| Control | Default | Purpose |
|---|---|---|
| `ALPACA_TRADING_ENABLED` | `false` | Master kill-switch. `false` = signals only, no orders submitted. |
| `ALPACA_PAPER` | `true` | Routes all orders to Alpaca's paper trading environment. |

Start with both defaults. Enable trading only when ready: set `ALPACA_TRADING_ENABLED=true` (still safe with `ALPACA_PAPER=true`). Switch to live by setting `ALPACA_PAPER=false`.

## UI

The app has a Livewire/Flux dashboard at `http://localhost` (or the production domain) with six views:

- **Dashboard** — Portfolio value, buying power, day P&L, status badges, recent signals and trades
- **Watchlist** — Add/pause/remove symbols to watch
- **Discover** — Browse top gainers, losers, and most-active stocks; add to watchlist in one click
- **Positions** — Open positions synced from Alpaca with unrealized P&L
- **Signals** — Full signal log with manual trigger buttons per symbol
- **Trade History** — Filterable list of all submitted orders

## Status

In development. Running locally via Laravel Sail. Paper trading mode active. No live trades executed yet.

---

## Further Reading

- [[nvst.chat/tech-stack|Tech Stack]]
- [[nvst.chat/changelog|Changelog]]
