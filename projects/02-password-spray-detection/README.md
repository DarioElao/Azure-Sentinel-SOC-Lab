# Project 02 – Password Spray Detection

## Overview

Built and validated a Microsoft Sentinel detection for password spraying against Windows authentication logs.

The project simulates failed authentication attempts against multiple local accounts, correlates Event ID 4625 activity using KQL, and generates a Sentinel incident for SOC investigation.

## Objectives

* Detect password spraying with KQL
* Configure a Microsoft Sentinel Analytics Rule
* Investigate and validate generated alerts
* Map detections to MITRE ATT&CK
* Document the SOC investigation process

## Environment

* Microsoft Azure
* Microsoft Sentinel
* Log Analytics Workspace
* Azure Monitor Agent
* Windows 11
* Kusto Query Language (KQL)

## Detection Logic

The detection identifies:

> **5 or more unique accounts targeted by failed authentication attempts from the same source within 10 minutes.**

### Key Configuration

| Setting      | Value                         |
| ------------ | ----------------------------- |
| Severity     | Medium                        |
| Frequency    | Every 5 minutes               |
| Lookback     | 10 minutes                    |
| Event        | Windows 4625                  |
| MITRE ATT&CK | T1110.003 – Password Spraying |

## Results

The controlled simulation generated:

* **10** failed authentication attempts
* **5** targeted accounts
* **~4 minutes** attack duration
* **1** Sentinel alert
* **1** Sentinel incident
* **0** successful logons observed

The detection was successfully validated and the incident was investigated and closed as an authorized lab simulation.

## MITRE ATT&CK

**Credential Access → T1110.003 – Password Spraying**

## Skills Demonstrated

`Microsoft Sentinel` `KQL` `Azure Monitor` `Windows Event Logs` `Detection Engineering` `Incident Investigation` `MITRE ATT&CK` `SOC Operations`

## Project Evidence

Detailed KQL queries, investigation notes, screenshots, and architecture diagrams are included in this repository.

## Future Improvements

* Detect remote password spraying
* Add automated response with Sentinel Playbooks

