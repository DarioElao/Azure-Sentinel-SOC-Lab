# Investigation — Failed Network Authentication

## Detection

**Rule:** SOC-LAB - Failed Network Authentication
**Event ID:** 4625
**Logon Type:** 3 — Network
**Severity:** Medium
**MITRE ATT&CK:** T1110 — Brute Force

## Observed Event

The detection identified a failed network authentication attempt on the Windows endpoint.

| Field          | Value                             |
| -------------- | --------------------------------- |
| Computer       | `SOC-WIN11-01`                    |
| Target Account | `Administrator`                   |
| Logon Type     | `3`                               |
| Source IP      | `::1`                             |
| Failure Reason | Unknown user name or bad password |
| Authentication | NTLM                              |

## Investigation

The event generated a Microsoft Sentinel alert and was associated with **Incident #2**.

The source address `::1` is the IPv6 loopback address, indicating that the authentication attempt originated locally from the Windows endpoint used for testing.

The event was therefore consistent with the controlled authentication activity performed during the lab rather than an external source attempting to access the system.

Entity mapping was configured to associate the detection with the relevant **device and IP address**, improving the context available during investigation.

## Classification

**Classification:** Informational, expected activity
**Determination:** Security testing

The alert was intentionally generated to validate the detection pipeline.

## Investigation Outcome

The detection successfully identified the test authentication event and generated the expected Sentinel alert and incident.

The investigation also confirmed that the detection could provide useful context for future authentication investigations through:

* Account identification
* Source IP identification
* Device identification
* Logon type
* Authentication failure reason

## Validation

The detection was validated through the following workflow:

```text
Windows Event 4625
        ↓
Log Analytics
        ↓
KQL Detection
        ↓
Sentinel Analytics Rule
        ↓
Alert
        ↓
Incident
        ↓
Entity Mapping
        ↓
Investigation
        ↓
Classification
```
