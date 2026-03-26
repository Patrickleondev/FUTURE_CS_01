# Methodology: Step-by-Step Vulnerability Assessment

This document outlines the exact methodology and steps taken during the penetration testing and vulnerability assessment of `demo.testfire.net`. The assessment was conducted from a Kali Linux environment.

![1772657214352](image/Step_by_Step_Methodology/1772657214352.jpg)

## Step 1: Target Selection and Initial Reconnaissance

The target selected for this assessment is `demo.testfire.net` (Altoro Mutual), an authorized web application designed for security testing purposes.

![Initial Reconnaissance](Screenshots/Screenshot_2026-03-04_12_43_42.png)

## Step 2: Port Scanning and Service Enumeration (Nmap)

To identify open ports and running services, an aggressive Nmap scan was executed:

```bash
nmap -sV -sC -T4 -O -oA nmap_scan demo.testfire.net
```

**Findings**:

- Port 80 (HTTP) Open: Apache Tomcat/Coyote JSP engine 1.1
- Port 443 (HTTPS) Open: Apache Tomcat/Coyote JSP engine 1.1
- Port 8080 (HTTP) Open: Proxy

![Nmap Scan](Screenshots/Screenshot_2026-03-04_12_47_14.png)

## Step 3: Web Technology Fingerprinting (WhatWeb)

To gather information about the underlying technology stack, WhatWeb was utilized:

```bash
whatweb -v http://demo.testfire.net | tee whatweb_results.txt
```

**Findings**: Confirmed the presence of Apache-Coyote/1.1 and identified cookie attributes (HttpOnly flag on JSESSIONID).

![WhatWeb Scan](Screenshots/Screenshot_2026-03-04_12_47_21.png)

## Step 4: Vulnerability Scanning (Nikto)

A Nikto scan was performed to detect common server misconfigurations and missing security headers:

```bash
nikto -h http://demo.testfire.net -o nikto_results.txt
```

**Findings**: Identified missing `X-Frame-Options` and `X-Content-Type-Options` headers, as well as insecure HTTP methods (`PUT`, `DELETE`).

![Nikto Scan](Screenshots/Screenshot_2026-03-04_15_30_03.png)

## Step 5: Web Application Vulnerability Scanning (OWASP ZAP)

A passive and active automated scan was conducted using OWASP ZAP to identify application-level vulnerabilities.
The site was spidered and passively analyzed.

![OWASP ZAP Interface 1](Screenshots/Screenshot_2026-03-04_15_30_25.png)

The ZAP alert tab highlighted multiple Medium and Low severity vulnerabilities, including missing Anti-CSRF tokens and missing Content Security Policy headers.

![OWASP ZAP Interface 2](Screenshots/Screenshot_2026-03-04_15_30_30.png)


## Conclusion

The combination of Nmap, WhatWeb, Nikto, and OWASP ZAP provided a comprehensive overview of the security posture of the target application. All findings have been consolidated into the final `Vulnerability_Assessment_Report.md`.
