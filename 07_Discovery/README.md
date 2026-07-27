# Discovery

## Overview

The Discovery phase represents the attacker's effort to understand the compromised environment before proceeding with additional objectives. During this stage, the attacker enumerated the operating system, identified users and network configuration, searched for sensitive files, collected valuable data, and investigated external infrastructure associated with the phishing campaign.

The Security Operations Center (SOC) correlated Linux command-line evidence, Splunk telemetry, and Open Source Intelligence (OSINT) to reconstruct the attacker's discovery activities and identify the scope of the compromise.

---

# Objectives

- Identify sensitive information collected by the attacker.
- Investigate file and directory enumeration.
- Analyze post-exploitation discovery commands.
- Detect discovery activities within Splunk.
- Perform threat intelligence enrichment using OSINT.
- Correlate attacker behavior with MITRE ATT&CK techniques.

---

# Business Scenario

After successfully establishing persistence and evading endpoint defenses, the attacker began surveying the compromised Linux server to understand its environment and locate valuable information.

The attacker enumerated system configuration, users, network interfaces, directories, and sensitive files before archiving collected data for possible exfiltration. Simultaneously, the SOC enriched indicators of compromise using VirusTotal and AbuseIPDB to determine the reputation and infrastructure associated with the phishing campaign.

---

# Tools Used

- Kali Linux
- Linux Command Line
- Splunk Enterprise
- VirusTotal
- AbuseIPDB
- WHOIS
- MITRE ATT&CK Framework

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|------|
| Discovery | File and Directory Discovery | T1083 |
| Discovery | System Information Discovery | T1082 |
| Discovery | System Owner/User Discovery | T1033 |
| Discovery | Network Service Discovery | T1046 |
| Discovery | System Network Configuration Discovery | T1016 |
| Collection | Data from Local System | T1005 |
| Collection | Archive Collected Data | T1560 |
| Reconnaissance | Gather Victim Network Information | T1590 |

---

# Investigation Workflow

1. Collect sensitive files from the compromised system.
2. Archive collected data.
3. Enumerate sensitive directories and files.
4. Investigate system configuration and users.
5. Analyze network configuration and active connections.
6. Correlate discovery commands using Splunk.
7. Enrich indicators with external threat intelligence.

---

# Evidence

## Data Collection

The attacker collected valuable files from the compromised host and archived the information for later retrieval.

### Evidence

**24_Sensitive_Data_Collection_and_Archive_Creation.png**

- Collection and archival of sensitive data discovered during post-exploitation.

---

## File Enumeration

The attacker searched the filesystem to identify sensitive files and directories.

### Evidence

**25_Sensitive_File_Discovery.png**

- Enumeration of files containing potentially valuable information.

**26_File_System_Discovery.png**

- Splunk investigation confirming file system enumeration activity.

---

## Post-Exploitation Enumeration

Following successful compromise, the attacker gathered detailed information about the operating system, users, and network configuration.

### Evidence

**27_ROOT_System_Enumeration.png**

- Enumeration of operating system configuration and privileged account information.

**28_Splunk_Whoami_Command_Execution.png**

- Splunk investigation confirming execution of the `whoami` command.

**29_Splunk_Net_Command_Execution.png**

- Detection of Windows/Linux networking commands executed during discovery.

**30_Splunk_IPConfig_Network_Discovery.png**

- Investigation of network configuration discovery.

**31_Splunk_Network_Connection_Filter_192.168.56.1.png**

- Network connection investigation targeting the lab environment.

**32_Splunk_Network_Connections_EventID3_Table.png**

- Review of Sysmon Event ID 3 network connection telemetry.

**33_Splunk_No_Network_Connection_to_Ubuntu_Target.png**

- Validation showing unsuccessful communication with the Ubuntu target system.

---

## Splunk Detection

SOC analysts correlated discovery commands using Splunk Enterprise to reconstruct attacker activity.

### Evidence

**34_Splunk_DNS_Query_Search_Results.png**

- DNS query investigation results.

**35_Splunk_DNS_Query_Detection.png**

- Detection of DNS lookup activity.

**36_Sysmon_DNS_Query_Event_Details.png**

- Detailed Sysmon Event ID associated with DNS resolution.

**37_Splunk_DNS_Query_Statistics.png**

- Statistical analysis of DNS queries during the incident.

**38_Splunk_DNS_Resolution_Results.png**

- Final DNS resolution results supporting the investigation.

---

## Threat Intelligence

External intelligence platforms were used to validate the reputation of indicators associated with the phishing campaign.

### Evidence

**39_VirusTotal_IP_Reputation_Check.png**

- VirusTotal reputation analysis for the identified IP address.

**40_VirusTotal_IP_Relationship_Analysis.png**

- Infrastructure relationship analysis within VirusTotal.

**41_AbuseIPDB_WHOIS_Infrastructure_Analysis.png**

- WHOIS and infrastructure ownership investigation.

**42_AbuseIPDB_IP_Reputation_Summary.png**

- AbuseIPDB reputation summary.

**43_AbuseIPDB_Historical_Abuse_Reports.png**

- Historical abuse reports associated with the investigated IP.

---

# Findings

The investigation demonstrated that the attacker performed extensive reconnaissance within the compromised environment before attempting data exfiltration.

Evidence confirmed:

- Collection and archival of sensitive information.
- File system and directory enumeration.
- System, user, and network discovery.
- DNS resolution and network investigation.
- External reputation analysis of attack infrastructure.
- Correlation of discovery activities using Splunk.

The combined telemetry provided a comprehensive understanding of the attacker's objectives and the systems affected during the incident.

---

# Detection Summary

| Platform | Result |
|----------|--------|
| Kali Linux | Sensitive data collected |
| Kali Linux | File system enumeration completed |
| Splunk | Discovery commands detected |
| Splunk | DNS investigations completed |
| VirusTotal | IP reputation analyzed |
| AbuseIPDB | Infrastructure reputation verified |

---

# Lessons Learned

Discovery activities often generate a significant number of command-line executions, network queries, and filesystem access events that can provide early indicators of attacker intent. Correlating endpoint telemetry with threat intelligence enables defenders to understand attacker objectives, prioritize incident response actions, and identify additional systems that may be at risk.

Organizations should continuously monitor system enumeration commands, unusual DNS activity, network discovery attempts, and access to sensitive files while enriching indicators through trusted threat intelligence platforms.
