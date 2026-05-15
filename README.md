# Splunk Threat Investigation Lab

**Platform:** TryHackMe — Investigating with Splunk  
**Tool:** Splunk SIEM  
**MITRE ATT&CK:** T1059.001 — PowerShell Command and Scripting Interpreter

---

## Project Documentation

[Click here to view full project report](Splunk-Threat-Investigation.pdf)

---

## Scenario

A Windows endpoint showed signs of malicious PowerShell execution. The goal was to identify the attacker's actions using Splunk and document findings in a structured incident report.

---

## What I Did

- Ingested and analyzed Windows Event Logs in Splunk
- Queried EventID 800, 4624, 4688 to trace malicious activity
- Identified encoded PowerShell execution on host James.browne
- Detected suspicious user: Cybertees\James
- Recognized command obfuscation techniques
- Mapped attack to MITRE ATT&CK T1059.001
- Documented full incident report with severity, evidence, and remediation

---

## Key Splunk Queries Used

index=main EventID=4688
| table _time, host, user, CommandLine

index=main EventID=800
| search CommandLine="*encodedcommand*"
| table _time, host, user, CommandLine

---

## Findings

| Field | Value |
|-------|-------|
| Affected Host | James.browne |
| Suspicious User | Cybertees\James |
| Attack Technique | Encoded PowerShell Execution |
| MITRE Technique | T1059.001 |
| Severity | High |

---

## Tools

Splunk SIEM | Windows Event Logs | MITRE ATT&CK | TryHackMe
