# SOC-Homelab-Wazuh-Detection-Lab
SOC Homelab using Wazuh and Sysmon for Detection Engineering.


# 🛡️ SOC Homelab - Wazuh Detection Lab

## Overview

This project demonstrates a Security Operations Center (SOC) homelab built using Wazuh and Sysmon to detect and investigate Windows security events.

The lab simulates real-world attacker techniques and validates custom detection rules using Wazuh.

---

## Lab Environment

- Windows 10
- Ubuntu Server
- Wazuh Manager 4.12
- Wazuh Agent
- Sysmon
- VirtualBox

---

## Detection Use Cases

### ✅ PowerShell launching CMD

- Windows Event ID: Sysmon Event ID 1
- MITRE ATT&CK: T1059.001
- Detection: Custom Wazuh Rule

---

### ✅ Local Administrator Group Modification

Detects when a user is added to the local Administrators group.

Example:

```
net localgroup administrators hacker /add
```

MITRE ATT&CK:
- T1484

---

### ✅ Brute Force Detection

Custom correlation rule that detects multiple failed logon attempts.

Conditions:

- 5 failed logins
- within 60 seconds

Generated Alert:

```
Possible Brute Force Attack Detected
```

MITRE ATT&CK:

- T1110

---

## Skills Demonstrated

- Detection Engineering
- Windows Event Analysis
- Wazuh SIEM
- Sysmon
- MITRE ATT&CK
- Incident Investigation
- Custom XML Rules
- SOC Monitoring

---

## Project Status

🚧 In Progress

More detection rules and attack simulations will be added.
