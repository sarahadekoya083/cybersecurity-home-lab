Phase 1 Screenshots
## Phase 1 — Lab Environment Setup

Building out the VirtualBox inventory: attacker, victims, and infrastructure VMs, each on their own virtual disk and network adapter.

| Screenshot | Description |
|---|---|
| `01-virtualbox-manager-overview.png` | VirtualBox Manager showing the full VM inventory (Kali, WinServer2019, Windows 10, Metasploitable, pfSense, CyberOps Security Onion) with the Hard Disk Selector open, confirming all virtual disks are correctly attached. |
| `02-metasploitable2-extracted-files.png` | Extracted Metasploitable2 archive (`.vmdk`, `.vmx`, `.nvram`) ready to be imported as a VM. |
| `03-new-vm-wizard-windows10.png` | Creating the Windows 10 victim VM — naming it and selecting the OS type/version in the New Virtual Machine wizard. |
| `04-pfsense-nat-adapter-settings.png` | pfSense VM network Adapter 1 set to **NAT**, so the firewall itself can reach the internet (for updates) via its WAN interface. |
| `05-winserver2019-bridged-adapter-settings.png` | Windows Server 2019 VM Adapter 1 set to **Bridged Adapter**, used during initial Domain Controller setup before final network placement. |

> Each VM was deliberately isolated using VirtualBox internal/host-only networking, with pfSense acting as the router/firewall between segments.
