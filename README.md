# [📈 Live Status](https://status.instanode.dev): <!--live status--> **🟩 All systems operational**

<!--start: description-->
This repository contains the open-source uptime monitor and status page for [instanode.dev](https://instanode.dev), powered by [Upptime](https://github.com/upptime/upptime).

The 7-service agent bundle plus public web surfaces are probed every 5 minutes from GitHub Actions. Daily summaries, response-time graphs, and incident issues are auto-generated.
<!--end: description-->

[![Uptime CI](https://github.com/InstaNode-dev/instant-status/workflows/Uptime%20CI/badge.svg)](https://github.com/InstaNode-dev/instant-status/actions?query=workflow%3A%22Uptime+CI%22)
[![Response Time CI](https://github.com/InstaNode-dev/instant-status/workflows/Response%20Time%20CI/badge.svg)](https://github.com/InstaNode-dev/instant-status/actions?query=workflow%3A%22Response+Time+CI%22)
[![Graphs CI](https://github.com/InstaNode-dev/instant-status/workflows/Graphs%20CI/badge.svg)](https://github.com/InstaNode-dev/instant-status/actions?query=workflow%3A%22Graphs+CI%22)
[![Summary CI](https://github.com/InstaNode-dev/instant-status/workflows/Summary%20CI/badge.svg)](https://github.com/InstaNode-dev/instant-status/actions?query=workflow%3A%22Summary+CI%22)

With [Upptime](https://upptime.js.org), you get a free and open-source status page hosted on GitHub Pages. Probes run from GitHub-hosted runners; history is committed to `history/`; incidents are filed as Issues in this repo.

<!--start: status pages-->
<!--end: status pages-->

## [Status page](https://status.instanode.dev)

The live status page is at <https://status.instanode.dev>. Incidents that fire because an endpoint returns a non-success code automatically open as Issues here; they close when the endpoint recovers.

## What's monitored

Configured in [`.upptimerc.yml`](.upptimerc.yml):

**Public web** — marketing front door, agent API health, dashboard, OpenAPI spec.

**The 7-service agent bundle** — Postgres, Redis, MongoDB, NATS queue, MinIO storage, webhook receiver, and container deploy. POST-only routes are probed with GET and accept `405 Method Not Allowed` as the success signal (the route is registered).

## Setup notes

See [`SETUP.md`](SETUP.md) for the two human-ops steps required to enable auto-rewrite of this README (a `GH_PAT` secret + branch-protection allowance).

## License

- Code: [MIT](./LICENSE) © [InstaNode-dev](https://github.com/InstaNode-dev)
- Status website: [MIT](https://github.com/upptime/upptime.js.org/blob/master/LICENSE) © [Anand Chowdhary](https://anandchowdhary.com)
- Summary template, workflows, response-time, graphs: [MIT](https://github.com/upptime/upptime/blob/master/LICENSE) © [Anand Chowdhary](https://anandchowdhary.com)
