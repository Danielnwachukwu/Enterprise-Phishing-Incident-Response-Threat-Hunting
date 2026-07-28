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

Following successful compromise, the attacker attempted to
move laterally by initiating SSH connections to additional
systems within the environment. The Security Operations Center
(SOC) investigated process creation events to determine
whether remote access tools were used to expand the attack.

### SSH Client Process Creation

![SSH Client Process Creation](13_SSH_Client_Process_Creation.png)

Splunk investigation identified the creation of an SSH client
process used to establish remote connections. This activity
provided evidence of the attacker's attempt to access
additional hosts using legitimate remote administration
protocols.

---

# Scheduled Task Investigation

To facilitate remote command execution, the attacker attempted
to leverage scheduled tasks as a lateral movement technique.
SOC analysts investigated task creation events to determine
whether commands had been executed on remote systems.

### Remote Scheduled Task Detection

![Remote Scheduled Task Detection](26_Remote_Scheduled_Task_Detection.png)

Splunk detected activity consistent with remote scheduled task
execution. This technique is commonly used by attackers to
execute commands on remote hosts while minimizing direct user
interaction and maintaining operational stealth.

---

# Remote Service Execution

The attacker also attempted to create or manipulate remote
services as part of lateral movement. Service creation is a
well-known technique used to execute payloads and gain
execution on additional systems within a network.

### Remote Service Execution Investigation

![Remote Service Execution](27_Remote_Service_Execution.png)

Splunk investigation identified activity associated with
remote service execution, providing evidence of an attempt to
move laterally between systems using legitimate Windows
service management functionality.

The investigation enabled analysts to correlate remote
service activity with earlier SSH and scheduled task events,
demonstrating multiple lateral movement techniques employed
during the intrusion.
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
