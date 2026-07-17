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

Multiple failed Windows logon attempts were generated against a non-existent local account (hacker2) to simulate a brute force attack.

Windows generated Security Event ID 4625 for each failed authentication attempt.

---

## Detection Logic

A custom Wazuh correlation rule was created to detect repeated failed authentication attempts.

| Item | Value |
|------|------|
| Base Rule | 60122 |
| Custom Rule | 100101 |
| Event ID | 4625 |
| Frequency | 5 Events |
| Timeframe | 60 Seconds |
| Alert Level | 12 |
| MITRE ATT&CK | T1110 - Brute Force |

---

## Investigation

The Windows Security Log generated multiple Event ID 4625 entries.

After five failed logon attempts within sixty seconds, Wazuh generated the custom alert:

Possible Brute Force Attack Detected

---

## Evidence

### Detection Alert

![Detection Alert](../images/brute-force-alert)

---

### Failed Logon Events

![Failed Logons](../images/brute-force-events)

---

## Lessons Learned

- Windows Security Event ID 4625 records failed authentication attempts.
- Correlation rules help distinguish attack patterns from isolated events.
- Mapping detections to MITRE ATT&CK provides valuable threat context.
- Custom detection rules improve SOC visibility and reduce alert fatigue.
---

## Future Improvements

- Configure Active Response
- Send Email Notifications
- Detect Password Spraying
- Detect Account Lockout (Event ID 4740)
- Integrate Sigma Rules
- Build Detection Dashboard
