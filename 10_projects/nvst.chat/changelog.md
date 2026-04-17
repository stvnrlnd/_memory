---
title: nvst.chat — Changelog
type: project
created: 2026-04-15
---

# nvst.chat — Changelog

## 2026-04-16 — Laravel Horizon

- Installed `laravel/horizon` ^5.45; published config and `HorizonServiceProvider`
- Switched `QUEUE_CONNECTION` from `database` to `redis` in `.env.example`; added `REDIS_*` vars
- Configured two supervisors in `config/horizon.php`:
  - `supervisor-trading` — `trading` queue, `simple` balance, 1 try, 30s timeout; handles `ExecuteTradeJob`, `GenerateSignalJob`, `OrbEntryJob`, `OrbExitJob`
  - `supervisor-sync` — `sync` + `default` queues, `auto` balance, 3 tries, 120s timeout; handles all `Sync*` and `FetchMarketDataJob`
- Added `public string $queue` to all 10 jobs (`trading` for execution/signal/ORB, `sync` for market data and portfolio sync)
- `HorizonServiceProvider::gate()` — allows `steven@segment.team`
- `composer dev` script: replaced `queue:listen` with `php artisan horizon`
- Dashboard available at `/horizon`

## 2026-04-16 — Dual Watchlist (Auto + Manual)

### Automated Watchlist
- `stocks` table: added `source` varchar (default `'manual'`) and `last_seen_at` timestamp
- `Stock` model: added `scopeManual()`, `scopeAuto()`, `scopeStale(int $days)`, `isManual()`, `isAuto()` helpers
- `SyncAutoWatchlistJob` — runs at 4:30 PM ET weekdays; pulls top N symbols from `getMostActives()` + `getTopMovers()` (gainers), deduplicates, upserts into `stocks` with `source='auto'`, `is_active=true`, `last_seen_at=now()`; deactivates auto symbols not seen within `ALPACA_AUTO_WATCHLIST_STALE_DAYS` (default 7); never modifies `source='manual'` rows; both API feeds fail independently without blocking the other
- Config keys: `ALPACA_AUTO_WATCHLIST_ENABLED` (default true), `ALPACA_AUTO_WATCHLIST_SIZE` (default 50), `ALPACA_AUTO_WATCHLIST_STALE_DAYS` (default 7)
- Scheduler: `SyncAutoWatchlistJob` at 4:30 PM → `screener:run` at 8 PM → `OrbEntryJob` at 9:31 AM → `OrbExitJob` at 9:50 AM

### Tests (78 passing)
- `SyncAutoWatchlistJobTest` — 12 tests: adds from most-actives, adds from gainers, deduplicates, updates last_seen_at, never touches manual stocks, deactivates stale auto symbols, preserves fresh auto symbols, resilient to single-feed failures, bails when both feeds fail, respects enabled flag

## 2026-04-16 — ORB Strategy + Universe Screener

### Opening Range Breakout (ORB) Strategy
- `DailyPlay` model + `daily_plays` migration — one record per trading day tracking the ORB play lifecycle (pending → entered → exited/skipped); columns: symbol, date (unique), status, skip_reason, entry_signal_id FK, exit_signal_id FK, entered_at, exited_at
- `OrbEntryJob` — dispatched at 9:31 AM ET weekdays; picks top `ScreenerCandidate` for today, runs pre-flight checks (trading enabled, market open, screener candidate exists, macro not bearish, price fetchable), creates Buy signal, calls `TradingService::executeSignal()`; always creates a `DailyPlay` record (entered or skipped)
- `OrbExitJob` — dispatched at 9:50 AM ET weekdays; hard unconditional exit; finds today's entered `DailyPlay`, creates Sell signal, calls `executeSignal()`; marks play exited even if position was already closed by stop-loss
- Both jobs added to scheduler with `withoutOverlapping()`

### Universe Screener
- `AlpacaService::getBarsBulk()` — fetches 30-day OHLCV bars for multiple symbols in a single API call (`/v2/stocks/bars?symbols=...`); eliminates N serial API calls in screener runs
- `ScreenerService` refactored to use `getBarsBulk()` for all scoring; falls back to per-symbol `getBars()` if bulk endpoint fails
- Universe mode (`ALPACA_SCREENER_USE_UNIVERSE=true`): merges active watchlist with top N most-active symbols from Alpaca (`getMostActives`), deduplicates, then bulk-scores all candidates — fully hands-off, no manual watchlist curation needed
- Config keys added: `ALPACA_SCREENER_USE_UNIVERSE` (default false), `ALPACA_SCREENER_UNIVERSE_SIZE` (default 50)
- Most-actives API failure degrades gracefully to watchlist-only mode

### Tests (66 passing)
- `OrbJobsTest` — 13 tests: entry happy path, idempotency, all skip conditions (trading disabled, market closed, no candidates, bearish macro, no price, executeSignal blocked), picks highest-scored candidate, exit happy path, no play today, position already closed, executeSignal null on exit
- `UniverseScreenerTest` — 6 tests: bulk bar scoring, missing symbol in bulk response, bulk fallback to per-symbol, universe merge, deduplication, most-actives failure fallback
- `makeBars()` helper moved to `tests/Pest.php` (globally available to all test files)

## 2026-04-16 — Hardening + Screener

### Production Bug Fix
- `AlpacaService::data()` — added `connectTimeout(3)` and `timeout(8)` to prevent 10s cURL failures from causing multi-symbol cycles to exceed the 5-minute `withoutOverlapping()` window and lock the scheduler

### Signal Improvements
- **Signal cooldown** — `Signal::isOnCooldown()` checks for a recent non-Hold signal before generating a new one; configurable via `ALPACA_SIGNAL_COOLDOWN_MINUTES` (default 30 min)
- **Stop-loss** — `TradingService::checkStopLosses()` runs each cycle after portfolio sync; dispatches `ExecuteTradeJob` for positions breaching `ALPACA_STOP_LOSS_PCT` (default -5%)

### AI Foundation
- Installed `laravel/ai ^0.6`; published `config/ai.php` with Anthropic as default provider
- Created `App\Ai\Agents\TradingSignalAgent` — structured output agent with `#[Provider('anthropic')]` + `#[Model('claude-haiku-4-5-20251001')]`; schema enforces `action/confidence/reason`
- Refactored `SignalService::generateAiSignal()` to use the agent instead of raw `Http::` calls

### Nightly Screener
- New `ScreenerCandidate` model + `screener_candidates` migration (symbol, score, price, atr, atr_pct, sma5, sma20, up_days, disqualified, screened_date; unique on symbol+date)
- `MarketDataService::atr()` — ATR14 calculation from OHLCV bars
- `ScreenerService::run()` — scores all active watchlist symbols nightly; 3-factor scoring: momentum (SMA5 vs SMA20, 0–30 pts), volatility (ATR% sweet spot 2–4%, 0–40 pts), trend (up-days last 5 bars, 0–30 pts); disqualifies on price < min, ATR% out of range, earnings blackout, or insufficient data
- `screener:run` Artisan command with formatted output (qualified vs disqualified table)
- Scheduler: `screener:run` nightly at 8 PM ET weekdays
- Config keys: `ALPACA_SCREENER_MIN_PRICE`, `ALPACA_SCREENER_MIN_ATR_PCT`, `ALPACA_SCREENER_MAX_ATR_PCT`, `ALPACA_SCREENER_TOP_N`

### New Supporting Models
- `EarningsEvent` + migration, `MarketCondition` + migration, `NewsArticle` + migration + factory
- `SyncEarningsCalendarJob`, `SyncNewsSentimentJob`, `SyncMarketConditionJob` + scheduler entries

### Tests (47 passing)
- `EarningsEventTest` — 8 tests (blackout window, next-date logic, fixed CarbonImmutable bug)
- `MarketConditionTest` — 5 tests (bearish/bullish/stale/no-data)
- `SignalServiceTest` — 9 tests (crossover buy/sell/hold, insufficient data, cooldown, sentiment filter)
- `TradingServiceTest` — 15 tests (trading disabled, PDT, earnings, macro filter, position sizing, stop-loss)
- `ScreenerServiceTest` — 10 tests (scoring, disqualifiers, API failure resilience, idempotency)

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
