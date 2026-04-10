# nobullies.club — Tech Stack

## Backend

| Layer | Technology |
|---|---|
| Language | PHP 8.x |
| Framework | Laravel |
| CMS | Statamic |

## Frontend

| Layer | Technology |
|---|---|
| JS Framework | Alpine.js (assumed — consistent with other projects) |
| CSS | Tailwind CSS (assumed) |
| Bundler | Vite |

## Notes

- Stack is confirmed as Laravel + Statamic. Specific versions and additional packages TBD when the repo is pulled down.
- Anonymous story submissions: likely handled via a Laravel-backed form endpoint or Statamic Forms, storing submissions for moderation before display.
- Pledge counter: simple Laravel endpoint to record and display a running count of supporters. No account required.
- May need content moderation tooling for anonymous story submissions.
