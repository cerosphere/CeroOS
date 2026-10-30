# Changelog

## [v1.0.2] - 2026-10-31

### Fixed
- **System & OTA Updates**: Prevent stale version shadowing after OTA upgrades. Backend (`app.py`), TUI console (`cero-console.sh`), and OTA helper now prioritize reading `build-info` directly from the active boot slot (`/boot/cero-{active}/build-info` or `/run/live/medium/cero-{active}/build-info`) and synchronize build metadata to the persistence overlay (`rw/etc/cero/build-info`), ensuring the displayed version updates reliably.
- **Persistent Cloud Mounts**: Transitioned transient `systemd-run` rclone instances to dedicated persistent systemd unit services (`/etc/systemd/system/rclone-{name}.service`) with `Type=notify`, `Restart=always`, and `RestartSec=10` to survive reboots and process exits.
- **Auto-Heal Cloud Storage**: Added self-healing recovery to the storage list endpoint to automatically detect and restart stale or unmounted rclone units on demand.
- **FUSE Permissions**: Enabled `user_allow_other` in `/etc/fuse.conf` across installation scripts and ISO builds, ensuring `/media/{name}` mounts are accessible to unprivileged services.
- **File Manager Resilience**: Added automatic directory retry handling and background storage status polling in the Web UI to prevent empty directory listings.

## [v1.0.1a] - 2026-10-30

### Fixed
- **OTA Update & Boot**: Bundle kernel (`vmlinuz`) and `initrd.img` into OTA packages and add automatic kernel replication to standby partition to fix `/cero-b/vmlinuz not found` boot error.
- **OTA Verification**: Require real package assets before triggering update availability and remove simulation mock payload.

## [v1.0.1] - 2026-10-30

### Fixed
- **Cloud Storage**: Include `rclone` and `fuse3` in base system and ISO installer image to fix Google Drive mount.
