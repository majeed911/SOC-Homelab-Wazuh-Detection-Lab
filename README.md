# 🛡️ SOC Homelab - Wazuh Detection Lab

Hands-on Detection Engineering & Security Monitoring using Wazuh, Sysmon, and Windows Event Logs.

![Wazuh](https://img.shields.io/badge/Wazuh-4.12-blue)

![Windows](https://img.shields.io/badge/Windows-10-blue)

![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-orange)

![Sysmon](https://img.shields.io/badge/Sysmon-Installed-success)

![MITRE](https://img.shields.io/badge/MITRE-T1110-red)

## Overview

This repository documents my hands-on SOC Homelab, built to practice detection engineering, security monitoring, and incident investigation using Wazuh.

The goal is to simulate real-world attack techniques, analyze Windows security events, and improve blue team investigation skills.

---

## 🏗️ Lab Architecture

```mermaid
flowchart LR

A["🖥️ Windows 10 Endpoint<br/>Sysmon + Wazuh Agent"]
--> B["🛡️ Wazuh Manager<br/>Ubuntu Server"]

B --> C["📊 Wazuh Dashboard"]

D["👤 Security Analyst"]
--> C

E["⚔️ Attack Simulation"]
--> A
```

---

## 🖥️ Lab Environment

- Ubuntu Server
- Windows 10
- Wazuh Manager 4.12
- Wazuh Agent
- Sysmon
- VirtualBox

---

## 📊 Skills Demonstrated

- SIEM Monitoring (Wazuh)
- Windows Event Log Analysis
- Sysmon Telemetry Analysis
- Detection Engineering
- Incident Investigation
- MITRE ATT&CK Mapping
- Windows Security Monitoring

## 🔍 Detection Scenarios

##  Brute Force Detection

**Objective**

Detect multiple failed Windows logon attempts using Wazuh.

**Windows Event ID**

- 4625

**MITRE ATT&CK**

- T1110 – Brute Force

- ## Detection Alert

![Brute Force Alert](images/brute-force-alert)

- ## Failed Logon Events

![Failed Logons](images/brute-force-events)
---

## 🚀 Upcoming Detection Labs

- [x] Brute Force Detection
- [ ] PowerShell → CMD Detection
- [ ] User Added to Administrators
- [ ] New Local User Detection
- [ ] Scheduled Task Detection
- [ ] Windows Service Creation
- [ ] RDP Monitoring

---

## 📂 Repository Structure

```text
SOC-Homelab-Wazuh-Detection-Lab
│
├── images/
├── reports/
├── rules/
└── README.md
```
---

## 🎯 Learning Goals

- Detection Engineering
- Windows Event Analysis
- SOC Investigation
- Threat Detection
- MITRE ATT&CK
- Wazuh
- Sysmon

---

⭐ This repository will continue to grow as I build new detection scenarios.
