Phase 4 screenshots
## Phase 4 — Network Connectivity Verification

Confirming full Layer 3 connectivity across the lab segment and performing initial reconnaissance with Nmap before any exploitation.

| Screenshot | Description |
|---|---|
| `01-initial-ping-50pct-loss.png` | Initial `ping 192.168.56.101` from Windows Server showing intermittent "Destination host unreachable" (50% packet loss) — an early routing/interface issue that had to be resolved. |
| `02-pfsense-interface-assignments.png` | pfSense Interface Assignments page: WAN (`em0`) and Kali/LAN (`em1`) mapped to their NICs, with a third port (`em2`) available/unused. |
| `03-kali-ip-a-output.png` | Kali `ip a` output confirming its address on the lab segment (`192.168.56.103/24`). |
| `04-metasploitable-ifconfig.png` | Metasploitable2 `ifconfig` output confirming its address (`192.168.56.102`). |
| `05-nmap-host-discovery-sweep.png` | `nmap -sn 192.168.56.0/24` host discovery sweep — 4 hosts found up (`.100`, `.101`, `.102`, `.103`). |
| `06-kali-ping-tests-all-hosts.png` | Kali successfully pinging pfSense (`.101`) and Metasploitable (`.102`), 0% packet loss. |
| `07-windows10-ping-tests-all-hosts.png` | Windows 10 `cmd` ping tests to `.102`, `.103`, and `.101` all succeeding — confirming full connectivity across the segment. |
| `08-nmap-detailed-scan-metasploitable.png` | `nmap -sV -A 192.168.56.102` — detailed scan revealing FTP (vsftpd 2.3.4), SSH, Telnet, and SMTP. This scan reveals the vulnerable FTP backdoor exploited in Phase 6. |
| `09-nmap-detailed-scan-windows10.png` | `nmap -sV -A 192.168.56.21` — scan showing SMB stack (135/139/445), NetBIOS name, and OS fingerprinted as Windows. |
| `10-nmap-scan-host-down-retry.png` | Nmap initially reporting the Windows 10 host as down (blocking ping probes) and retrying with `-Pn`. |
| `11-nmap-scan-attempts-log.png` | Terminal log of the sequence of scans run against `.100`–`.103` during the recon phase. |
| `12-nmap-scan-full-subnet.png` | `nmap -sV -Pn` sweep across the full `/24` subnet plus a targeted scan of the Windows 10 host. |
| `13-port-scan-ftp-open-verification.png` | Targeted `nmap -p21` and `nc -zv` checks confirming Metasploitable's FTP port is open before exploitation. |
