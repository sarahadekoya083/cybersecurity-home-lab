Phase 3 screenshots
## Phase 3 — Active Directory Domain Controller Setup

Standing up Active Directory Domain Services (AD DS) and Certificate Services (AD CS) on Windows Server 2019.

| Screenshot | Description |
|---|---|
| `01-shutdown-event-tracker.png` | Windows Shutdown Event Tracker after an unexpected VM restart mid-configuration. |
| `02-adcs-adds-roles-installed.png` | Server Manager dashboard confirming both **AD CS** and **AD DS** roles installed, with a pending "Post-deployment Configuration" flag for AD CS. |
| `03-post-deployment-config-notice.png` | Close-up of the AD CS post-deployment configuration notification. |
| `04-powershell-installaddsforest-failure.png` | Attempted domain promotion via PowerShell (`Install-ADDSForest -DomainName "yourdomain.local"`), which failed with a parameter error (`'NewDomain' was not recognized`). Pivoted to the GUI wizard after this. |
| `05-adds-wizard-already-dc-error.png` | AD DS Configuration Wizard error encountered while adding the server as a DC for `CyberGuardian.local`: *"target server is already a domain controller."* |
| `06-adcs-configuration-wizard-credentials.png` | AD CS Configuration Wizard — Credentials step, configuring the Certificate Authority role on `CyberGuardian-SAM.CyberGuardian.local`. |
| `07-firewall-off-pfsense-gateway-tutorial.png` | Disabling Windows Firewall (lab-only, not recommended in production) while following the tutorial steps to set pfSense as the Domain Controller's default gateway (`192.168.2.10` / gateway `192.168.2.1`). |
| `08-tutorial-checkpoint.png` | Checkpoint marker showing where I paused in the tutorial, for resuming the walkthrough later. |
| `09-network-and-internet-settings-check.png` | Verifying Control Panel network settings applied correctly on the Domain Controller. |
