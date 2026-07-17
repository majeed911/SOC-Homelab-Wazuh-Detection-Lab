# Brute Force Detection

## Objective

Detect multiple failed Windows logon attempts using a custom Wazuh correlation rule.

---

## Environment

- Windows 10
- Sysmon
- Wazuh Agent
- Wazuh Manager 4.12
- Ubuntu Server
- VirtualBox

---

## Attack Simulation

Multiple failed logon attempts were generated using an invalid Windows account.

Example:

- Username: hacker2
- Event ID: 4625

---

## Detection Logic

A custom Wazuh rule was created to detect repeated failed logon events.

Base Rule ID:
60122

Custom Rule:
100101

Frequency:
5 Events

Timeframe:
60 Seconds

Alert Level:
12

MITRE ATT&CK:
T1110 – Brute Force

---

## Investigation

The Windows Security Log generated multiple Event ID 4625 entries.

After five failed logon attempts within sixty seconds, Wazuh generated the custom alert:

Possible Brute Force Attack Detected

---

## Evidence

### Detection Alert

![Detection Alert](../images/brute-force-alert.png)

---

### Failed Logon Events

![Failed Logons](../images/brute-force-events.png)

---

## Lessons Learned

- Windows Event ID 4625 represents failed authentication attempts.
- Wazuh correlation rules can detect repeated attack behavior.
- Mapping detections to MITRE ATT&CK improves investigation.
- Custom rules reduce analyst workload by highlighting suspicious activity.

---

## Future Improvements

- Email notifications
- Active Response
- Account Lockout Detection
- Dashboard visualization
