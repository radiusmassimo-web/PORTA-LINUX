# PORTA-LINUX
PORTA-LINUX: Sistema Operativo Linux Portatile su SSD Esterno
PORTA-LINUX: Sistema Operativo Linux Portatile
su SSD Esterno
Questo documento descrive il progetto PORTA-LINUX, un sistema operativo Linux completo e
portatile installato su un SSD esterno collegato tramite adattatore SATA–USB. Il sistema è
concepito per garantire portabilità, privacy, compatibilità e indipendenza hardware, con l’aggiunta di
funzionalità avanzate come doppio browser, supporto AppImage, integrazione VPN e gestione
torrent



and
By RadiusMassimo 02/11/2025
PORTA-LINUX: Portable Linux Operating System on
External SSD
This document describes the projectPORTA-LINUX, a full-featured, portable Linux operating
system installed on an external SSD connected via a SATA-to-USB adapter. The system is
designed for portability, privacy, compatibility, and hardware independence, while adding
advanced features such as dual browsers, AppImage support, VPN integration, and torrent
management.
Hardware architecture:
- External SSD connected via SATA→USB 3.0 adapter (with UASP support).
- Internal SSD formatted in exFAT, used for AppImage and torrent files.
- Internet connection via Ethernet cable for maximum stability and speed.
- Linux operating system installed and bootable from any compatible machine (UEFI or BIOS).
Software structure:
The system uses a Linux distribution installed on an external SSD, with manual configuration of
the GRUB bootloader to ensure independence from the host PC's internal disk.
The main partitions include:
- EFI (FAT32) for boot.
- Root (EXT4) for the operating system.
- exFAT (internal SSD) for AppImage and shared data.
Main software components:
- Firefox: main browser for everyday use, access to standard sites and services.
- FreeWolf: Secondary browser with built-in VPN for anonymous browsing or accessing
blocked sites.
- qBittorrent / Transmission : torrent client with magnet-link support.
- AppImageLauncher : Automatic management of AppImage applications.
- UFW / Firejail: firewall and sandbox for security.
- WireGuard / ProtonVPN : Optional system VPN connection
-
- xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
- 
