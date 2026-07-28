# Exfiltration

## Overview

Exfiltration is the final stage of the attack lifecycle where an adversary attempts to transfer collected data from the compromised environment to an external destination.

In this simulated incident involving the **NAD Cybersecurity Institute**, the attacker used PowerShell web requests to prepare and simulate outbound data transfer after completing reconnaissance, initial access, exploitation, privilege escalation, persistence, defense evasion, discovery, and collection.

The Security Operations Center (SOC) investigated these outbound PowerShell activities using Splunk to determine whether sensitive institutional data had been transferred outside the network.

---

# Objectives

- Detect outbound PowerShell web transfer activity.
- Investigate potential data exfiltration attempts.
- Correlate PowerShell execution with network events.
- Validate indicators of data theft.
- Produce evidence supporting incident containment.

---

# Business Scenario

After collecting sensitive information from the compromised Ubuntu server, the attacker attempted to transfer the staged data using PowerShell web requests.

SOC analysts investigated the suspicious outbound activity using Splunk telemetry and process execution logs to determine whether institutional data belonging to NAD Cybersecurity Institute had been successfully exfiltrated.

The investigation confirmed suspicious PowerShell-based outbound communication consistent with data exfiltration behavior.

---

# Tools Used

- Splunk Enterprise
- Sysmon
- PowerShell Logging
- MITRE ATT&CK Framework

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|------|
| Exfiltration | Exfiltration Over Web Service | T1567 |
| Exfiltration | Exfiltration Over Command and Control Channel | T1041 |
| Execution | PowerShell | T1059.001 |

---

# Investigation Workflow

1. Identify suspicious PowerShell web requests.
2. Investigate outbound network activity.
3. Correlate PowerShell execution with process telemetry.
4. Validate attempted data transfer.
5. Document exfiltration indicators.

---

# Evidence

## PowerShell Web Transfer Investigation

The attacker attempted to transfer collected information using PowerShell web requests.

### Evidence

**PowerShell Web Transfer**

**44_PowerShell_Web_Transfer_Investigation.png**

- Splunk investigation identifying PowerShell web transfer activity associated with attempted data exfiltration.

---

# Findings

The investigation confirmed evidence of outbound PowerShell activity consistent with attacker attempts to exfiltrate sensitive information.

Observed attacker behavior included:

- PowerShell web requests.
- Outbound network communication.
- Data transfer preparation.
- Exfiltration attempt following information collection.

These findings indicate the attack had progressed through the complete intrusion lifecycle from phishing to attempted data theft.

---

# Detection Summary

| Platform | Detection |
|----------|-----------|
| Splunk | PowerShell web transfer investigation |
| Sysmon | PowerShell process execution |
| Windows Event Logs | Outbound process activity |

---

# Lessons Learned

Data exfiltration is often the final opportunity for defenders to detect and stop an attacker before sensitive information leaves the organization.

Organizations should continuously monitor outbound network connections, PowerShell activity, web requests, and abnormal data transfer behavior. Combining endpoint telemetry with SIEM correlation rules enables rapid detection and containment of exfiltration attempts before business-critical information is lost.
