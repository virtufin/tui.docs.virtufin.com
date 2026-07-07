# virtufin-tui

Terminal UI: operator dashboard for the Virtufin platform.

A Textual-based Python TUI that connects to a `virtufin-api` endpoint and exposes the
full Virtufin control plane — workers, WebSocket connections, state store, and the
live CloudEvent stream — in a single keyboard-driven screen. Reuses the existing
`virtufin.api` Python client; no service-side changes.

See the normative contract in
[`virtufin-openspec/openspec/changes/virtufin-tui/specs/terminal-ui/spec.md`](https://gitea.haenerconsulting.com/virtufin/virtufin-openspec/src/branch/master/openspec/changes/virtufin-tui/specs/terminal-ui/spec.md).

## Quick start

```bash
# Run without installation
uvx --from virtufin-tui virtufin-tui

# Or install and run
pip install virtufin-tui
virtufin-tui
```

First run with no config: the TUI opens the contexts picker and prompts you to add
a `virtufin-api` endpoint. Subsequent runs read `~/.config/virtufin-tui/contexts.toml`.

## Features

- **3-panel dashboard** — workers, WebSocket connections, and live CloudEvent stream
- **Multi-context** — switch between dev / staging / prod `virtufin-api` endpoints
  without restart
- **Hot-reload** — load new worker code, set env-vars, set tags — all from a single keypress
- **State + service browser** — invoke any gRPC method via the API gateway's
  `Gateway.Invoke` with auto-built form
- **Live pubsub streaming** — `Gateway.Subscribe` server-streaming consumer feeding
  an interactive log

## Documentation

- [Getting started](docs/v1/getting-started.md)
- [Keybindings](docs/v1/keybindings.md)
- [Contexts](docs/v1/contexts.md)
- [Architecture](docs/v1/architecture.md)

## License

MIT
