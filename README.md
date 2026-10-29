# Cero OS

**A lightweight, self-hosted appliance operating system designed for modern home labs, edge servers, and high-performance network-attached storage (NAS).**

Website: [ceroos.cerosphere.my.id](https://ceroos.cerosphere.my.id/) · Releases: [GitHub Releases](https://github.com/cerosphere/CeroOS/releases)

---

## Overview

Cero OS transforms commodity x86-64 hardware into a reliable, enterprise-grade storage appliance. Built around atomic immutable updates and an ultra-clean web interface, Cero OS delivers raw storage performance without bloat or telemetry tracking.

- **Dual-Slot A/B OTA Updates:** Atomic system upgrades via Squashfs images (`filesystem.squashfs`). If an update fails, the bootloader automatically rolls back to the previous known-good partition slot.
- **Native ZFS Engine:** Enterprise data integrity, pooling, dataset compression (ZSTD/LZ4), automated background scrubs, and instant snapshots.
- **Container Runtime:** Integrated container management for running microservices and media servers alongside your storage pools.
- **Zero AI-Slop Web Console:** Fast, keyboard-accessible web UI built with Swiss design principles, real-time telemetry streaming, and instant disk health inspection.
- **Hardware Agnostic (BYOH):** Tested on Intel N100, AMD Embedded, Mini PCs, legacy towers, and custom multi-bay server chassis.

---

## System Requirements

| Specification | Minimum | Recommended |
|---|---|---|
| **Architecture** | 64-bit x86 (x86_64) | 64-bit x86 (x86_64, AVX support) |
| **CPU** | 2 cores (e.g., Intel Celeron J4125) | 4+ cores (e.g., Intel N100, Core i3/i5, AMD Ryzen) |
| **RAM** | 4 GB DDR4 | 8 GB+ DDR4/DDR5 (with ECC if supported) |
| **Boot Drive** | 16 GB SSD/NVMe (Dual A/B slot) | 32 GB+ NVMe SSD |
| **Storage Pool** | 1+ SATA/NVMe/SAS HDD or SSD | 2+ drives for ZFS Mirror, RAIDZ1, or RAIDZ2 |
| **Network** | 1 GbE Ethernet | 2.5 GbE or 10 GbE Ethernet |

---

## Downloads & Releases

Pre-built installer ISOs and OTA system update packages are distributed exclusively through the **[GitHub Releases](https://github.com/cerosphere/CeroOS/releases)** section of this repository.

### Release Package Contents
- `cero-installer-v*.iso`: Bootable bare-metal installation media for USB flash drives.
- `filesystem-v*.squashfs`: Compressed system image for dual-slot A/B partition OTA upgrades.
- `sha256sums.txt`: Cryptographic checksums to verify package integrity before flashing.

---

## Documentation & Support

- Official Portal: [https://ceroos.cerosphere.my.id/](https://ceroos.cerosphere.my.id/)
- Bug Reports & Feature Requests: Please use the [Issues](https://github.com/cerosphere/CeroOS/issues) tab.

---

## License

Copyright (c) 2026 Cerosphere. All Rights Reserved.

Cero OS binary releases are provided free of charge for personal and organizational deployment on your own hardware. The underlying source code is proprietary. See the [LICENSE](LICENSE) file for complete terms and warranty disclaimers.
