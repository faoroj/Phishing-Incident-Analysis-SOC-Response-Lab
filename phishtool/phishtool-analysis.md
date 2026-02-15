# PhishTool Analysis

The reported email was uploaded to PhishTool for automated parsing, indicator extraction, and threat intelligence enrichment.

---

## Analysis Summary

- Classification: Malicious
- Threat Type: Credential Harvesting
- Technique: Account validation / re-authentication lure
- Delivery Method: Phishing email with an embedded malicious link

The email attempts to trick the recipient into clicking a link and submitting account credentials.

---

## Extracted Indicators

| Type | Value |
|------|------|
| Sender | khz.port@scp.gov.iq |
| Display Name | SupportDesk |
| Recipient | admin@malware-traffic-analysis.net |
| Malicious Domain | email.procedure[.]best |
| Phishing URL | hxxps://email.procedure[.]best/management.aspx |
| Originating IP | 188.127.247.252 |
| Reverse DNS | s468451.srvape.com |

---

## Header Findings

- Sender domain does not match the impersonated organization
- Email originated from external infrastructure
- Originating IP resolves to unrelated hosting provider
- Message-ID domain does not align with legitimate enterprise mail services
- Indicators consistent with spoofed or malicious email delivery

---

## Reputation Insights

- PhishTool identified the embedded URL as suspicious
- VirusTotal detection: **7 / 98 vendors flagged**
- Domain is not associated with the impersonated organization
- Infrastructure appears to be hosted on non-enterprise shared hosting
- Indicators consistent with phishing infrastructure used for credential harvesting

---

## Social Engineering Indicators

- Urgent account validation request
- Use of administrative target (“Hello admin”)
- Call-to-action button: **“Re-authenticate Now”**
- Requests email password submission
- Generic formatting with impersonation of the internal validation process

---

## Screenshots

### 1. Rendered Email Content
`screenshots/phishtool-rendered-email.png`

Shows the phishing email as delivered to the user, including the social engineering message and the **“Re-authenticate Now”** credential harvesting link.

---

### 2. Header & Sender Details
`screenshots/phishtool-header-details.png`

Displays sender information, recipient, timestamp, and the **originating IP address (188.127.247.252)** along with reverse DNS, confirming external and suspicious sending infrastructure.

---

### 3. URL Analysis
![URL Analysis](screenshots/phishtool-url-analysis.png)


Shows extracted URLs from the email, including the malicious domain **email.procedure[.]best** and VirusTotal detection results (7/98).

---

### 4. Authentication Results
`screenshots/phishtool-authentication.png`

Displays SPF, DKIM, and DMARC results, supporting analysis of email authenticity and potential spoofing indicators.

---

## Conclusion

PhishTool analysis confirms the email is a **credential harvesting phishing attempt** delivered from external infrastructure using social engineering techniques and malicious web infrastructure.
