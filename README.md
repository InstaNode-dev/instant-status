# instant-status

Upptime-powered status page for [instanode.dev](https://instanode.dev).

- Live status page: <https://status.instanode.dev>
- Incidents auto-open as issues in this repo when a monitored endpoint fails; they close automatically when the endpoint recovers.
- Checks run every 5 minutes from GitHub Actions (`.github/workflows/uptime.yml`).
- Daily summary, response-time, and graph generation run at 00:00 UTC.

## What is monitored

Configured in `.upptimerc.yml` — the 7-service agent bundle plus public web surfaces:

**Public web**
- Marketing site (`instanode.dev/`)
- Agent API health (`api.instanode.dev/healthz`)
- Dashboard (`app.instanode.dev/`)
- OpenAPI spec (`api.instanode.dev/openapi.json`)

**Provisioning surfaces (7-service bundle)**
- Postgres — `POST /db/new`
- Redis — `POST /cache/new`
- MongoDB — `POST /nosql/new`
- Queue (NATS) — `POST /queue/new`
- Storage (MinIO) — `POST /storage/new`
- Webhook — `POST /webhook/new`
- Deploy — `POST /deploy/new`

POST-only routes are probed by GET; a `405 Method Not Allowed` response is the success signal (the handler is wired and the router is up). `/deploy/new` is auth-gated and returns `401` for unauthenticated probes — also treated as success.

**Customer TCP surface**
- Customer Postgres TLS handshake (`pg.instanode.dev:5432`)

## Setup (one-time human ops)

Before the status site renders correctly, an admin needs to do two things — see [`SETUP.md`](./SETUP.md).

1. Add a `GH_PAT` secret (personal access token with `repo` scope) so workflows can push the auto-generated badges, response-time data, and README updates past branch protection.
2. Either disable `enforce_admins` on the `master` branch protection rule, or grant the PAT owner admin bypass, so the daily Summary/Graphs/Response-Time workflows succeed.

Once both are in place, run `Setup CI` manually from the Actions tab to seed the badge directory; the rest is automatic.

## Powered by

[Upptime](https://upptime.js.org/) — open-source uptime monitor and status page powered by GitHub Actions, Issues, and Pages. No servers, no dashboards, no recurring cost.

## License

MIT
