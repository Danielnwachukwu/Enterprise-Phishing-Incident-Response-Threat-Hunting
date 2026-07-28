# Enterprise Phishing Incident Response & Threat Hunting

> **An end-to-end SOC investigation of a simulated enterprise phishing attack using Splunk Enterprise, Wazuh, Sysmon, Snort IDS, pfSense, Kali Linux, Ubuntu Linux, and the MITRE ATT&CK Framework.**

---

# Organization

**NAD Cybersecurity Institute**

---

# Business Challenge

NAD Cybersecurity Institute recently launched a cloud-based student portal used for student admissions, course registration, and online learning resources.

Shortly after deployment, an employee in the Admissions Department received a phishing email impersonating Microsoft Security requesting immediate account verification. The email contained a malicious hyperlink (`example.com`) designed to lure the employee into interacting with attacker-controlled infrastructure.

After the malicious link was accessed, multiple security monitoring platforms began detecting suspicious activity across the enterprise environment. What initially appeared to be a phishing incident quickly evolved into a multi-stage cyber attack involving reconnaissance, exploitation, privilege escalation, persistence, defense evasion, internal discovery, credential collection, attempted data exfiltration, and lateral movement.

The Security Operations Center (SOC) was tasked with investigating the incident, reconstructing the attack timeline, identifying indicators of compromise (IOCs), containing the threat, eradicating persistence mechanisms, and documenting the complete incident response process.

---

# Project Objectives

This project demonstrates how a SOC analyst investigates an enterprise attack from initial compromise through attacker containment by:

- Investigating a phishing-based initial access vector.
- Correlating endpoint, network, and SIEM telemetry.
- Performing enterprise threat hunting across multiple platforms.
- Mapping attacker behavior to the MITRE ATT&CK Framework.
- Reconstructing the complete attack timeline.
- Identifying Indicators of Compromise (IOCs).
- Producing forensic evidence for each attack phase.
- Demonstrating detection engineering and incident response techniques.

---

# Lab Environment

| Component | Technology |
|-----------|------------|
| SIEM | Splunk Enterprise |
| HIDS / XDR | Wazuh |
| Endpoint Telemetry | Sysmon |
| IDS | Snort IDS |
| Firewall | pfSense |
| Attacker Machine | Kali Linux |
| Target Server | Ubuntu Linux |
| Investigation Workstation | Windows 11 |
| Threat Intelligence | VirusTotal, AbuseIPDB, WHOIS |
| Framework | MITRE ATT&CK |

---

# Attack Timeline

The investigation follows the complete attacker lifecycle.

| Phase | Description |
|--------|-------------|
| **00** | Lab Setup & Verification |
| **01** | Reconnaissance |
| **02** | Initial Access |
| **03** | Exploitation |
| **04** | Privilege Escalation |
| **05** | Persistence |
| **06** | Defense Evasion |
| **07** | Discovery |
| **08** | Collection |
| **09** | Exfiltration |
| **10** | PowerShell Investigation |
| **11** | Lateral Movement |

---

# Investigation Workflow

## 00. Lab Setup & Verification

Validated the monitoring infrastructure before the attack simulation.

- Sysmon service verification
- Splunk log ingestion validation
- Event ID distribution
- Endpoint telemetry verification

---

## 01. Reconnaissance

The attacker performed external reconnaissance against the target.

Activities included:

- Web content discovery
- Directory enumeration
- Gobuster reconnaissance
- Wazuh detection of reconnaissance activity

---

## 02. Initial Access

The attack began with a phishing campaign targeting an employee.

Investigation included:

- Phishing email analysis
- Email header authentication
- SPF validation
- DKIM verification
- DMARC validation
- PhishTool forensic analysis
- SSH credential discovery
- Splunk process correlation

---

## 03. Exploitation

Following initial access, the attacker exploited vulnerable services.

Activities investigated:

- SQLMap exploitation
- SSH compromise
- Wazuh detections
- Snort IDS alerts

---

## 04. Privilege Escalation

The attacker escalated privileges to obtain administrative access.

Evidence included:

- Sudo investigation
- SUID binary enumeration
- Root privilege acquisition
- Wazuh root access detection

---

## 05. Persistence

The attacker established mechanisms for long-term access.

Investigated techniques:

- Cron scheduled task persistence
- SSH Authorized Keys backdoor
- Splunk persistence detections

---

## 06. Defense Evasion

The attacker attempted to avoid detection.

Observed techniques:

- Living-off-the-Land Binaries (LOLBins)
- Encoded PowerShell execution
- Windows Defender tampering

---

## 07. Discovery

After gaining persistence, the attacker mapped the internal environment.

Activities included:

- System enumeration
- User discovery
- File system discovery
- Network discovery
- Data collection
- Threat Intelligence (VirusTotal, AbuseIPDB, WHOIS)
- Splunk threat hunting

---

## 08. Collection

The attacker gathered sensitive information before exfiltration.

Evidence includes:

- Credential collection
- Screen capture investigation

---

## 09. Exfiltration

The attacker attempted to transfer collected information outside the environment.

SOC investigation focused on:

- PowerShell web requests
- Outbound transfer investigation
- Data exfiltration indicators

---

## 10. PowerShell Investigation

A dedicated forensic investigation into PowerShell activity.

Analysis included:

- Encoded PowerShell detection
- Process creation analysis
- Command-line investigation
- Sysmon Event ID 1 correlation
- Wazuh PowerShell alerts

---

## 11. Lateral Movement

Following compromise, the attacker attempted to pivot across the environment.

Investigated techniques:

- SSH client activity
- Remote service execution
- Scheduled task movement

---

# MITRE ATT&CK Coverage

This project demonstrates detections across multiple ATT&CK tactics.

| Tactic |
|---------|
| Reconnaissance |
| Initial Access |
| Execution |
| Persistence |
| Privilege Escalation |
| Defense Evasion |
| Discovery |
| Collection |
| Exfiltration |
| Lateral Movement |

---

# Skills Demonstrated

- Security Operations Center (SOC) Investigation
- Incident Response
- Threat Hunting
- Digital Forensics
- Detection Engineering
- SIEM Engineering
- Endpoint Detection & Response (EDR)
- Host Intrusion Detection (HIDS)
- Log Correlation
- MITRE ATT&CK Mapping
- Linux Security
- Windows Security
- PowerShell Analysis
- Email Security Analysis
- Threat Intelligence Analysis
- Network Security Monitoring
- IDS Investigation
- Root Cause Analysis


# Incident Response Report

A complete enterprise incident response report is included
with this repository.

The report documents the investigation from the initial
phishing compromise through containment, eradication,
recovery, and post-incident analysis.

The report includes the following sections:

- Executive Summary
- Business Challenge
- Incident Overview
- Business Impact Assessment
- Attack Timeline
- Root Cause Analysis
- MITRE ATT&CK Mapping
- Indicators of Compromise (IOCs)
- Evidence Collection
- Threat Hunting Findings
- Detection Analysis
- Containment Actions
- Eradication Activities
- Recovery Procedures
- Lessons Learned
- Security Recommendations
- Conclusion

The report demonstrates how a Security Operations Center (SOC)
documents an enterprise phishing investigation while
communicating technical findings to security analysts,
management, and executive stakeholders.

---

# Evidence Summary

This investigation is supported by a comprehensive collection
of forensic evidence gathered throughout the simulated
enterprise phishing incident.

Each phase of the investigation contains screenshots,
detections, and supporting artifacts that document
attacker activity and the corresponding SOC analysis.

| Investigation Phase | Evidence Collected |
|---------------------|------------------:|
| Lab Setup & Verification | 4 |
| Reconnaissance | 5 |
| Initial Access | 11 |
| Exploitation | 9 |
| Privilege Escalation | 4 |
| Persistence | 5 |
| Defense Evasion | 3 |
| Discovery | 20 |
| Collection | 2 |
| Exfiltration | 1 |
| PowerShell Investigation | 7 |
| Lateral Movement | 3 |

**Total Evidence Collected:** **74 screenshots**

The evidence includes attacker actions, SIEM detections,
endpoint telemetry, network alerts, forensic investigations,
and external threat intelligence used to reconstruct the
complete attack lifecycle.



# Repository Structure

```text
Enterprise-Phishing-Incident-Response-Threat-Hunting
│
├── 00_Lab_Setup_and_Verification
│
├── 01_Reconnaissance
│
├── 02_Initial_Access
│
├── 03_Exploitation
│
├── 04_Privilege_Escalation
│
├── 05_Persistence
│
├── 06_Defense_Evasion
│
├── 07_Discovery
│
├── 08_Collection
│
├── 09_Exfiltration
│
├── 10_PowerShell_Investigation
│
├── 11_Lateral_Movement
│
├── Enterprise_Phishing_Incident_Response_Report.pdf
│
└── README.md
```

---

# Evidence Organization

Each investigation folder contains:

- A dedicated README explaining the attack phase.
- Investigation objectives.
- MITRE ATT&CK mapping.
- Business context.
- Detection workflow.
- Evidence screenshots.
- Findings.
- Lessons learned.

This structure allows readers to follow the complete attack lifecycle while understanding how each detection contributed to the overall investigation.

---

# Key Outcomes

This project demonstrates a complete enterprise phishing incident response investigation from the initial phishing email through attempted lateral movement.

The investigation correlates telemetry from Splunk Enterprise, Wazuh, Sysmon, Snort IDS, and Linux endpoint logs to reconstruct attacker behavior across every phase of the intrusion lifecycle. Each stage is documented with forensic evidence, MITRE ATT&CK mappings, and detection logic to reflect how a Security Operations Center investigates, validates, and responds to a modern enterprise attack.

---

# Lessons Learned

This investigation reinforces several key defensive principles:

- Layered security monitoring provides greater visibility than relying on a single tool.
- Correlating endpoint, network, and SIEM telemetry improves detection accuracy.
- Early phishing detection can prevent attackers from progressing through later attack stages.
- Continuous monitoring of PowerShell, SSH, scheduled tasks, and outbound connections is critical for identifying advanced adversary behavior.
- Mapping detections to the MITRE ATT&CK Framework helps standardize investigations and improve incident response maturity.

---

# Disclaimer

This project was developed in a controlled laboratory environment for cybersecurity education, threat hunting, and incident response training. All attacks were simulated against intentionally vulnerable systems owned and operated by the project author. No production systems or third-party environments were targeted.
