# Collection

## Overview

The Collection phase represents the attacker's attempt to gather sensitive information from a compromised system before transferring it outside the environment.

In this simulated incident involving the **NAD Cybersecurity Institute**, the attacker collected credential-related information and captured sensitive on-screen data after successfully compromising the Ubuntu server. The Security Operations Center (SOC) investigated these activities using Splunk to determine whether confidential information had been staged for exfiltration.

---

# Objectives

- Detect credential-related file access.
- Identify screen capture activities.
- Correlate collection events using Splunk.
- Determine the attacker's data collection objectives.
- Prepare evidence for the Exfiltration investigation.

---

# Business Scenario

Following successful exploitation, privilege escalation, persistence, defense evasion, and internal discovery, the attacker began collecting valuable information from the compromised host.

Evidence showed attempts to access credential-related files and capture sensitive information displayed on the compromised system. These activities were investigated using Splunk to determine the extent of data collection before any outbound data transfer occurred.

The SOC confirmed that the attacker had successfully staged sensitive information for exfiltration.

---

# Tools Used

- Splunk Enterprise
- Sysmon
- Linux Audit Logs
- MITRE ATT&CK Framework

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|------|
| Collection | Data from Local System | T1005 |
| Collection | Screen Capture | T1113 |
| Collection | Credentials from Password Stores | T1555 |

---

# Investigation Workflow

1. Investigate credential-related file access.
2. Identify screenshot collection activity.
3. Correlate process execution with collection events.
4. Confirm attacker preparation for data exfiltration.

---

# Evidence

## Credential Collection

The attacker accessed files containing sensitive credential information that could later be stolen or abused.

### Evidence

**Credential Collection**

**32_Credential_File_Access_Investigation.png**

- Splunk investigation showing access to sensitive credential-related files on the compromised host.

---

## Screen Capture

The attacker captured information displayed on the compromised system as part of information gathering prior to exfiltration.

### Evidence

**Screen Capture**

**33_Screenshot_Capture_Investigation.png**

- Splunk investigation identifying screen capture activity performed during the attack.

---

# Findings

The investigation confirmed that the attacker had transitioned from system discovery into the Collection phase.

Observed attacker activities included:

- Accessing credential-related files.
- Collecting sensitive local information.
- Capturing on-screen information.
- Preparing collected data for exfiltration.

These actions significantly increased the risk of sensitive data exposure.

---

# Detection Summary

| Platform | Detection |
|----------|-----------|
| Splunk | Credential file access investigation |
| Splunk | Screenshot capture investigation |

---

# Lessons Learned

Collection activities are often one of the final stages before attackers attempt data theft. Monitoring access to sensitive files, credential stores, and screen capture utilities provides defenders with valuable opportunities to detect adversary activity before data leaves the environment.

Organizations should implement file access monitoring, endpoint telemetry, behavioral analytics, and real-time alerts for suspicious collection activities to reduce the likelihood of successful data exfiltration.
