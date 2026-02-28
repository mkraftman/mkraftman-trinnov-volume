# Mkraftman Trinnov Volume

Custom Home Assistant Lovelace card for controlling Trinnov Altitude volume. Features a pill-shaped slider with mute toggle and volume +/- buttons.

## Features

- Pill-shaped slider matching mushroom card aesthetics
- Mute toggle button (via `remote.send_command` or `switch.toggle` fallback)
- Volume +/- buttons (0.5 dB steps)
- Optimistic UI updates — slider responds instantly during drag
- Throttled service calls (max 1 per 200ms) to avoid overloading HA
- Graceful handling of unavailable entities

## Installation

### HACS

1. Add this repository as a custom repository in HACS (category: Lovelace)
2. Install "Mkraftman Trinnov Volume"
3. Add the resource in your Lovelace configuration

### Manual

1. Copy `dist/mkraftman-trinnov-volume.js` to `www/community/mkraftman-trinnov-volume/`
2. Add the resource:
   ```yaml
   resources:
     - url: /hacsfiles/mkraftman-trinnov-volume/mkraftman-trinnov-volume.js
       type: module
   ```

## Configuration

```yaml
type: custom:mkraftman-trinnov-volume
entity: number.trinnov_altitude_14681209_volume
mute_entity: switch.trinnov_altitude_14681209_mute
remote_entity: remote.trinnov_altitude_14681209
```

| Option          | Required | Description                                          |
| --------------- | -------- | ---------------------------------------------------- |
| `entity`        | Yes      | Volume number entity                                 |
| `mute_entity`   | No       | Mute switch entity                                   |
| `remote_entity` | No       | Remote entity for `mute_toggle` command (preferred)  |

## Layout

```
[Mute Icon]  -30.0 dB            [Vol-] [Vol+]
[============= SLIDER (full width) =============]
```
