# Enterprise Phishing Incident Response & Threat Hunting

## Organization

**NAD Cybersecurity Institute**

---

## Business Challenge

NAD Cybersecurity Institute recently launched a cloud-based student portal for admissions, course registration, and learning resources.

An employee in the Admissions Department received a phishing email impersonating Microsoft requesting urgent account verification. The email contained a malicious hyperlink (`example.com`).

After the employee clicked the malicious link, security monitoring platforms began detecting suspicious activity across multiple systems.

The Security Operations Center (SOC) initiated an incident response investigation to identify the attack timeline, contain the compromise, eradicate persistence, recover affected systems, and document the incident.

---

# Investigation Objectives

- Analyze phishing email artifacts
- Investigate attacker activity across multiple security platforms
- Correlate logs from Splunk, Wazuh, Sysmon and Snort
- Map attacker behavior to the MITRE ATT&CK Framework
- Produce a complete incident response timeline
- Document indicators of compromise (IOCs)
- Recommend containment and remediation actions

---

# Technologies Used

| Category | Technology |
|----------|------------|
| SIEM | Splunk Enterprise |
| Endpoint Monitoring | Sysmon |
| HIDS | Wazuh |
| IDS | Snort |
| Firewall | pfSense |
| Attacker Machine | Kali Linux |
| Target Server | Ubuntu Linux |
| Analysis Workstation | Windows 11 |
| Threat Intelligence | VirusTotal, AbuseIPDB, WHOIS |

---

# Investigation Workflow

## 00. Lab Setup & Verification

- Sysmon service verification
- Splunk log ingestion validation
- Event ID distribution analysis
- Endpoint telemetry verification

---

## 01. Reconnaissance

- Web content discovery
- Directory enumeration
- Reconnaissance detection using Wazuh

---

## 02. Initial Access

- Phishing email analysis
- Email header analysis
- SPF / DKIM / DMARC validation
- PhishTool forensic analysis
- SSH brute-force attack investigation
- Initial SIEM detections

---

## 03. Exploitation

- SQLMap exploitation
- SSH compromise
- Wazuh detections
- Snort IDS alerts

---

## 04. Privilege Escalation

- Sudo abuse
- SUID binary enumeration
- Root privilege acquisition

---

## 05. Persistence

- Cron job persistence
- SSH Authorized Keys backdoor

---

## 06. Defense Evasion

- Living-off-the-Land Binaries (LOLBins)
- Encoded PowerShell
- Windows Defender tampering

---

## 07. Discovery

- Network discovery
- User discovery
- File system enumeration
- System information discovery

---

## 08. Collection

- Sensitive file discovery
- Data collection
- Archive creation

---

## 09. Exfiltration

- PowerShell web transfer
- Data transfer investigation

---

## 10. PowerShell Investigation

- Encoded PowerShell detection
- Process creation analysis
- Command-line investigation
- Sysmon Event ID 1 correlation

---

## 11. Threat Intelligence

- VirusTotal analysis
- AbuseIPDB reputation checks
- WHOIS infrastructure analysis

---

# MITRE ATT&CK Coverage

- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Defense Evasion
- Discovery
- Collection
- Exfiltration

---

# Skills Demonstrated

- Incident Response
- Threat Hunting
- Digital Forensics
- SIEM Engineering
- Detection Engineering
- Endpoint Detection & Response
- Network Security Monitoring
- Log Correlation
- MITRE ATT&CK Mapping
- IOC Analysis
- Linux Security
- Windows Security
- PowerShell Analysis
- Threat Intelligence

---

# Repository Structure

```text
Enterprise-Phishing-Incident-Response-Threat-Hunting
│
├── 00_Lab_Setup_and_Verification
├── 01_Reconnaissance
├── 02_Initial_Access
├── 03_Exploitation
├── 04_Privilege_Escalation
├── 05_Persistence
├── 06_Defense_Evasion
├── 07_Discovery
├── 08_Collection
├── 09_Exfiltration
├── 10_PowerShell_Investigation
├── 11_Threat_Intelligence
├── Incident_Report.pdf
└── README.md
```

---

# Key Outcomes

This investigation demonstrates a complete enterprise phishing incident response workflow, correlating endpoint, network, and SIEM telemetry across multiple security platforms to reconstruct attacker activity from initial phishing email delivery through data exfiltration.

The project highlights practical SOC investigation techniques, threat hunting, forensic analysis, and detection engineering aligned with industry best practices.
