# SOC Triage Report

## Incident Summary

**Incident Type:** Phishing Email  
**Attack Method:** Credential Harvesting  
**Status:** Confirmed Malicious  
**Severity:** High  

A reported email was analyzed and determined to be a phishing attempt designed to collect user credentials through a malicious external website.

---

## Investigation Findings

- Email originated from external sender: khz.port@scp.gov.iq
- Originating IP: 188.127.247.252
- Message impersonated administrative account validation
- Embedded link directed to malicious domain:
  email.procedure[.]best
- VirusTotal detections:
  - Domain: 9/93 vendors flagged
  - URL: 8/98 vendors flagged
- WHOIS analysis indicates recently registered domain with anonymized ownership
- URLScan shows hosting behind Cloudflare (AS13335)

---

## Indicators of Compromise (IOCs)

| Type | Value |
|------|------|
| Sender Email | khz.port@scp.gov.iq |
| Originating IP (Email) | 188.127.247.252 |
| Domain | email.procedure[.]best |
| URL | hxxps://email.procedure[.]best/management.aspx |
| Hosting IP | 172.67.202.104 |
| ASN | AS13335 (Cloudflare) |

---

## Impact Assessment

If a user clicks the link and submits credentials:

- Unauthorized access to email account
- Potential account takeover
- Risk of lateral movement
- Possible Business Email Compromise (BEC)
- Exposure of sensitive communications or data

The targeted account was an administrative mailbox, increasing potential impact.

---

## Recommended Containment Actions

### Email Security

- Block sender domain: scp.gov.iq
- Block malicious domain: procedure.best
- Remove phishing email from all user mailboxes (search and purge)
- Add domain and URL to email gateway block list

---

### Network / Web Security

- Block the domain and URL at the web proxy or firewall
- Monitor DNS and proxy logs for connections to:
  - email.procedure.best

---

### User Protection

- Reset credentials for affected user (if interaction suspected)
- Force password reset and MFA re-authentication
- Notify user of phishing attempt

---

### Threat Hunting

- Search email logs for additional recipients
- Check authentication logs for suspicious activity
- Monitor for abnormal login locations or behavior

---

## Incident Classification

**Category:** Phishing  
**Technique:** Credential Harvesting  
**MITRE ATT&CK:**  
- T1566.002 – Phishing: Link
