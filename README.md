# conductr-dashboard-android

Android tablet app (Expo / React Native) that consumes the [`conductr`](https://github.com/Luan-vP/conductr) daemon over the network and renders a read-only dashboard for projects, PRs, cadence schedules, and idle findings.

This is one of two outlets (the other is [`conductr-dashboard-vscode`](https://github.com/Luan-vP/conductr-dashboard-vscode)). Both consume the same data model + command surface, defined in [`docs/dashboard-api.md`](https://github.com/Luan-vP/conductr/blob/develop/docs/dashboard-api.md) of the main `conductr` repo.

## Status

Scaffolding pending — see issue [Luan-vP/conductr#151](https://github.com/Luan-vP/conductr/issues/151) for the v1 implementation plan.

## Architecture

- Connects to the conductr daemon over TLS + bearer token (Tailscale or static-IP reachable).
- Subscribes to the daemon's SSE channel for push updates (`react-native-sse` polyfill).
- Imports `@conductr/dashboard-core` for shared types and assembly logic.
- v1 is read-only and single-host. Multi-host federation lands with [Luan-vP/conductr#152](https://github.com/Luan-vP/conductr/issues/152).
- Designed for 10–13" Android tablets in landscape. Phone form factor is not a v1 target.

## v1 screens

1. **Home** — what's playing right now, live cadence staff, per-project status cards.
2. **Projects** — list of active projects from `~/.conductr`.
3. **Project detail** — open PRs, idle findings, recent cycles, build status.
4. **Findings** — global inbox across all projects.
5. **Pod** — tmux session health.
6. **Settings** — drone host config (URL + bearer token, persisted in SecureStore).

## Cross-links

- API contract: [Luan-vP/conductr#146](https://github.com/Luan-vP/conductr/issues/146)
- Daemon v1: [Luan-vP/conductr#147](https://github.com/Luan-vP/conductr/issues/147)
- Dashboard core crate: [Luan-vP/conductr#149](https://github.com/Luan-vP/conductr/issues/149)
- Multi-host federation (v2): [Luan-vP/conductr#152](https://github.com/Luan-vP/conductr/issues/152)
- Sister outlet (VSCode): [conductr-dashboard-vscode](https://github.com/Luan-vP/conductr-dashboard-vscode)
