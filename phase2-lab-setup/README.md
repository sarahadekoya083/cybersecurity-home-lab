Phase 2 screenshots
## Phase 2 — pfSense Firewall Deployment

Standing up pfSense as the gateway for the lab and troubleshooting the initial configuration.

| Screenshot | Description |
|---|---|
| `01-pfsense-console-boot-interface-assignment.png` | pfSense console after boot, showing interface assignment: `WAN (em0)` on NAT/DHCP, `KALI (em1 / LAN)` statically set to `192.168.56.101/24`. This is the core network map for the lab. |
| `02-pfsense-wan-lan-interfaces-detail.png` | Close-up of the WAN/LAN interface assignment output. |
| `03-ie-blocked-pfsense-gui.png` | Internet Explorer Enhanced Security Configuration blocking access to the pfSense web GUI (`192.168.56.101`) from the Windows Server VM — a config step I had to work around. |
| `04-pfsense-dhcp-no-static-ip-error.png` | pfSense DHCP Server page warning: *"This system has no interfaces configured with a static IPv4 address"* — documenting a step that had to be fixed before DHCP would serve clients. |
| `05-domain-join-tutorial-dns-config.png` | Tutorial reference (Cyberwox Academy guide) for pointing pfSense's DHCP DNS setting to the Domain Controller (`192.168.2.10`) and setting the domain name (`CYBERWOX.local`) so clients could resolve and join the domain. |
