# Active Directory Splunk Home Lab
A home lab made to practice Active Directory administration, centralized log collection, and security monitoring using Splunk.

## Objective
Built a four-VM home lab with a Windows Server, Windows domain, a Splunk SIEM, and a Kali Linux attacker machine to practice detecting simulated attacks.

## Environment
- Windows Server 2022 – Domain Controller (Sysmon, Splunk Universal Forwarder)
- Windows 10 – Domain-joined endpoint (Sysmon, Splunk Universal Forwarder, Atomic Red Team)
- Ubuntu Server – Splunk Enterprise
- Kali Linux – Attacker machine (NetExec)

![Lab Diagram](Lab%20Network%20Diagram/AD%20project%20diagram.drawio.png)

## Implementation
- Installed Splunk Enterprise on the Ubuntu Server and configured it so it was able to receive forwarded logs.
- Installed both Sysmon and Splunk Universal Forwarder on the Windows 10 machine and Windows Server to send endpoint and authentication logs to Splunk.
- Set up Active Directory Domain Services on the Windows Server 2022 and join the Windows 10 machine to the domain.
- Used NetExec from Kali Linux to run RDP credential attacks against the Windows 10 endpoint.
- Searched Splunk for the Event ID 4625 (failed logon) and the Event ID 4624 (successful logon) events that resulted from the attack.
- Used Atomic Red Team on the Windows 10 endpoint to simulate MITRE ATT&CK techniques to generate additional telemetry in Splunk.

## Results
- The Sysmon and Windows Security logs from both Windows machines were forwarded to and searchable in Splunk successfully.
- The NetExec RDP attack successfully produced Event ID 4625 failed logons, then was followed by a successful login (Event ID 4624), which I analyzed inside of Splunk.
- Atomic Red Team generated additional endpoint telemetry that I reviewed in Splunk.
