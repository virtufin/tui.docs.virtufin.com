# virtufin-tui

Terminal UI: operator dashboard for the Virtufin platform.

A Textual-based Python TUI that connects to a `virtufin-api` endpoint and exposes the
full Virtufin control plane — workers, WebSocket connections, state store, and the
live CloudEvent stream — in a single keyboard-driven screen. Reuses the existing
`virtufin.api` Python client; no service-side changes.

See the normative contract in
[`virtufin-openspec/openspec/changes/virtufin-tui/specs/terminal-ui/spec.md`](https://gitea.haenerconsulting.com/virtufin/virtufin-openspec/src/branch/master/openspec/changes/virtufin-tui/specs/terminal-ui/spec.md).

## Quick start

`virtufin-tui` is published to a private index, not public PyPI --
authenticate first (a Gitea personal access token with `read:packages`
scope works as the password):

```bash
export VIRTUFIN_PACKAGES_USER=<your-gitea-username>
export VIRTUFIN_PACKAGES_TOKEN=<your-gitea-token>
INDEX="https://${VIRTUFIN_PACKAGES_USER}:${VIRTUFIN_PACKAGES_TOKEN}@pypi.haenerconsulting.com/api/packages/virtufin/pypi/simple/"

# Run without installation
uvx --index "$INDEX" --from virtufin-tui virtufin-tui

# Or install and run
pip install virtufin-tui --index-url "$INDEX" --extra-index-url https://pypi.org/simple
virtufin-tui
```

See [Installation](docs/v1/getting-started.md#install) for the persistent
(non-inline-credential) setup.

First run with no config: the TUI prints an error and exits -- create
`~/.config/virtufin/api/contexts.toml` by hand (see
[`contexts.toml.example`](contexts.toml.example) for the file format, and
[Contexts](docs/v1/contexts.md) for the full schema).

## Features

- **Configurable multi-tab dashboard** — `Home` / `Trading` / `Infra` by
  default, workers / connections / scripts / triggers / live CloudEvent
  stream / config; the tab and pane layout is user-editable from the TUI
  itself, and you can add your own tabs and panes without touching the
  source tree
- **Multi-context** — switch between dev / staging / prod `virtufin-api`
  endpoints without restart
- **Hot-reload** — load new worker code, set env-vars, set tags — all from a single keypress
- **State + service browser** — invoke any gRPC method via the API gateway's
  `Gateway.Invoke` with auto-built form
- **Live pubsub streaming** — `Pubsub.Subscribe` server-streaming consumer feeding
  an interactive log

## Documentation

- [Getting started](docs/v1/getting-started.md)
- [Keybindings](docs/v1/keybindings.md)
- [Contexts](docs/v1/contexts.md)
- [Custom tabs & panes](docs/v1/custom-panes.md)
- [Architecture](docs/v1/architecture.md)

## License

MIT
