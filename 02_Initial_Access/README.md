# Initial Access

## Overview

Initial Access is the stage where an attacker successfully gains an entry point into the target environment. In this simulated enterprise phishing incident, the attack began with a phishing email impersonating Microsoft Security requesting urgent account verification.

The phishing email contained a malicious hyperlink (`example.com`) designed to deceive the victim into interacting with attacker-controlled infrastructure. Following the initial compromise, the attacker performed credential attacks against the target system, resulting in successful SSH authentication.

This phase combines email forensics, credential compromise evidence, and endpoint telemetry to reconstruct how the attacker obtained initial access.

---

# Objectives

- Analyze the phishing email.
- Validate email authenticity.
- Examine email headers and metadata.
- Verify SPF, DKIM and DMARC records.
- Investigate the malicious URL.
- Confirm credential compromise.
- Correlate endpoint telemetry using Sysmon and Splunk.

---

# Business Scenario

An employee within the Admissions Department of NAD Cybersecurity Institute received an email claiming to originate from Microsoft Security.

The email instructed the recipient to immediately verify their account by clicking a malicious hyperlink. After interacting with the phishing campaign, attacker activity was observed across multiple monitoring platforms.

The SOC investigation focused on determining how initial access was achieved and validating the compromise using multiple evidence sources.

---

# Tools Used

- Microsoft Outlook
- Google Admin Toolbox
- MXToolbox
- PhishTool
- Hydra
- Kali Linux
- Splunk Enterprise
- Sysmon

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|------|
| Initial Access | Phishing: Spearphishing Link | T1566.002 |
| Credential Access | Brute Force | T1110 |
| Initial Access | External Remote Services (SSH) | T1133 |

---

# Investigation Workflow

1. Analyze the phishing email.
2. Validate sender authentication.
3. Inspect email headers.
4. Review email metadata.
5. Analyze the malicious hyperlink.
6. Validate SPF, DKIM and DMARC.
7. Review PhishTool forensic analysis.
8. Confirm successful credential discovery.
9. Correlate endpoint activity using Splunk and Sysmon.

---

# Evidence

## Email Analysis

The phishing email was analyzed to determine its legitimacy,
identify indicators of compromise (IOCs), and understand the
initial attack vector used against the organization.

### Initial Phishing Email

![Initial Phishing Email](01_Phishing_Email_Microsoft_Security_Alert.png)

The phishing email impersonated Microsoft Security and attempted
to trick the recipient into clicking a malicious hyperlink.

---

### Email Header Authentication Analysis

![Email Header Authentication Analysis](02_Email_Header_Authentication_Analysis.png)

Authentication results were reviewed to verify the legitimacy
of the sender and identify potential email spoofing attempts.

---

### PhishTool Email Forensic Analysis

![PhishTool Email Forensic Analysis](03_PhishTool_Email_Forensic_Analysis.png)

PhishTool was used to perform automated forensic analysis of
the email, extracting indicators and identifying suspicious
characteristics.

---

### DMARC Record Validation

![DMARC Record Validation](04_DMARC_Record_Validation.png)

The sender's DMARC policy was examined to determine whether
the message complied with domain authentication policies.

---

### SPF and DKIM Verification

![SPF and DKIM Verification](05_SPF_DKIM_Record_Verification.png)

SPF and DKIM records were validated to confirm whether the
email passed authentication checks or exhibited signs of
spoofing.

---

### Email Header Forensic Analysis

![Email Header Forensic Analysis](06_Email_Header_Forensic_Analysis.png)

A detailed inspection of the email headers provided insight
into message routing, originating servers, and authentication
results.

---

### Phishing Link Destination Analysis

![Phishing Link Destination Analysis](07_Phishing_Link_Destination_Analysis.png)

The embedded hyperlink was analyzed to identify the destination
and determine whether it redirected users to attacker-controlled
infrastructure.

---

### Email Header Metadata Analysis

![Email Header Metadata Analysis](08_Email_Header_Metadata_Analysis.png)

Message metadata, routing information, timestamps, and other
email attributes were reviewed to support the forensic
investigation.

---

# Kali Attack Evidence

Following reconnaissance, the attacker attempted credential
attacks against the exposed SSH service.

### Hydra SSH Credentials Discovery

![Hydra SSH Credentials Discovery](09_Hydra_SSH_Credentials_Discovered.png)

Hydra successfully identified valid SSH credentials, providing
the attacker with initial access to the target system.

---

# Splunk Detection

Sysmon telemetry was ingested into Splunk Enterprise to verify
attacker activity and correlate endpoint events with the
incident timeline.

### Sysmon Network Connection Event

![Sysmon Network Connection Event](10_Sysmon_Network_Connection_Event.png)

Sysmon Event ID 3 captured network connection activity
associated with the attack, providing visibility into
communications initiated by the compromised host.

---

### Process Correlation Using ProcessGUID

![Process Correlation Using ProcessGUID](11_Process_Correlation_ProcessGUID.png)

Splunk was used to correlate Sysmon events through the
ProcessGUID, allowing investigators to trace attacker actions
across multiple process and network events.
- Process correlation using ProcessGUID to associate network activity with the originating process.

---

# Findings

The investigation confirmed that the attacker successfully gained initial access through a phishing campaign followed by credential compromise.

Evidence confirmed:

- Successful phishing delivery.
- Email impersonation.
- Authentication record validation.
- Malicious hyperlink analysis.
- Successful SSH credential discovery using Hydra.
- Endpoint telemetry captured by Sysmon.
- Event correlation performed within Splunk Enterprise.

---

# Detection Summary

| Platform | Result |
|----------|--------|
| Email Analysis | Phishing confirmed |
| PhishTool | Email classified as malicious |
| SPF/DKIM/DMARC | Authentication records reviewed |
| Hydra | Valid SSH credentials discovered |
| Sysmon | Network connection recorded (Event ID 3) |
| Splunk Enterprise | Process correlation completed |

---

# Lessons Learned

Phishing continues to be one of the most effective initial access techniques used by threat actors.

Combining email forensics with endpoint telemetry enables SOC analysts to rapidly validate suspicious emails, identify compromised credentials, and reconstruct the attack path. Correlating Sysmon network events with Splunk process telemetry significantly improves visibility into attacker activity and provides high-confidence evidence for incident response investigations.
