# Changelog

## [v1.0.3] - 2026-11-01

### Added
- **Realtime LXC Resource Telemetry**: Real-time background polling (2.5s interval) for container CPU, RAM, and Disk metrics with smooth CSS bar gliding and Proxmox-style color-coded thresholds (accent for normal, amber $\ge 75\text{--}80\%$, red $\ge 90\%$).
- **LXC Physical Disk Isolation**: Enforced loop virtual disk device backingstore (`rootdev`) with strict hardware quota limits, replacing directory-based storage to prevent host disk overconsumption.
- **LXC Lifecycle Activity Logging**: Integrated event logging in the container resource panel displaying timestamps, action badges, and status messages for container lifecycle events.
- **Dashboard Telemetry & Multi-Volume Aggregation**:
  - **DATA Widget**: Aggregated capacity and usage across all active data pools with explicit free space readouts (`X GB Free`).
  - **MEMORY Widget**: Added real-time available memory telemetry in widget header.
  - **CPU & Power**: Added live CPU power draw (W) and CPU package temperature streaming via SSE; prioritized `coretemp` / `k10temp` sensors over motherboard chipset sensors.
  - **Storage Sidebar**: Real-time telemetry status, capacity bars, and health indicators for sidebar volume mounts.
- **Linear-Style Floating Sidebar Toggle**: Redesigned sidebar collapse button into a floating border tab mathematically centered on the border crosshair (`translate(50%, 50%)`), unified across expanded and collapsed states.

### Fixed
- **Virtualization Navigation & Sidebar Isolation**: Fixed Files sidebar DOM elements and storage volume timers leaking into Virtualization view by scoping selectors to `#files_side`, adding route guards (`dataset.app === 'files'`), and clearing teardown timers.
- **SSE Feedback Loop & Screen Flickering**: Excluded sub-command `stats` from backend SSE container event broadcasts in `app.py` and converted container detail updates to in-place DOM manipulation in `chunk-lxc.js`, eliminating 2–3x screen flashing on container selection.
- **LXC Memory Calculation Accuracy**: Excluded `inactive_file` reclaimable page cache from cgroup memory statistics to reflect actual resident application usage rather than total cached memory.
- **LXC Console Modal & Fullscreen**: Expanded terminal modal dimensions, resolved text clipping via `ResizeObserver`, enabled true 100vw/100vh fullscreen mode with proper terminal dimension resize, and removed redundant modal footers.
- **Compact Viewport Layout**: Prevented container detail card squashing on compact/low-resolution screens (`flex: none`), enabled wrapping for long paths and IP addresses (`overflow-wrap: anywhere; word-break: break-word`), and added responsive toolbar button wrapping.
- **vCPU Label Grammar**: Corrected static pluralization to dynamically display `1 Core` vs `>1 Cores`.
- **Power Actions Authentication**: Added `credentials: "same-origin"` to shutdown and reboot API fetch calls to prevent HTTP 401 Unauthorized errors.
- **Branding & Visual Consistency**: Aligned CLI banner and system accent colors to high-contrast indigo (`#6366F1`) matching the web dashboard theme.
  
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
