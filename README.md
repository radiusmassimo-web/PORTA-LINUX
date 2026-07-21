# PORTA-LINUX

**PORTA-LINUX: Portable Linux Operating System on External SSD**

*By RadiusMassimo*

## Overview

PORTA-LINUX is a complete, portable Linux operating system installed on an external SSD connected via a SATA-to-USB adapter. The system is designed for **portability**, **privacy**, **compatibility**, and **hardware independence**, while providing advanced features such as dual browsers, AppImage support, VPN integration, and torrent management.

### Key Features

- 🖥️ **Portable**: Boot from any compatible machine (UEFI or BIOS)
- 🔒 **Privacy-Focused**: Dual browser setup with built-in VPN options
- 📦 **AppImage Support**: Automated AppImage management
- 🌐 **Torrent Client**: Built-in torrent management
- 🔌 **Hardware Independent**: Works on any compatible PC without modifying the host system

---

## Hardware Architecture

### Components Required

- **External SSD**: Connected via SATA→USB 3.0 adapter (with UASP support recommended)
- **Internal SSD/HDD** (Optional): Formatted in exFAT for AppImage and torrent files
- **Internet Connection**: Ethernet cable recommended for maximum stability and speed
- **Compatible PC**: UEFI or BIOS bootable system

## Software Architecture

The system uses a standard Linux distribution with manual GRUB bootloader configuration to ensure independence from the host PC's internal disk.

### Core Components

#### Web Browsers
- **Firefox**: Primary browser for everyday use and standard web services
- **LibreWolf**: Secondary browser with built-in VPN for anonymous browsing and accessing geo-restricted content

#### Torrent Management
- **qBittorrent** or **Transmission**: Full-featured torrent client with magnet link support

#### Application Management
- **AppImageLauncher**: Automatic discovery, installation, and management of AppImage applicatio
- 
#### VPN & Network
- **WireGuard**: Lightweight VPN protocol
- **ProtonVPN**: Optional system-wide VPN integration

---

## Installation & Setup

### Prerequisites

Before starting, ensure you have:
- An external SSD (minimum 60GB recommended)
- SATA-to-USB 3.0 adapter with UASP support
- A Linux installation USB (Ubuntu, Fedora, or similar)
- Access to a working computer with internet connection

### Step 1: Prepare the External SSD

1. Connect the external SSD via USB adapter
2. Boot from a Linux live USB on the target machine

### Step 2: Install Linux Operating System

1. During Linux installation, select the external SSD as the installation target
2. Choose the EFI partition for /boot/efi
3. Choose the Root partition for /
4. Configure GRUB bootloader to install on the external SSD's EFI partition
5. Complete the installation

### Step 3: Configure GRUB Bootloader

After installation, ensure GRUB boots from the external SSD by modifying the boot order in your BIOS/UEFI settings.

### Booting PORTA-LINUX

1. Connect the external SSD to your PC via USB adapter
2. Power on and enter BIOS/UEFI boot menu (usually F2, F10, or DEL during startup)
3. Select the external SSD as the primary boot device
4. Boot into PORTA-LINUX

### Daily Operations

- **Web Browsing**: Use Firefox for standard browsing; LiberWolf for privacy-critical activities
- **Torrent Downloads**: Use qBittorrent (GUI) or Transmission (lightweight alternative)
- **AppImages**: Place AppImage files in the designated AppImage folder; AppImageLauncher will handle integration
- **VPN Connection**: Enable WireGuard or ProtonVPN for encrypted network traffic

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


## System Requirements

| Requirement | Minimum | Recommended |
|------------|---------|-------------|
| External SSD Capacity | 60GB | 128GB+ |
| RAM | 4GB | 8GB+ |
| Processor | Intel i5 / AMD Ryzen 5 | i7 / Ryzen 7 |
| USB Adapter | USB 2.0 | USB 3.0 with UASP |
| Internet Speed | 1Mbps | 10Mbps+ |

---


## Contributing

Contributions are welcome! Please feel free to:

- Report bugs and issues
- Suggest improvements and features
- Submit pull requests with enhancements
- Improve documentation

### Version 1.0 (Initial Release - 2026-07-21)
- ✅ Complete documentation
- ✅ Installation guide
- ✅ Hardware specifications
- ✅ Software configuration instructions

---

## Roadmap

- [ ] Automated installation script
- [ ] Docker container support
- [ ] Enhanced security hardening guide
- [ ] Community package repository
- [ ] GUI configuration tool

---

**Created by**: RadiusMassimo  
**Last Updated**: 2026-07-21  
**Repository**: https://github.com/radiusmassimo-web/PORTA-LINUX

---

*PORTA-LINUX: Your portable, private, and independent Linux system.*
