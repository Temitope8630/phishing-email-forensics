# Phishing Email Forensics – Email Header & Domain Analysis Toolkit

## Project Overview
This project focuses on performing forensic analysis on suspicious phishing emails using email header inspection, sender infrastructure validation, domain reputation analysis, and IOC extraction techniques.

The investigation was conducted on a suspicious email reported through a ServiceNow incident ticket and preserved as an `.eml` evidence file. The analysis involved validating embedded URLs, reviewing sender IP reputation, checking SPF/DKIM/DMARC authentication records, and identifying spoofing indicators through header inconsistencies.

The project demonstrates practical phishing investigation workflows used by SOC analysts, threat hunters, and incident responders.

---

# Objectives
- Analyze suspicious email headers
- Detect spoofed or impersonated sender domains
- Investigate phishing URLs and attachments
- Validate SPF, DKIM, and DMARC authentication
- Perform sender IP reputation analysis
- Extract and document Indicators of Compromise (IOCs)
- Produce a structured phishing investigation report

---

# Investigation Focus Areas

## Email Header Analysis
The email headers were reviewed to identify suspicious routing patterns, spoofing attempts, and authentication inconsistencies.

### Analysis Performed
- Received path inspection
- From vs Return-Path comparison
- SPF validation
- DKIM verification
- DMARC alignment review
- Message-ID inspection
- Routing server analysis

### Findings
| Control | Result |
|---|---|
| SPF | Pass |
| DKIM | Pass |
| DMARC | Pass |
| From vs Return-Path | Mismatch |
| Suspicion Level | High |

### Key Observation
Although SPF, DKIM, and DMARC passed successfully, the mismatch between the visible sender address and the Return-Path raised phishing suspicion and suggested possible relay abuse or impersonation infrastructure.

---

## Embedded URL Investigation
Suspicious URLs embedded inside the email were analyzed using threat intelligence and behavioral analysis platforms.

### Analysis Platforms
- VirusTotal
- URLScan.io

### Findings
- Redirect behavior observed
- Suspicious tracking infrastructure identified
- Potential phishing redirection chain detected
- VirusTotal detection ratio: `1/93`
- Analyst assessment: **Malicious**

### Sample Investigated URL
```text
https://75cf03ff33327619f546ee0199768471.eu-west-1.resend-clicks-a.com/
```

---

## Attachment Analysis
The email contained a suspicious `.htm` attachment impersonating a job notification email.

### Attachment Reviewed
```text
15 new jobs matching your preferences - Gmail.htm
```

### Hashes Extracted
| Hash Type | Value |
|---|---|
| MD5 | d14439c530c2db83c2c1f97ef012892e |
| SHA1 | 34b9ce6e0532e21df5d7dd1f858ef3bf216cf868 |
| SHA256 | 3db588bf58ed9e8e614d68440cc1282227d9444fad9f2bc4e2a0366443c7b8e3 |

---

## Sender IP Reputation Analysis
The originating sender IP address was investigated using AbuseIPDB.

### Findings
| Indicator | Result |
|---|---|
| Sender IP | 198.244.57.133 |
| Abuse Confidence Score | 0% |
| Report Count | 3 Reports |
| ASN | AS396479 |
| Provider | Mailgun Technologies Inc |

### Analyst Observation
The IP reputation alone did not conclusively confirm malicious activity, but combined with the phishing indicators and header inconsistencies, it contributed to the overall suspicion level.

---

# Tools Used

| Tool | Purpose |
|---|---|
| VirusTotal | URL & file reputation analysis |
| URLScan.io | URL behavior inspection |
| AbuseIPDB | IP reputation investigation |
| MXToolbox | Email header analysis |
| WHOIS | Domain investigation |
| ServiceNow | Incident management |
| Kali Linux | Investigation environment |

---

# Investigation Workflow

```text
Suspicious Email Collection
            ↓
Header Extraction & Review
            ↓
SPF/DKIM/DMARC Validation
            ↓
Embedded URL Investigation
            ↓
Attachment Hash Analysis
            ↓
Sender IP Reputation Check
            ↓
IOC Extraction
            ↓
Final Analyst Assessment
```

---

# Indicators of Compromise (IOCs)

| IOC Type | Value |
|---|---|
| Sender Email | noreply@candidates.workablemail.com |
| Sender IP | 198.244.57.133 |
| Suspicious URL | resend-clicks-a.com |
| Attachment Type | .HTM phishing attachment |
| Return-Path | workablemail.com |
| Detection Status | Suspicious / Phishy |

---

# Key Findings
- Identified phishing-related URL redirection infrastructure
- Detected mismatch between From address and Return-Path
- Extracted malicious attachment hashes
- Validated authentication controls
- Correlated indicators with external threat intelligence platforms
- Documented phishing evidence for incident response handling

---

# Skills Demonstrated
- Phishing Email Investigation
- Email Header Analysis
- Threat Intelligence Correlation
- IOC Extraction
- Incident Response
- Domain Reputation Analysis
- Security Operations Center (SOC) Workflow
- Cyber Threat Hunting

---

# Ethical & Legal Notice
This project was conducted strictly for educational, defensive, and authorized cybersecurity investigation purposes only.

Do not use these techniques for unauthorized phishing, impersonation, or malicious activity.

---

# References
- RFC 5322 Email Header Standard
- VirusTotal
- URLScan.io
- AbuseIPDB
- MXToolbox
- MITRE ATT&CK Framework

---

# Author
## Adabanija Toheeb Tope

Cybersecurity Analyst | SOC Enthusiast | Threat Hunter

---
````
