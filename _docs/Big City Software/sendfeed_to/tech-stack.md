# sendfeed.to — Tech Stack

## Backend

| Layer | Technology |
|---|---|
| Language | PHP 8.5 |
| Framework | Laravel 12 |
| CMS | Statamic v6 |
| Admin/App Panels | Filament v5 |
| Billing | Laravel Cashier v16 (Stripe) |
| Queues / Cache | Redis |
| Database | MySQL 8.4 |
| Search | Meilisearch |
| Media | Spatie Laravel Media Library |
| Image Processing | Spatie Image + Browsershot (Puppeteer) |

## Frontend

| Layer | Technology |
|---|---|
| JS Framework | Alpine.js v3 (+ Collapse, Focus, Morph, Persist plugins) |
| CSS | Tailwind CSS v4 |
| Bundler | Vite v7 |
| Form Validation | Laravel Precognition (Alpine integration) |
| Carousel | Embla Carousel |

## Development & Tooling

| Tool | Purpose |
|---|---|
| Laravel Sail | Docker-based local dev environment |
| Laravel Boost | MCP server for AI-assisted dev (Artisan, Tinker, DB inspection) |
| Laravel Pint | PHP code formatting |
| Laravel Pail | Real-time log streaming |
| PHPUnit v11 | Testing |
| Laravel Debugbar | Local debugging |

## Architecture Notes

- **Statamic** handles CMS content (flat-file by default). The app layer uses Laravel's Eloquent and MySQL for user accounts, projects, feeds, subscribers, and billing data.
- **Filament** provides the admin panel and user-facing app dashboards (separate panels).
- **Redis** backs both the queue driver and cache. Background jobs are central to the product — feed polling and digest email dispatch both run as queued jobs.
- **Inertia.js v2** is used for extending Statamic's Control Panel (Vue 3 under the hood in the CP).
- **Laravel Cashier** handles Stripe subscriptions and the per-1,000 subscriber add-on billing.
- **Browsershot / Puppeteer** is present for server-side rendering/image generation (likely for digest previews or OG images).
- Local dev runs via Laravel Sail (Docker). The dev command runs the app server, queue listener, log stream, and Vite concurrently.
