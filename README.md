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
- 🛡️ **Security**: Firewall and sandbox capabilities
- 🔌 **Hardware Independent**: Works on any compatible PC without modifying the host system

---

## Hardware Architecture

### Components Required

- **External SSD**: Connected via SATA→USB 3.0 adapter (with UASP support recommended)
- **Internal SSD/HDD** (Optional): Formatted in exFAT for AppImage and torrent files
- **Internet Connection**: Ethernet cable recommended for maximum stability and speed
- **Compatible PC**: UEFI or BIOS bootable system

### Partition Layout

| Partition | Format | Size | Purpose |
|-----------|--------|------|---------|
| EFI       | FAT32  | 512MB | Boot partition |
| Root      | EXT4   | Main | Linux operating system |
| Data      | exFAT  | Variable | AppImages, torrent files, shared data |

---

## Software Architecture

The system uses a standard Linux distribution with manual GRUB bootloader configuration to ensure independence from the host PC's internal disk.

### Core Components

#### Web Browsers
- **Firefox**: Primary browser for everyday use and standard web services
- **FreeWolf**: Secondary browser with built-in VPN for anonymous browsing and accessing geo-restricted content

#### Torrent Management
- **qBittorrent** or **Transmission**: Full-featured torrent client with magnet link support

#### Application Management
- **AppImageLauncher**: Automatic discovery, installation, and management of AppImage applications

#### Security & Firewall
- **UFW (Uncomplicated Firewall)**: Simple firewall management
- **Firejail**: Application sandboxing for enhanced security

#### VPN & Network
- **WireGuard**: Lightweight VPN protocol
- **ProtonVPN**: Optional system-wide VPN integration

---

## Installation & Setup

### Prerequisites

Before starting, ensure you have:
- An external SSD (minimum 64GB recommended)
- SATA-to-USB 3.0 adapter with UASP support
- A Linux installation USB (Ubuntu, Fedora, or similar)
- Access to a working computer with internet connection

### Step 1: Prepare the External SSD

1. Connect the external SSD via USB adapter
2. Boot from a Linux live USB on the target machine
3. Open a terminal and identify your external drive:
   ```bash
   lsblk
   ```
4. Use a partition tool (GParted) to create the following partitions:
   - **512MB EFI partition** (FAT32) - bootable flag
   - **Remaining space Root partition** (EXT4)

### Step 2: Install Linux Operating System

1. During Linux installation, select the external SSD as the installation target
2. Choose the EFI partition for /boot/efi
3. Choose the Root partition for /
4. Configure GRUB bootloader to install on the external SSD's EFI partition
5. Complete the installation

### Step 3: Configure GRUB Bootloader

After installation, ensure GRUB boots from the external SSD by modifying the boot order in your BIOS/UEFI settings, or by running:

```bash
sudo update-grub
sudo grub-install /dev/sdX1  # Replace sdX with your external drive identifier
```

### Step 4: Initial System Configuration

Once booted into PORTA-LINUX:

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install base dependencies
sudo apt install -y curl wget git build-essential

# Set up UFW firewall
sudo apt install -y ufw
sudo ufw enable
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

### Step 5: Install Core Applications

```bash
# Install Firefox
sudo apt install -y firefox

# Install FreeWolf (privacy-focused Firefox)
sudo apt install -y freewolf

# Install torrent clients
sudo apt install -y qbittorrent transmission

# Install AppImageLauncher
sudo apt install -y appimagelauncher

# Install security tools
sudo apt install -y firejail wireguard

# Install optional VPN
# ProtonVPN: Visit https://protonvpn.com/download/linux
```

### Step 6: Configure VPN (Optional)

For WireGuard:
```bash
# Generate WireGuard keys
wg genkey | tee privatekey | wg pubkey > publickey

# Create VPN configuration
sudo nano /etc/wireguard/wg0.conf
```

For ProtonVPN, follow their official installation guide.

---

## Usage

### Booting PORTA-LINUX

1. Connect the external SSD to your PC via USB adapter
2. Power on and enter BIOS/UEFI boot menu (usually F2, F10, or DEL during startup)
3. Select the external SSD as the primary boot device
4. Boot into PORTA-LINUX

### Daily Operations

- **Web Browsing**: Use Firefox for standard browsing; FreeWolf for privacy-critical activities
- **Torrent Downloads**: Use qBittorrent (GUI) or Transmission (lightweight alternative)
- **AppImages**: Place AppImage files in the designated AppImage folder; AppImageLauncher will handle integration
- **VPN Connection**: Enable WireGuard or ProtonVPN for encrypted network traffic

### Security Best Practices

```bash
# Enable firewall rules
sudo ufw allow 22/tcp    # SSH (if enabled)
sudo ufw allow 53        # DNS
sudo ufw allow 80        # HTTP
sudo ufw allow 443       # HTTPS

# Use Firejail to sandbox applications
firejail firefox
firejail qbittorrent

# Check system security
sudo ufw status
```

---

## Troubleshooting

### System Won't Boot from External SSD

- Verify BIOS/UEFI boot order includes the external SSD
- Check USB adapter compatibility (UASP support recommended)
- Try a different USB port on your PC
- Ensure EFI partition is marked bootable

### Slow Performance

- Use a USB 3.0 adapter and port (not 2.0)
- Enable UASP support in BIOS/UEFI if available
- Check for background processes: `top` or `htop`
- Consider upgrading to a faster SSD

### VPN Connection Issues

- Verify WireGuard/ProtonVPN installation: `wg show` or `protonvpn status`
- Check DNS resolution: `nslookup google.com`
- Review logs: `sudo journalctl -xe`

### AppImage Not Running

- Ensure AppImageLauncher is installed
- Make executable: `chmod +x application.AppImage`
- Check dependencies: `ldd application.AppImage`

---

## Project Structure

```
PORTA-LINUX/
├── README.md                 # This file
├── docs/
│   ├── INSTALLATION.md       # Detailed installation guide
│   ├── HARDWARE.md           # Hardware compatibility
│   ├── SECURITY.md           # Security hardening guide
│   ├── TROUBLESHOOTING.md    # Common issues & solutions
│   └── CONTRIBUTING.md       # Contribution guidelines
├── scripts/
│   ├── install-packages.sh   # Automated package installation
│   └── setup-vpn.sh          # VPN configuration script
└── configs/
    ├── wireguard/            # WireGuard configuration templates
    └── ufw/                  # UFW firewall rules
```

---

## System Requirements

| Requirement | Minimum | Recommended |
|------------|---------|-------------|
| External SSD Capacity | 64GB | 128GB+ |
| RAM | 4GB | 8GB+ |
| Processor | Intel i5 / AMD Ryzen 5 | i7 / Ryzen 7 |
| USB Adapter | USB 2.0 | USB 3.0 with UASP |
| Internet Speed | 1Mbps | 10Mbps+ |

---

## Security Considerations

⚠️ **Important**: While PORTA-LINUX is designed with privacy in mind, remember:

- VPN services are only as secure as the provider
- Firejail provides application-level sandboxing, not full system isolation
- Always keep your system updated with security patches
- Use strong passwords for system access
- Regularly backup important data
- Be cautious when downloading torrents from untrusted sources

---

## Contributing

Contributions are welcome! Please feel free to:

- Report bugs and issues
- Suggest improvements and features
- Submit pull requests with enhancements
- Improve documentation

See [CONTRIBUTING.md](docs/CONTRIBUTING.md) for detailed guidelines.

---

## License

This project is released under the [MIT License](LICENSE).

---

## Support & Community

- **Issues**: Report bugs and request features on [GitHub Issues](https://github.com/radiusmassimo-web/PORTA-LINUX/issues)
- **Discussions**: Join discussions on [GitHub Discussions](https://github.com/radiusmassimo-web/PORTA-LINUX/discussions)
- **Documentation**: Check the `/docs` folder for comprehensive guides

---

## Changelog

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
