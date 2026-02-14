# Phishing Incident Analysis & SOC Response Lab

## Overview
This project simulates a real-world Security Operations Center (SOC) workflow for investigating a reported phishing email. The investigation includes email analysis, IOC extraction, threat classification, risk assessment, and recommended containment actions.

The goal is to demonstrate practical SOC analyst skills in phishing detection, triage, and incident documentation.

---

## Scenario

A user reports a suspicious email to the security team claiming to be a Microsoft account security alert. The email urges the user to click a link to verify their account.

SOC Task:
- Determine if the email is malicious
- Identify indicators of compromise (IOCs)
- Assess risk to the organization
- Recommend appropriate response actions

Reported email file: scenario/reported-email.txt


---

## Investigation Workflow

### 1. Email Header Analysis
- Reviewed SPF, DKIM, and DMARC results
- Identified originating IP address
- Checked for sender spoofing and Reply-To mismatch

See: [`analysis/content-analysis.md`](analysis/content-analysis.md)


---

### 2. Email Content Analysis
- Identified social engineering tactics (urgency, impersonation)
- Compared displayed vs actual URLs
- Evaluated attachment or embedded links

See: analysis/url-domain-investigation.md


---

## Indicators of Compromise (IOCs)

Extracted artifacts:
- Malicious domain
- Sender email address
- Source IP address
- Phishing URL

Full list: iocs/ioc-list.md


---

## Threat Classification

**Attack Type:** Credential Harvesting  
**Technique:** Brand Impersonation (Microsoft)  
**Delivery Method:** Email phishing with malicious link  

---

## Risk Assessment

| Risk Factor | Severity |
|------------|---------|
| Credential theft potential | High |
| Newly registered domain | High |
| External spoofed sender | Medium |
| User interaction (if clicked) | Critical |

Overall Risk Level: **High**

---

## SOC Triage & Response Actions

Simulated Level 1 SOC response:

- Block malicious domain in email gateway
- Block URL at web proxy/firewall
- Reset affected user credentials
- Review email logs for additional recipients
- Submit domain to blocklist
- Notify users via security awareness alert

Full report: incident-response/soc-triage-report.md


---

## SIEM Detection Simulation

This section demonstrates how the phishing activity could be detected or investigated within a SIEM environment.

Includes:
- Example email security alert
- Proxy/DNS query logs to malicious domain
- Sample investigation queries
- Detection recommendations

See: siem/detection-simulation.md


---

## Tools Used

- TryHackMe (Phishing Module)
- VirusTotal
- URLScan.io
- MXToolbox / Google Header Analyzer
- WHOIS Lookup
- GitHub for documentation

---

## Skills Demonstrated

- Phishing analysis and threat identification
- Email header investigation
- IOC extraction and documentation
- Threat classification and risk assessment
- SOC triage and incident response
- Basic SIEM investigation concepts

---

## Project Outcome

The reported email was confirmed to be a phishing attempt designed to harvest user credentials. Appropriate containment and monitoring actions were documented to reduce organizational risk.

## Repository Structure
```text
phishing-incident-response-lab/
│
├── README.md
│
├── scenario/
│   └── reported-email.txt
│
├── analysis/
│   ├── header-analysis.md
│   ├── content-analysis.md
│   └── url-domain-investigation.md
│
├── iocs/
│   └── ioc-list.md
│
├── incident-response/
│   └── soc-triage-report.md
│
├── siem/
│   └── detection-simulation.md
│
└── screenshots/
