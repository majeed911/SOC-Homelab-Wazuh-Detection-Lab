# 🛡️ Detection Scenario 2: PowerShell Spawning CMD Execution

## 1. Overview
In Windows attack chains, adversaries frequently leverage native execution utilities (**Living off the Land - LotL**) to bypass traditional security controls. This project documents the creation, implementation, and testing of a custom **Wazuh Detection Rule** designed to identify instances where `powershell.exe` spawns an interactive `cmd.exe` process.

---

## 2. Environment Setup
* **SIEM / XDR Manager:** Wazuh Manager (Ubuntu Server)
* **Endpoint Agent:** Windows 10 (`SOC-WIN10`)
* **Telemetry Engine:** Microsoft Sysmon (`Microsoft-Windows-Sysmon/Operational`)
* **Event Log Monitored:** Sysmon Event ID 1 (Process Creation)

---

## 3. Attack Simulation
1. Opened an interactive **PowerShell** session on the target Windows endpoint.
2. Executed `cmd.exe` directly within PowerShell.
3. Observed process parentage hierarchy:
   * **Parent Process:** `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`
   * **Child Process:** `C:\Windows\System32\cmd.exe`

---

## 4. Custom Detection Logic

```xml
<rule id="100002" level="10">
  <if_sid>92004</if_sid>
  <field name="win.eventdata.parentimage" type="pcre2">(?i)\\powershell\.exe$</field>
  <field name="win.eventdata.image" type="pcre2">(?i)\\cmd\.exe$</field>
  <description>Suspicious Process Creation : PowerShell spawned CMD.exe</description>
  <mitre>
    <id>T1059.001</id>
    <id>T1059.003</id>
  </mitre>
</rule>
