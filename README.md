# FUTURE_CS_01: Vulnerability Assessment Report for a Live Website

## 🔍 Task Overview

This repository contains the deliverables for **Task 1: Vulnerability Assessment Report for a Live Website**, part of the Future Interns Cyber Security track.

The objective was to perform a read-only, non-intrusive security analysis of a public, authorized test website, classify the identified risks, and document the findings in a professional, business-friendly report.

**Target Selected:** `demo.testfire.net` (Altoro Mutual - IBM's legally authorized test domain)

## 🛠️ Tools Used

- **Nmap**: For port scanning and service detection.
- **Nikto**: For web server vulnerability scanning and identifying missing security configurations.
- **WhatWeb**: For technology stack fingerprinting and header analysis.
- **OWASP ZAP**: For passive web application vulnerability assessment.
- **Kali Linux**: The primary operating system used to conduct the scans.

## 📄 Deliverables

- [**Vulnerability Assessment Report**](Vulnerability_Assessment_Report.md): The detailed report covering the identified vulnerabilities, their business context, risk levels, and remediation steps.
- **Scan Evidence Data**: Raw outputs from `nmap`, `nikto`, `whatweb`, and `ZAP` stored locally in the analysis environment.
