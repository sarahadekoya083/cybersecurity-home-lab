Phase 5 Screenshots
## Phase 5 — Network Segmentation & Firewall Rule Testing

Proving that pfSense firewall rules actually enforce policy between segments — not just building the lab, but validating it.

| Screenshot | Description |
|---|---|
| `01-firewall-rules-block-kali-to-metasploitable.png` | pfSense firewall rule set on the KALI interface: anti-lockout rule, a rule **blocking Kali → Metasploitable FTP (`:21`)**, and default allow rules. |
| `02-firewall-rule-edit-detail.png` | Detail view of the block rule — Action: Block, Interface: KALI, Protocol: TCP, Source `192.168.56.103/32`, Destination `192.168.56.102/32`. |
| `03-firewall-logs-deny-hits-set1.png` | pfSense firewall logs showing repeated "Default deny rule IPv4" hits as Kali's traffic to port 80/21 gets blocked — proof the rule is active. |
| `04-firewall-logs-deny-hits-set2.png` | Additional log entries, including blocked UDP/DHCP broadcast traffic and further TCP attempts. |
| `05-firewall-logs-deny-hits-set3.png` | Further confirmation of blocked traffic across a longer time span. |
| `06-reset-firewall-state-table.png` | Diagnostics → Reset States page — clearing pfSense's firewall state table so new rule changes take effect immediately. |
| `07-kali-outbound-internet-blocked.png` | Kali unable to reach the internet (`ping: connect: Network is unreachable`, later 100% packet loss to `8.8.8.8`) — demonstrating an outbound-block rule keeping Kali contained to the isolated lab segment. |
| `08-kali-internet-unreachable-then-lan-ok.png` | Kali confirming internet access is blocked while LAN traffic to pfSense/Metasploitable still works normally. |
| `09-firewall-rule-disabled-internet-restored.png` | Disabling the outbound-block rule and confirming Kali regains internet/DHCP access — set up for the exploitation demo in Phase 6. |
| `10-firewall-log-outbound-block-confirmed.png` | pfSense syslog explicitly confirming the "Block KALI OUTBOUND TO INTERNET (DEMO)" rule firing repeatedly before it was disabled. |

> This phase demonstrates that network segmentation isn't just configured — it's *validated* with before/after firewall log evidence.
