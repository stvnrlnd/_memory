# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workspace Overview

This is a personal workspace repository containing three categories of work:

- **`_sites/`** — Laravel + Statamic web projects (each has its own `CLAUDE.md`)
- **`_vaults/`** — Obsidian knowledge vaults, organized by family/company group
- **`okonomi/`** — Personal Omarchy Linux desktop configuration

The root directory itself is also an Obsidian vault (see `.obsidian/`).

## Sites (`_sites/`)

Each site is a standalone Laravel 12 + Statamic 6 application. When working inside a site, consult that site's own `CLAUDE.md` — it contains the full Laravel Boost guidelines, package versions, testing conventions, and coding standards specific to that project.

Current sites:
- `homestead_plus/` → homestead.plus
- `sendfeed_to/` → sendfeed.to
- `stevenroland_com/` → stevenroland.com

### Common site commands (run from the site directory)

```bash
composer install && npm install   # Install dependencies
composer run dev                  # Start dev server (Vite + PHP)
php artisan test --compact        # Run all tests
php artisan test --compact tests/Feature/SomeTest.php  # Run one file
php artisan test --compact --filter=testName            # Run one test
vendor/bin/pint --dirty --format agent   # Fix PHP code style after changes
php artisan route:list --except-vendor  # Inspect routes
php artisan tinker --execute 'Your::code();'  # Run PHP in app context
php please                        # Statamic CLI (list available commands)
```

## Vaults (`_vaults/`)

Obsidian markdown vaults grouped by family/entity:
- `allgood_roland/` — allgood-roland.org, openfaith.world, stevenroland.com, theirvoice.blog, theoandchar.com
- `big_city_software/` — Big City Software client sites
- `kelley_roland/` — Kelley Roland family
- `segment_holdings/` — homestead.plus, sendfeed.to, segment.holdings

## Okonomi (`okonomi/`)

Personal preferences and configuration for [Omarchy](https://omarchy.org), an Arch Linux + Hyprland setup. Use the `omarchy` skill when editing files here.

## Environment

- `.mise.toml` adds `bin/` to PATH (for any local scripts)
- Sites use SQLite by default in development
- Docker Compose (`compose.yaml`) is available in each site for containerized development
