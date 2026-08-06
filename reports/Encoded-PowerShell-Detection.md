# Encoded PowerShell Detection

## Objective

Detect the execution of Base64-encoded PowerShell commands using Wazuh.

---

## Environment

- Ubuntu Server
- Windows 10
- Wazuh Manager 4.12
- Wazuh Agent
- Sysmon
- VirtualBox

---

## Attack Simulation

An encoded PowerShell command was executed to simulate attacker behavior using the `-EncodedCommand` parameter.

This technique is commonly used by attackers to hide malicious commands.

---

## Detection Logic

A custom Wazuh rule was created based on the built-in detection.

| Item | Value |
|------|-------|
| Base Rule | 92057 |
| Custom Rule | 100003 |
| Alert Level | 12 |
| MITRE ATT&CK | T1059.001, T1027 |

---

## Investigation

The original Wazuh rule detected the execution of an encoded PowerShell command.

A custom rule was then created to generate a dedicated alert for suspicious encoded PowerShell execution.

---

## Evidence

### Built-in Detection

![Encoded PowerShell Alert](../images/encoded-powershell-alert)

---

### Custom Rule

![Custom Rule](../images/encoded-powershell-rule)

---

## Lessons Learned

- Attackers frequently use Base64-encoded PowerShell commands to evade detection.
- Wazuh can detect encoded PowerShell activity using built-in rules.
- Custom rules can improve alert visibility and support future correlation logic.
- Mapping detections to MITRE ATT&CK provides additional investigation context.

---

## Future Improvements

- Detect PowerShell Download Cradles
- Detect Invoke-Expression (IEX)
- Detect AMSI Bypass Techniques
- Correlate with Network Connections
