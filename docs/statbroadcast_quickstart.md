# StatBroadcast Quickstart

## What It Does

`statbroadcast` makes a repeater send plain text status messages over mesh so companion radios can receive them like regular group chat traffic.

## Current Status Format

`<repeater_name>: batt=<mV> battp=<percent>% nf=<dBm> snr=<dB> rssi=<dBm> neigh=<count> sent=<count> total=<count> uptime=<DD:HH:MM:SS>`

## CLI Commands

- `statbroadcast`
  - Show current status (on/off, interval, channel)
- `statbroadcast now`
  - Send one immediate status message
- `get statbroadcast.interval`
  - Read interval in minutes
- `set statbroadcast.interval <minutes>`
  - Set interval (`0-1440`, `0` disables periodic sends)
- `get statbroadcast.channel`
  - Read current hashtag channel
- `set statbroadcast.channel <hashtag_name>`
  - Set channel (`#` optional, example: `rptstats` or `#rptstats`)

## Default Settings

- Interval: `60` minutes
- Channel: `#rptstats`

## Message Routing

- Messages use standard plain group text packet type.
- Messages follow the normal flood forwarding path.
- No special forwarding path is introduced for this feature.

## Notes

- Channel key is derived from the hashtag name.
- Hashtag name must follow MeshCore naming rules.
- This fork is for testing/experimentation.
