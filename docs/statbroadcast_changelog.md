# StatBroadcast Changelog (Test Fork)

This changelog tracks the repeater status broadcast feature added in this fork.
It starts from the first implementation and lists updates up to the latest revision.

## Iteration 1 - Initial StatBroadcast implementation

- Added periodic repeater status push as plain text group messages.
- Added CLI interval control:
  - `get statbroadcast.interval`
  - `set statbroadcast.interval <minutes>`
- Added manual debug trigger:
  - `statbroadcast now`
- Added quick status command:
  - `statbroadcast`
- Reused existing repeater stats collection path to avoid duplicate logic.
- Fixed channel for testing to hashtag channel `#rptstats` using derived channel key.

## Iteration 2 - Documentation updates

- Added `statbroadcast` command documentation to `docs/cli_commands.md`.
- Documented fixed hashtag channel usage for status broadcasts.

## Iteration 3 - Repository notice

- Added top-level fork notice in `README.md`:
  - Clarifies this fork is not the original MeshCore author.
  - Clarifies this fork is intended for stat push testing and experimentation.

## Iteration 4 - Uptime format refinement

- Changed `uptime` in stat messages from raw seconds to `DD:HH:MM:SS`.

## Iteration 5 - Battery percentage estimate

- Added `battp` (battery percentage) to status messages.
- `battp` is estimated for a single 18650 cell using linear mapping:
  - `3000 mV -> 0%`
  - `4200 mV -> 100%`
  - Clamped to `0..100`

## Iteration 6 - Noise floor added

- Added noise floor as `nf` in status messages.

## Iteration 7 - Upstream release sync (v1.13.0)

- Branch merged with upstream release tag `repeater-v1.13.0`.
- Statbroadcast functionality was retained after merge:
  - fixed hashtag channel `#rptstats`
  - interval CLI (`get/set statbroadcast.interval`)
  - manual trigger (`statbroadcast now`)
  - payload fields including `battp`, `nf`, `uptime`

## Iteration 8 - Dated build artifact folder

- Added dated firmware artifact folder for Heltec v4 repeater builds:
  - `bin/HeltecRPT-2026-02-15/`
- Included build files for later download/reuse:
  - `firmware.bin`
  - `bootloader.bin`
  - `partitions.bin`
  - `BUILD_INFO.txt`

## Iteration 9 - Main page changelog

- Added a "Latest Changelog" section to `README.md` so the current status is visible from the repository front page.

## Iteration 10 - Configurable hashtag channel via CLI

- Added repeater CLI support to view/change statbroadcast hashtag channel:
  - `get statbroadcast.channel`
  - `set statbroadcast.channel <hashtag_name>`
- Channel name now persists in node preferences.
- Input accepts hashtag with or without `#`; normalized to hashtag form internally.
- Channel key derivation continues to follow hashtag-based derivation from channel name.
- Default remains `#rptstats`.

## Current status message fields

- `batt` (battery millivolts)
- `battp` (estimated battery percentage)
- `nf` (noise floor)
- `snr` (last SNR)
- `rssi` (last RSSI)
- `neigh` (number of neighbors)
- `sent` (total sent packets)
- `total` (sent + received packets)
- `uptime` (`DD:HH:MM:SS`)
