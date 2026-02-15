# Fork Overview (Quark1980)

## Origin

This repository is derived from:

- https://github.com/meshcore-dev/MeshCore

The upstream MeshCore project is authored and maintained by the MeshCore team and contributors.

## Why This Fork Exists

This fork was created to test a repeater-side status push feature for solar repeater monitoring, without requiring a separate monitoring app.

Goal:

- Send repeater health/performance data as plain text mesh messages that companion radios can receive and log.

## Intended Use

- Testing and experimentation
- Validation of status push behavior, message format, and practical monitoring workflow

This fork is not positioned as a long-term production branch.

## Upstream Strategy

If this approach proves useful, the preferred path is:

1. Keep changes minimal and clearly documented.
2. Converge back toward upstream MeshCore.
3. Upstream relevant parts where appropriate.

## What Was Changed

Main feature area:

- Repeater `statbroadcast` capability

Key additions:

- Periodic status messages
- Manual send trigger
- Configurable interval
- Configurable hashtag channel with proper hashtag-derived channel key
- Documentation and dated build artifacts

See details here:

- `docs/statbroadcast_changelog.md`
- `docs/statbroadcast_quickstart.md`
- `docs/cli_commands.md`
