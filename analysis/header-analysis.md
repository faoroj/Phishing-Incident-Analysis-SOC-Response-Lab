# Email Header Analysis

The email headers were analyzed using PhishTool to evaluate sender authenticity and identify the origin of the message.

---

## Sender Information

| Field | Value |
|------|------|
| Display Name | SupportDesk |
| From Address | khz.port@scp.gov.iq |
| Recipient | admin@malware-traffic-analysis.net |
| Message ID Domain | scp.gov.iq |

---

## Infrastructure Details

- Originating IP: 188.127.247.252  
- Reverse DNS: s468451.srvape.com  
- Email originated from external infrastructure unrelated to the recipient domain

---

## Authentication Observations

- Sender domain does not match the targeted organization
- No legitimate relationship between sender domain and recipient environment
- Message originated from a third-party hosting provider rather than enterprise mail infrastructure

---

## Header-Based Indicators

- External sender targeting administrative account
- Display name impersonation ("SupportDesk")
- Mismatch between sender domain and target organization
- Non-enterprise sending infrastructure

---

## Conclusion

Header analysis indicates the message originated from external, untrusted infrastructure and was likely spoofed or sent from attacker-controlled systems.
