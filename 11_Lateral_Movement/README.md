# Lateral Movement

## Overview

Lateral Movement is the phase where an attacker attempts to move from one compromised system to other hosts within the network in order to expand access, increase privileges, and reach high-value assets.

In this simulated incident involving the **NAD Cybersecurity Institute**, the attacker attempted multiple lateral movement techniques after compromising the Ubuntu server. These activities included SSH-based movement, remote service execution, and scheduled task execution. The Security Operations Center (SOC) investigated these activities using Splunk telemetry to identify attacker movement across the environment.

---

# Objectives

- Detect SSH-based lateral movement.
- Investigate remote service creation.
- Identify scheduled task execution used for remote movement.
- Correlate process execution with network activity.
- Produce evidence supporting lateral movement detection.

---

# Business Scenario

After successfully compromising the initial host, the attacker attempted to pivot deeper into the environment by leveraging legitimate administrative protocols and remote execution techniques.

SOC analysts investigated the activity using Splunk Enterprise and endpoint telemetry to determine whether the attacker attempted to establish access to additional systems within the NAD Cybersecurity Institute network.

The investigation confirmed multiple indicators consistent with lateral movement techniques commonly observed during enterprise intrusions.

---

# Tools Used

- Splunk Enterprise
- Sysmon
- Windows Event Logs
- SSH
- MITRE ATT&CK Framework

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|------|
| Lateral Movement | Remote Services | T1021 |
| Lateral Movement | SSH | T1021.004 |
| Lateral Movement | Scheduled Task | T1053 |
| Execution | Command and Scripting Interpreter | T1059 |

---

# Investigation Workflow

1. Investigate SSH client activity.
2. Detect remote service creation.
3. Identify scheduled task execution.
4. Correlate process execution events.
5. Validate lateral movement attempts.
6. Document evidence supporting attacker pivoting.

---

# Evidence

## SSH Client Activity

The attacker initiated SSH sessions in an attempt to access additional systems within the environment.

### Evidence

**13_SSH_Client_Process_Creation.png**

- Splunk investigation identifying SSH client process creation used for remote access.

---

## Scheduled Task Movement

The attacker attempted to leverage scheduled tasks to execute commands remotely.

### Evidence

**26_Remote_Scheduled_Task_Detection.png**

- Splunk investigation detecting remote scheduled task execution associated with lateral movement.

---

## Remote Service Execution

The attacker attempted remote service creation to facilitate movement between systems.

### Evidence

**27_Remote_Service_Creation.png**

- Splunk investigation identifying remote service creation activity.

---

# Findings

The investigation confirmed multiple lateral movement indicators following successful compromise of the initial host.

Observed attacker behavior included:

- SSH client execution.
- Remote service creation.
- Scheduled task execution.
- Administrative remote access techniques.
- Attempts to expand access within the environment.

These findings demonstrate how attackers use trusted administrative mechanisms to move between systems while attempting to remain undetected.

---

# Detection Summary

| Platform | Detection |
|----------|-----------|
| Splunk | SSH Client Process Creation |
| Splunk | Remote Scheduled Task Detection |
| Splunk | Remote Service Creation |
| Sysmon | Process Creation Events |
| Windows Event Logs | Remote Administrative Activity |

---

# Lessons Learned

Lateral movement often marks the transition from compromising a single endpoint to compromising an entire enterprise environment.

Organizations should continuously monitor remote service creation, SSH activity, scheduled task execution, and administrative process creation. Correlating endpoint telemetry with SIEM detections enables defenders to identify attacker pivoting early and contain compromises before critical systems are affected.
