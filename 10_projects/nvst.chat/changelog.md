---
title: nvst.chat — Changelog
type: project
created: 2026-04-15
---

# nvst.chat — Changelog

## 2026-04-15 — Initial Build

**Built from scratch in a single session.**

### Infrastructure
- Laravel 13 + Sail (Docker: MySQL, Redis, Soketi)
- Configured `config/alpaca.php` with credentials, paper mode toggle, trading kill-switch, strategy and position sizing settings
- Added Anthropic API key support to `config/services.php`

### Database
- Migrations for `stocks`, `positions`, `signals`, `trades`
- Full factory definitions for all four models with realistic states

### Models & Enums
- `Stock`, `Position`, `Signal`, `Trade` models with casts, scopes, and relationships
- `SignalAction`, `TradeSide`, `TradeStatus`, `OrderType` PHP 8 backed enums

### Services
- `AlpacaService` — REST wrapper for Alpaca trading and data endpoints
- `MarketDataService` — Price fetching, bar history, SMA helper, position price refresh
- `SignalService` — SMA crossover strategy (default) + AI strategy via Claude Haiku
- `TradingService` — Portfolio sync, position sizing logic, order execution, pending order polling

### Jobs & Commands
- `SyncPortfolioJob`, `FetchMarketDataJob`, `GenerateSignalJob`, `ExecuteTradeJob`
- `trading:run` Artisan command — full cycle orchestrator
- Scheduler: `trading:run` every 5 min + `SyncPortfolioJob` every minute, both weekdays 9:30–4pm ET

### UI (Livewire 4 + Flux UI v2)
- Dashboard — portfolio stats, status badges (paper/live, market open, trading enabled), recent signals & trades
- Watchlist — add/pause/remove symbols
- Positions — open positions with sync button and unrealized P&L
- Signals — full log with per-symbol manual trigger buttons
- Trade History — paginated and filterable

### Bugs Fixed
- MySQL container not attached to Docker network on first Sail start — resolved with `docker network connect`
- `MultipleRootElementsDetectedException` on all Livewire pages — fixed by replacing `<x-layouts::app>` wrappers with `#[Layout('layouts.app')]` PHP attribute + single `<div>` root per template
- `flux::columns` component not found — fixed by using correct Flux v2 table sub-component names: `<flux:table.columns>`, `<flux:table.rows>`, etc.
