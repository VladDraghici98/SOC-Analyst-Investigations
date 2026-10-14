# SOC-Analyst-Investigations

Executive Summary
A high-severity security alert was triggered in the SIEM indicating a targeted spear-phishing campaign associated with the Lazarus Group (APT38). The attacker sent a malicious hiring assessment lure to an internal employee (Ellen), who subsequently accessed the embedded URL and executed the downloaded payload.

Incident Metadata
Alert Name: SOC337 - Lazarus Phishing Campaign Detected (APT38)
Event ID: 315
Event Time: 2025-03-06 T 07:15:00+03:00
Closed Time: 2026-10-14 T 09:11:40+00:00
Severity: High
Difficulty: Medium
Alert Type: APT Group / Spear-Phishing
Device Action: Allowed
Delivery Status: Delivered
Result: True Positive
Playbook Score: 100% Success Rate (25/25)
SMTP Source IP: 152.89.61.96
Source Address: trevorgreer9312@gmail.com
Destination Address: Ellen@letsdefend.io
Email Subject: Invitation: Coinbase Crypto Trader Hiring Assessment

Indicators of Compromise (IoCs)

Malicious URL: https://blockchainjobhub[.]com/invite/E3fM8yF7

Sender IP: 152.89.61.96

Sender Email: trevorgreer9312@gmail.com

MITRE ATT&CK Mapping

T1566 - Phishing (Initial Access)

T1598.002 - Spearphishing Link / Attachment

T1059 / T1059.001 - Command and Scripting Interpreter: PowerShell

T1204.001 - User Interaction: Malicious Link

T1105 - Ingress Tool Transfer

Investigation Findings & Playbook Workflow

Email Analysis & Header Parsing
Examined the email in the Email Security tab. The sender identity matched between the Return-Path and From fields, confirming that header spoofing was not utilized; instead, an attacker-controlled external mailbox (trevorgreer9312@gmail.com) was used directly.
The email contained a embedded hyperlinked URL (https://blockchainjobhub[.]com/invite/E3fM8yF7) masquerading as a cryptocurrency recruitment assessment.

Threat Intelligence & URL Analysis
Analyzed the extracted URL using Threat Intelligence tools such as VirusTotal and Any.run. The domain and associated payload were confirmed to be malicious, linked to Lazarus Group infrastructure.

Log Management & Execution Check
Cross-referenced network and proxy logs in the Log Management tab. Confirmed that the recipient host (Ellen's workstation) clicked the phishing link, navigated to the malicious domain, downloaded the payload file, and executed it.

Containment & Response Actions

Identified the alert as a True Positive security incident.

Initiated immediate device containment/isolation for Ellen's endpoint to prevent lateral movement and C2 communications.

Purged and deleted the malicious email from the recipient mailbox and blocked the sender address at the email gateway.

Blocked the malicious domain (blockchainjobhub[.]com) and IP (152.89.61.96) at the perimeter firewall/proxy.
