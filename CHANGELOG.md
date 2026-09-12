# Changelog

## Unreleased

### Added

- Combined Omarchy monitor controls for brightness, resolution, refresh rate, scale, rotation, mirror/extend, cursor size, text size, and arrangement.
- Persistent monitor configuration with backup and Hyprland validation/rollback.
- Atomic screensaver and lock timeout editing in `shell.json`.

### Fixed

- Show per-monitor controls when only one display is connected.
- Fall back to the richer Hyprland monitor query when the shared monitor-state helper returns no displays.
- Keep single-monitor display settings enabled when the Turn Off action is unavailable.
- Update idle controls immediately after saving so they do not display stale timeout values.
- Corrected the README install command to use the GitHub repository URL instead of a machine-specific home path.
- Renamed the published plugin identity from `io.github.soulshocker.super-monitor-settings` to `io.github.thetxeagle.super-monitor-settings`.
