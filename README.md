# MITRE ATT&CK Technique Reference - Common Network & Windows Log Detections

## Overview
This is a reference document mapping common security log events (Windows Security logs, firewall/network logs) to their corresponding MITRE ATT&CK techniques. Built while learning Splunk and studying the ATT&CK framework, as a foundation for future detection engineering work.

Reference: [attack.mitre.org](https://attack.mitre.org)

## Status
This is a **learning/reference project**, documenting technique mappings and detection logic concepts. Live query testing against real log data is in progress as a separate, ongoing project.

---

## Technique Mapping Table

| Log Source | Event / Indicator | ATT&CK Technique | Technique ID | Tactic |
|---|---|---|---|---|
| Windows Security | Repeated failed logons (EventCode 4625) from one source | Brute Force | T1110 | Credential Access |
| Windows Security | Successful logon (4624) after repeated failures | Valid Accounts | T1078 | Persistence / Initial Access |
| Windows Security | Remote process creation (4688) via PsExec/WMIC/PowerShell | Remote Services | T1021 | Lateral Movement |
| Firewall (e.g. FortiGate) | Single source IP hitting many destination ports | Network Service Discovery | T1046 | Discovery |
| Firewall | Traffic denied/blocked repeatedly from one source | Network Denial of Service (context-dependent) | T1498 | Impact |
| Windows Application Log | Repeated crash of security-related service | Impair Defenses | T1562 | Defense Evasion |

## Why this matters
Mapping raw log events to ATT&CK techniques is the core skill behind writing real SOC detections - it connects "what the log shows" to "what an attacker is actually doing." This table represents the reasoning I'd apply before writing detection logic in Splunk (SPL) or building a SOAR playbook.

## Next steps
- Validate these mappings against real log data (Windows Security logs, FortiGate CSV samples)
- Convert each row into a working SPL detection query
- Build a Splunk SOAR playbook triggered by one of these detections

## Tools referenced
- Splunk (SPL)
- MITRE ATT&CK Framework
- Windows Event Logs, FortiGate firewall logs
