# Application-Security-Project
Automated security assessment of VulnWeb targets using OWASP ZAP
# Automated Assessment of VulnWeb Targets

**Course Project — Application Security (L&T EduTech)**


## Overview
This project is a security assessment conducted as part of the **Application Security course at L&T EduTech**. The goal was to identify and document common web application vulnerabilities using automated and manual testing techniques.

## Scope
Four VulnWeb test applications were assessed:
- `testphp.vulnweb.com`
- `testasp.vulnweb.com`
- `testaspnet.vulnweb.com`
- `rest.vulnweb.com`

## Tools & Methodology
- **OWASP ZAP (v2.16.1)** — Active Scan across all four targets
- Manual verification of scanner findings
- Alerts documented across High, Medium, Low, and Informational risk levels

## Key Findings

| Vulnerability | Affected Host(s) | Severity |
|---|---|---|
| SQL Injection (SQLi) | testasp, testphp | High |
| Insecure File Upload | testphp | High |
| Vulnerable JS Library (Handlebars.js) | rest.vulnweb.com | High |
| Reflected XSS | testaspnet | Medium |
| Absence of Anti-CSRF Tokens | testasp, testaspnet | Medium |
| Missing Anti-Clickjacking Header | All sites | Medium |

A total of **21 unique security alerts** were identified. Confirmed critical flaws include SQL Injection, Insecure File Upload (leading to potential Remote Code Execution), and Reflected XSS.

## Mitigation Highlights
- Patch/remove vulnerable JS libraries (or apply WAF virtual patching)
- Implement `X-Frame-Options` / CSP `frame-ancestors` to prevent clickjacking
- Deploy a strict Content-Security-Policy header
- Add Anti-CSRF (Synchronizer) tokens on all state-changing requests
- Suppress version-revealing headers (`Server`, `X-Powered-By`, `X-AspNet-Version`)
- Set `HttpOnly` and `SameSite` cookie flags
- Add `X-Content-Type-Options: nosniff`

## Full Report
See [`l_t-project_report.pdf`](./l_t-project_report.pdf) in this repo for the complete write-up, ZAP scan details, and references.
