Phase 6 Screenshots
## Phase 6 — Exploitation with Metasploit

Using the reconnaissance from Phase 4 to exploit the vulnerable targets, including one full compromise and two honestly-documented failed attempts.

| Screenshot | Description |
|---|---|
| `01-smb-enumeration-access-denied.png` | Initial `smbclient -L` against Windows 10 (`192.168.56.21`) failing with `NT_STATUS_ACCESS_DENIED` on anonymous session setup; `enum4linux -a` kicked off next. |
| `02-enum4linux-results.png` | `enum4linux -a` results — RID range, known usernames, and successful NetBIOS/workgroup enumeration (`WORKGROUP`, `CYBERSAM`). |
| `03-smbclient-nbtstat-verification.png` | `nbtstat` and further `smbclient` session attempts confirming host services but no valid anonymous SMB session. |
| `04-ms17-010-module-load-attempt.png` | Metasploit console startup and initial attempt to load the `smb_ms17_010` scanner module. |
| `05-eternalblue-not-vulnerable.png` | `auxiliary/scanner/smb/smb_ms17_010` and `exploit/windows/smb/ms17_010_eternalblue` both reporting the target is **not vulnerable** — an honest "it didn't work" result showing real methodology, not a cherry-picked win. |
| `06-msf-console-ms17-010-scanner.png` | Metasploit console (v6.1.27-dev) setting `RHOSTS` and running the MS17-010 scanner against `192.168.56.21`. |
| `07-psexec-credential-failure.png` | `windows/smb/psexec` attempt with `SMBUser TEST-SAM` and a guessed password failing with `STATUS_LOGON_FAILURE` (invalid credentials). |
| `08-psexec-service-start-issues.png` | Later `psexec` attempts with valid credentials authenticating successfully but the service failing to start (`ACCESS_DENIED` / timeout) before eventually succeeding. |
| `09-psexec-success-meterpreter-system-shell.png` | **`psexec` succeeds** — Meterpreter session opened. `sysinfo` confirms `CYBERSAM`, Windows 10 Build 19045; `getuid` confirms **`NT AUTHORITY\SYSTEM`**. |
| `10-vsftpd-backdoor-exploit-root-shell.png` | `exploit/unix/ftp/vsftpd_234_backdoor` against Metasploitable2 (`192.168.56.102`) — backdoor shell spawned, `whoami` confirms **`root`**. |
