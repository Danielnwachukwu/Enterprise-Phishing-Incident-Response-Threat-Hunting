# Defense Evasion

## Overview

Defense Evasion encompasses techniques used by attackers to bypass security controls, conceal malicious activity, and reduce the likelihood of detection during an intrusion.

In this simulated incident involving the NAD Cybersecurity Institute, the attacker employed several defense evasion techniques, including the use of Living Off the Land Binaries (LOLBins), obfuscated PowerShell commands, and Windows Defender tampering. These activities were investigated through Splunk telemetry to identify suspicious command execution and attempts to weaken endpoint defenses.

---

# Objectives

- Investigate the use of trusted Windows binaries for malicious purposes.
- Detect obfuscated PowerShell command execution.
- Identify attempts to tamper with Windows Defender.
- Correlate defense evasion activity using Splunk.
- Map attacker behavior to the MITRE ATT&CK framework.

---

# Business Scenario

After successfully establishing persistence on the compromised environment, the attacker attempted to evade detection before continuing post-exploitation activities.

Instead of introducing additional malware, the attacker leveraged legitimate Windows binaries (LOLBins) to execute commands that blended into normal system activity. PowerShell commands were encoded to conceal their true purpose, while Windows Defender settings were targeted to reduce the effectiveness of endpoint protection.

The SOC investigated these actions to determine whether the attacker was actively attempting to bypass defensive controls.

---

# Tools Used

- Windows PowerShell
- Windows Defender
- Splunk Enterprise
- MITRE ATT&CK Framework

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|------|
| Defense Evasion | Living Off the Land Binaries (LOLBins) | T1218 |
| Defense Evasion | Obfuscated Files or Information | T1027 |
| Defense Evasion | PowerShell | T1059.001 |
| Defense Evasion | Impair Defenses | T1562.001 |

---

# Investigation Workflow

1. Investigate LOLBins command execution.
2. Analyze encoded PowerShell activity.
3. Investigate Windows Defender tampering attempts.
4. Correlate suspicious process execution in Splunk.
5. Assess the impact on endpoint security.

---

# Evidence

## Living Off the Land Binaries (LOLBins)

The attacker abused legitimate Windows binaries to execute commands while blending into normal operating system activity.

### Evidence

**21_LOLBins_Command_Investigation.png**

- Splunk investigation identifying suspicious execution of trusted Windows binaries associated with attacker activity.

---

## PowerShell Obfuscation

To conceal malicious intent, PowerShell commands were executed in an encoded format.

### Evidence

**22_Encoded_PowerShell_Command_Investigation.png**

- Splunk investigation highlighting encoded PowerShell command execution consistent with obfuscation techniques.

---

## Security Tool Evasion

The attacker attempted to weaken endpoint defenses by interacting with Windows Defender.

### Evidence

**23_Windows_Defender_Tampering_Investigation.png**

- Splunk investigation showing activity associated with Windows Defender tampering and potential security control impairment.

---

# Findings

The investigation confirmed multiple defense evasion techniques designed to reduce visibility and delay detection.

Evidence demonstrated:

- Abuse of legitimate Windows binaries (LOLBins).
- Execution of encoded PowerShell commands.
- Attempts to interfere with Windows Defender protections.
- Correlated process execution events captured by Splunk.

These techniques significantly increased the attacker's ability to operate without triggering traditional security controls.

---

# Detection Summary

| Platform | Result |
|----------|--------|
| Splunk | LOLBins command execution investigated |
| Splunk | Encoded PowerShell activity detected |
| Splunk | Windows Defender tampering investigated |

---

# Lessons Learned

Attackers increasingly rely on legitimate administrative tools instead of deploying custom malware. Monitoring command-line execution, encoded PowerShell activity, and changes to endpoint security configurations provides valuable visibility into defense evasion attempts.

Organizations should enable detailed PowerShell logging, monitor Windows Defender configuration changes, and establish detection rules for abnormal use of LOLBins to reduce attacker dwell time.
