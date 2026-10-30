# Changelog

## [v1.0.1a] - 2026-10-30

### Fixed
- **OTA Update & Boot**: Bundle kernel (`vmlinuz`) and `initrd.img` into OTA packages and add automatic kernel replication to standby partition to fix `/cero-b/vmlinuz not found` boot error.
- **OTA Verification**: Require real package assets before triggering update availability and remove simulation mock payload.

## [v1.0.1] - 2026-10-30

### Fixed
- **Cloud Storage**: Include `rclone` and `fuse3` in base system and ISO installer image to fix Google Drive mount.
