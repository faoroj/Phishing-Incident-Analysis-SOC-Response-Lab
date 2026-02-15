# Phishing Incident Analysis & SOC Response Lab

## Overview
This project simulates a real-world Security Operations Center (SOC) workflow for investigating a reported phishing email. The investigation includes email analysis, IOC extraction, threat classification, risk assessment, and recommended containment actions.

The goal is to demonstrate practical SOC analyst skills in phishing detection, triage, and incident documentation.

---

## Scenario

Date: 2-14-2026

A user reported a suspicious email requesting account validation for the address **admin@malware-traffic-analysis.net**. The message instructed the recipient to click a link and re-authenticate their account by entering their email credentials.

Initial review indicated the message originated from an external sender and contained a suspicious embedded URL.

SOC Task:
- Determine whether the email is malicious
- Identify indicators of compromise (IOCs)
- Assess potential organizational risk
- Recommend containment and remediation actions

Reported email file: [`scenario/2024-08-29-phishing-email-0415-UTC.eml`](scenario/2024-08-29-phishing-email-0415-UTC.eml)


---

## Investigation Workflow

### 1. Email Header Analysis
- Reviewed SPF, DKIM, and DMARC results
- Identified originating IP address
- Checked for sender spoofing and Reply-To mismatch

See: [`analysis/content-analysis.md`](analysis/content-analysis.md)


---

### 2. PhishTool Analysis

The reported email was uploaded to PhishTool for automated analysis and threat intelligence enrichment.

PhishTool capabilities used:
- Email parsing and header analysis
- IOC extraction (domains, IPs, URLs)
- Threat classification
- Reputation checks

See: [`phishtool/phishtool-analysis.md`](phishtool/phishtool-analysis.md)

---

### 3. Email Content Analysis
- Identified social engineering tactics (urgency, impersonation)
- Compared displayed vs actual URLs
- Evaluated attachment or embedded links

See: [`analysis/url-domain-investigation.md`](analysis/url-domain-investigation.md)


---

## Indicators of Compromise (IOCs)

Extracted artifacts:
- Malicious domain
- Sender email address
- Source IP address
- Phishing URL

Full list: [`iocs/ioc-list.md`](iocs/ioc-list.md)


---

## Threat Classification

**Attack Type:** Credential Harvesting  
**Technique:** Account Validation / Re-authentication Phishing  
**Impersonation Method:** Generic administrative account validation theme  
**Delivery Method:** Phishing email containing a malicious external link  

The email attempts to trick the recipient into submitting email credentials via a fraudulent web page hosted on attacker-controlled infrastructure.

---

## Risk Assessment

| Risk Factor | Severity |
|------------|---------|
| Credential theft potential | High |
| Malicious external domain detected (7/98 VirusTotal) | High |
| External, untrusted sending infrastructure | Medium |
| Targeted administrative account | High |
| User interaction (if link clicked) | Critical |

**Overall Risk Level: High**

### Risk Summary

If a user submits credentials to the phishing site, attackers could gain unauthorized access to organizational email accounts. Compromise of an administrative account would significantly increase the risk of lateral movement, data exposure, or business email compromise (BEC).

---

## SOC Triage & Response Actions

Simulated Level 1 SOC response:

- Block malicious domains in the email gateway
- Block URL at web proxy/firewall
- Reset affected user credentials
- Review email logs for additional recipients
- Submit the domain to the blocklist
- Notify users via security awareness alert

Full report: [`incident-response/soc-triage-report.md`](incident-response/soc-triage-report.md)


---

## SIEM Detection Simulation

This section demonstrates how the phishing activity could be detected or investigated within a SIEM environment.

Includes:
- Example email security alert
- Proxy/DNS query logs to a malicious domain
- Sample investigation queries
- Detection recommendations

See: [`siem/detection-simulation.md`](siem/detection-simulation.md)


---

## Tools Used

- TryHackMe (Phishing Module)
- VirusTotal
- Phishtool
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
├── phishtool/
│   └── phishtool-analysis.md
│
└── screenshots/
