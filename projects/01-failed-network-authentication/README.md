# Project 01 — Failed Network Authentication Detection

**Platform:** Microsoft Azure / Microsoft Sentinel
**Focus:** Detection Engineering, KQL, SOC Investigation
**MITRE ATT&CK:** T1110 — Brute Force

## Overview

This project demonstrates the development and validation of a custom Microsoft Sentinel detection for failed Windows network authentication attempts.

The objective was to apply and reinforce existing skills in KQL, SIEM administration, detection engineering, and security event analysis while building a functional SOC detection within Azure.

## Environment

* Microsoft Azure
* Resource Group (SOC-LAB-RG)
* Windows 11 VM (SOC-WIN11-01)
* Azure Monitor Agent
* Log Analytics Workspace (SOC-LAB-LAW1)
* Microsoft Sentinel
* Scheduled Analytics Rule (SOC-LAB - Failed Network Authentication)
* Alert
* Incident
* SOC Analyst Investigation 

<p align="center">
  <img src="screenshots/Lab-Environment.png" width="600">
</p>

*Figure 1 - Microsoft Sentinel SOC lab environment used for the investigation*

## Detection

The detection monitors:

* **Event ID:** 4625
* **Logon Type:** 3 (Network)
* Target account
* Source IP
* Computer
* Failure reason

The query was implemented as a **Scheduled Analytics Rule**:

`SOC-LAB - Failed Network Authentication`

## Results

The detection successfully generated a Sentinel alert and Incident #2.

Example event:

| Field          | Value                    |
| -------------- | ------------------------ |
| Computer       | `SOC-WIN11-01`           |
| Target Account | `Administrator`          |
| Logon Type     | `3`                      |
| Source IP      | `::1`                    |
| Failure        | Bad username or password |

The detection was mapped to **MITRE ATT&CK T1110 — Brute Force** and enriched with entity mapping for the device and IP address.

The event was intentionally generated as part of controlled security testing and classified as **Informational, expected activity / Security testing**.

## Skills Demonstrated

* KQL query development and validation
* Microsoft Sentinel Analytics Rules
* Windows security event analysis
* Detection engineering
* MITRE ATT&CK mapping
* Entity mapping and alert enrichment
* SOC incident investigation and classification
* Detection troubleshooting and tuning

