# instant-status

Upptime-powered status page for [instanode.dev](https://instanode.dev).

- Live status page: https://status.instanode.dev
- Incidents auto-open as issues in this repository when a monitored endpoint fails; they close automatically once the endpoint recovers.
- Checks run every 5 minutes via GitHub Actions (see `.github/workflows/uptime.yml`).

## What is monitored

Configured in `.upptimerc.yml`:

- **API** - `https://api.instanode.dev/healthz`
- **Marketing site** - `https://instanode.dev/`
- **Customer Postgres** - TCP ping to `pg.instanode.dev:5432`

## Powered by

[Upptime](https://upptime.js.org/) - the open-source uptime monitor and status page powered entirely by GitHub Actions, Issues, and Pages. No servers, no dashboards, no cost.

## License

MIT
