# Omarchy Super Monitor Settings


One Omarchy bar widget for tuning monitors, display layout, cursor/UI sizing, brightness, night light, and idle behavior without hand-editing Lua.

## What it combines

- `omarchy-display`: live display arrangement, resolution/refresh controls, brightness, and a night-light toggle.
- `Omarchy-Monitor-Settings-Extender`: friendly monitor names, mirror/extend, rotation, cursor size, text size, scale, and drag-and-drop layout.
- `omarchy-idle-settings`: saved screensaver and lock timeout controls.

## Persistence

Monitor actions are applied live, then captured into a marked block in `~/.config/hypr/monitors.lua`. The plugin creates a first-write backup at `~/.config/omarchy/monitors.lua.before-super-monitor-settings`.

Turn Off is temporary and does not remove the monitor from the saved layout. Turn On reloads that preserved layout so the monitor returns with its saved mode, position, scale, and rotation.

Before accepting a saved monitor layout, the helper reloads Hyprland and checks `hyprctl configerrors`. A rejected layout is rolled back automatically. Idle values are written atomically to `~/.config/omarchy/shell.json` while preserving the rest of the file; lock time is always kept at or after the screensaver time.

Other settings use their native Omarchy persistence paths: text size uses the Omarchy command, cursor size uses GNOME settings, and the Night Light button uses Omarchy's own toggle command.

## Install

Install directly from GitHub:

```sh
omarchy plugin add https://github.com/thetxeagle/omarchy-super-monitor-settings-plugin.git --enable
```

Open the monitor icon in the Omarchy bar. The plugin replaces the stock display widget in place. Move it with:

```sh
omarchy bar move io.github.thetxeagle.super-monitor-settings --section right
```

If an older install left both widgets on the bar, run this one-time migration:

```sh
omarchy plugin disable omarchy.monitor
omarchy plugin disable io.github.soulshocker.super-monitor-settings
omarchy plugin enable io.github.thetxeagle.super-monitor-settings --section right
omarchy restart shell
```

The `disable` line removes the previous Soulshocker-branded installation before enabling the renamed plugin.

Fresh installs use `omarchy.clonedFrom: omarchy.monitor` and replace the stock widget automatically.

## Requirements

Omarchy with Hyprland, `hyprctl`, `jq`, `gsettings`, and the standard Omarchy monitor helpers. No daemon or Lua customization is required.

## Validation

```sh
omarchy plugin validate .
shellcheck bin/omarchy-super-monitor-settings
```

MIT licensed.
