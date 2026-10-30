# Changelog

All notable changes to Cero OS will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v1.0.1] - 2026-10-30

### Added
- **Cloud Storage Integration**:
  - Native Google Drive integration via OAuth flow (`cerosphere.my.id`).
  - Bundled `rclone` and `fuse3` packages directly in base ISO and Debian host installation.
  - Multi-account cloud drive support with dedicated systemd-run unit isolation.
- **Virtualization & Container Ecosystem**:
  - LXC system container manager with structured 4-step creation wizard.
  - Pre-bundled Ubuntu 24.04 LTS container template with Proxmox-grade live PTY web terminal console.
  - Dedicated hardware resource limits (CPU cores, RAM memory, and swap space).
  - Direct host LAN interface bridge selection.
  - KVM/QEMU Virtual Machines with interactive noVNC web console and ISO mounting/ejection controls.
  - Docker Compose YAML editor and CLI deployment wizard.
- **Dual-Slot A/B OTA Engine**:
  - Image-based dual-slot A/B system partition updates with GRUB watchdog fallback.
  - Background update checker on startup with status alert in Notification Center.
  - Strict version matching with "System Up to Date" status indicators.
- **File Explorer & Media Previews**:
  - In-browser file previews: Images, Video player modal, Audio playback, PDF documents, Markdown, CSV, and ZIP archive contents.
  - Drag-and-drop file upload with circular ring progress indicators.
  - ZimaOS-style shared folder management and friendly volume paths (`/cerodata`, `/<volume>`).
- **Web Terminal & Services Management**:
  - Standalone full-screen Web Terminal with persistent `/root` working directory and authentic ASCII banner.
  - System Services manager: Samba / SMB1 toggles, HTTPS toggle with automated TLS generation, SSH & Web Terminal dialogs, and Factory Reset.

### Changed
- Refactored Navigation: consolidated containers and VMs into **Virtualization**.
- Rebuilt Settings into a responsive two-pane layout with nested folder permission picker.
- Enabled Server-Sent Events (SSE) telemetry stream for real-time dashboard telemetry.
- Reduced privileged helper latency using persistent daemon `cero-helperd` and bytecode launcher.

### Fixed
- Fixed missing `rclone` and `fuse3` runtime binaries on bare-metal appliance installations.
- Fixed long filename overflow in file explorer grid tiles with middle-truncation.
- Fixed optimistic UI toggle flip on service failure.
- Fixed boot latency and eliminated black-screen transition on tty1 login hand-off.

---

## [v1.0.0] - 2026-10-01

### Added
- Official initial stable release of Cero OS.
- Dual-Slot A/B OTA Updates with squashfs payload format.
- ZFS 2.2 Storage Engine with native RAIDZ pools and scrub monitoring.
- Industrial Web Dashboard with dark mode and telemetry widgets.
- BYOH (Bring Your Own Hardware) architecture for Intel & AMD x86_64 systems.
