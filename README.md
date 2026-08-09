# Azure Sentinel SOC Lab

![Microsoft Azure](https://img.shields.io/badge/Microsoft%20Azure-Security-0078D4?logo=microsoftazure\&logoColor=white)
![Microsoft Sentinel](https://img.shields.io/badge/Microsoft%20Sentinel-SIEM-0078D4)
![KQL](https://img.shields.io/badge/KQL-Detection%20Engineering-blue)
![MITRE ATT\&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-T1110-red)

## Overview

This repository documents a hands-on cybersecurity laboratory built in Microsoft Azure to develop and demonstrate practical Security Operations Center (SOC), detection engineering, threat hunting, and incident response capabilities.

The environment uses Microsoft Sentinel, Microsoft Defender, Azure Log Analytics, and a Windows endpoint to simulate real-world security monitoring and investigation workflows.

The goal of this project is not simply to configure security tools, but to understand the complete lifecycle of a security detection:

**Telemetry → Detection → Alert → Incident → Investigation → Classification → Improvement**

---

## Environment

| Component          | Purpose                                        |
| ------------------ | ---------------------------------------------- |
| Microsoft Azure    | Cloud security laboratory                      |
| Microsoft Sentinel | SIEM and security analytics                    |
| Log Analytics      | Security telemetry and KQL analysis            |
| Microsoft Defender | Security operations and incident investigation |
| Windows 11         | Endpoint generating security telemetry         |
| KQL                | Detection engineering and threat hunting       |
| MITRE ATT&CK       | Threat behavior classification                 |

---

# Projects

## Project 01 — Failed Network Authentication Detection

**Status:** ✅ Completed

### Objective

Develop and validate a custom Microsoft Sentinel detection for failed network authentication attempts using Windows Security Event ID **4625**.

### Detection

The detection identifies failed network logons and extracts:

* Target account
* Source IP address
* Target computer
* Logon type
* Authentication failure reason

### Technologies

* Microsoft Sentinel
* Azure Log Analytics
* Windows Security Event Logs
* KQL
* Microsoft Defender
* MITRE ATT&CK

### MITRE ATT&CK

**T1110 — Brute Force**

**TA0006 — Credential Access**

### Investigation Workflow

1. Generate a controlled failed authentication event.
2. Ingest Windows Security Event ID 4625 into Log Analytics.
3. Query the event using KQL.
4. Create a Scheduled Analytics Rule.
5. Generate a Sentinel alert.
6. Create and investigate the resulting incident.
7. Classify the alert as authorized security testing.
8. Configure entity mapping.
9. Validate that the IP address and device are associated with the alert.
10. Analyze the detection and identify opportunities for improvement.

### Detection Result

The detection successfully generated a Microsoft Sentinel incident:

**SOC-LAB - Failed Network Authentication**

The resulting investigation identified:

* **Target:** `SOC-WIN11-01`
* **Target Account:** `Administrator`
* **Logon Type:** `3` — Network
* **Source IP:** `::1`
* **Failure:** Unknown username or bad password
* **Authentication:** NTLM

The alert was intentionally generated as part of controlled security testing and classified as:

**Informational, expected activity — Security testing**

---

## Lessons Learned

This project demonstrated several important SOC and detection engineering concepts:

* Windows Event ID 4625 can provide valuable authentication telemetry.
* KQL can transform raw Windows security events into actionable detections.
* Analytics rules convert detections into operational security alerts.
* MITRE ATT&CK mapping provides behavioral context.
* Entity mapping improves investigation and incident enrichment.
* Log Analytics can be used to independently validate detection queries.
* Incident filtering can affect visibility of otherwise valid detections.
* Detection development often requires iterative troubleshooting and validation.

---

# Portfolio Roadmap

| Project | Focus                                   | Status     |
| ------- | --------------------------------------- | ---------- |
| 01      | Failed Network Authentication Detection | ✅ Complete |
| 02      | Password Spray Detection                | 🔜 Planned |
| 03      | PowerShell Threat Hunting               | 🔜 Planned |
| 04      | RDP Attack Detection                    | 🔜 Planned |
| 05      | Microsoft Defender XDR Investigation    | 🔜 Planned |
| 06      | Automated Incident Response             | 🔜 Planned |
| 07      | Advanced KQL Threat Hunting             | 🔜 Planned |
| 08      | SOC Dashboard & Workbooks               | 🔜 Planned |
| 09      | Purple Team Simulation                  | 🔜 Planned |
| 10      | Enterprise SOC Capstone                 | 🔜 Planned |

---

## Cyber Analyst

**Dario Elao**

Cybersecurity | IT | Networking | Microsoft Security | Detection Engineering

This repository represents an ongoing hands-on cybersecurity laboratory and portfolio documenting practical security engineering and SOC operations.
