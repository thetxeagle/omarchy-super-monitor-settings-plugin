# Omarchy Super Monitor Settings

One Omarchy bar widget for tuning monitors, display layout, cursor/UI sizing, brightness, night light, and idle behavior without hand-editing Lua.

## What it combines

- `omarchy-display`: live display arrangement, resolution/refresh controls, brightness, and a night-light toggle.
- `Omarchy-Monitor-Settings-Extender`: friendly monitor names, mirror/extend, rotation, cursor size, text size, scale, and drag-and-drop layout.
- `omarchy-idle-settings`: saved screensaver and lock timeout controls.

## Persistence

Monitor actions are applied live, then captured into a marked block in `~/.config/hypr/monitors.lua`. The plugin creates a first-write backup at `~/.config/omarchy/monitors.lua.before-super-monitor-settings`.

Before accepting a saved monitor layout, the helper reloads Hyprland and checks `hyprctl configerrors`. A rejected layout is rolled back automatically. Idle values are written atomically to `~/.config/omarchy/shell.json` while preserving the rest of the file; lock time is always kept at or after the screensaver time.

Other settings use their native Omarchy persistence paths: text size uses the Omarchy command, cursor size uses GNOME settings, and night-light scheduling uses the user Hyprsunset configuration.

## Install

From the checked-out plugin directory:

```sh
omarchy plugin add /home/soulshocker/GitHub/omarchy-super-monitor-settings-plugin --enable
```

Open the monitor icon in the Omarchy bar. The plugin replaces the stock display widget in place. Move it with:

```sh
omarchy bar move io.github.soulshocker.super-monitor-settings --section right
```

## Requirements

Omarchy with Hyprland, `hyprctl`, `jq`, `gsettings`, and the standard Omarchy monitor helpers. No daemon or Lua customization is required.

## Validation

```sh
omarchy plugin validate .
shellcheck bin/omarchy-super-monitor-settings
```

MIT licensed.
