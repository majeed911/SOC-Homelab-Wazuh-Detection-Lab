# PowerShell Spawning CMD Detection

## Objective

Detect when PowerShell launches Command Prompt (cmd.exe) using Sysmon process creation events and a custom Wazuh detection rule.

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

PowerShell was launched and used to spawn a new Command Prompt process.

Example:

```powershell
powershell.exe
cmd.exe
```

Sysmon generated a Process Create event recording the parent-child relationship.

---

## Detection Logic

A custom Wazuh rule was created to detect PowerShell spawning cmd.exe.

| Item | Value |
|------|-------|
| Base Rule | 92004 |
| Custom Rule | 100002 |
| Parent Process | powershell.exe |
| Child Process | cmd.exe |
| Alert Level | 10 |
| MITRE ATT&CK | T1059.001, T1059.003 |

---

## Investigation

Sysmon Event ID 1 recorded the process creation event.

The event showed:

- Parent Process: powershell.exe
- Child Process: cmd.exe

The custom Wazuh rule matched this behavior and generated the alert:

**Suspicious Process Creation: PowerShell Spawned CMD.exe**

---

## Evidence

### Detection Alert

![PowerShell CMD Alert](../images/powershell-cmd-alert)

---

### Custom Detection Rule

![PowerShell CMD Rule](../images/powershell-cmd-rule)

---

## Lessons Learned

- Sysmon Event ID 1 provides valuable process creation telemetry.
- Parent-child process relationships are useful for detecting suspicious execution chains.
- Custom Wazuh rules enable detection of attacker behavior beyond default rules.
- MITRE ATT&CK mapping improves investigation and threat classification.

---

## Future Improvements

- Detect PowerShell spawning rundll32.exe
- Detect PowerShell spawning regsvr32.exe
- Detect PowerShell spawning mshta.exe
- Detect PowerShell Download Cradles
