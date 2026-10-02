# Week-4-Penetration-Testing
## 📌 Overview

This repository contains my Week 4 cybersecurity lab work on
Penetration Testing as part of the Networkwalks Cybersecurity Internship.

The assessment focuses on understanding the penetration testing
methodology, reconnaissance, scanning, enumeration, vulnerability
identification, and security documentation.

---
## 🎯 Objectives

- Understand the penetration testing methodology
- Perform reconnaissance and information gathering
- Identify open ports and running services
- Enumerate discovered services
- Identify potential security weaknesses
- Validate findings in an authorized testing environment
- Document security findings and evidence
- Recommend appropriate remediation measures

---
## 🎯 Target

**Target Website:** `http://medirozahospital.com`

**Target Type:** Web Application

> ⚠️ Testing was performed only within the scope and authorization
> provided for the cybersecurity lab.

---
## 🛠️ Tools Used

- Kali Linux
- Nmap
- WhatWeb
- Gobuster
- Nikto
- Burp Suite
- Metasploit Framework
- sql injection
- Other tools used during the lab

---
## 🚨 Finding 01 – SQL Injection in Login Authentication

### Description

The application's login functionality was found to be susceptible to
SQL Injection. User-controlled input appears to be incorporated into
a backend SQL query without adequate parameterization or input handling.

During authorized testing, a SQL injection payload demonstrated that
the authentication mechanism could potentially be bypassed.

### Vulnerability Type

- **OWASP Category:** A03 – Injection
- **Vulnerability:** SQL Injection (SQLi)
- **Affected Component:** Admin Login
- **Severity:** High
- **Status:** Confirmed

### Evidence

The vulnerability was identified during authorized testing of the
administrator login functionality.
<img width="1917" height="962" alt="Screenshot 2026-10-03 005815" src="https://github.com/user-attachments/assets/7c2fdab4-105b-41f8-92ad-a40ceb7aa845" />
**Test input:**

`admin'--`


<img width="1901" height="970" alt="image" src="https://github.com/user-attachments/assets/cdf5c073-f5ee-4309-be06-04ed80c8c11f" />
The application accepted the manipulated input in a manner that
indicated the login query may be vulnerable to SQL injection.

> Do not include real administrator credentials or sensitive
> application data in this repository.





<img width="1912" height="921" alt="image" src="https://github.com/user-attachments/assets/e46b003f-c668-4933-89f2-3d488a28f0ef" />
### Security Impact

A successful SQL Injection vulnerability in an administrative
authentication mechanism could allow an attacker to bypass
authentication and potentially gain unauthorized administrative access.

Depending on the application's database privileges and configuration,
SQL injection may also expose or modify database information.

### Root Cause

The likely root cause is unsafe construction of SQL queries using
user-supplied input without proper parameterized queries/prepared
statements.
## 🔐 Finding 02 – Weak Password Protection on PDF Documents

### Description

After accessing the authorized administrative area, three password-protected
PDF documents were identified.

The PDFs were protected using passwords that were susceptible to
offline password-cracking techniques. John the Ripper was used in the
authorized lab environment to demonstrate the weakness.
### Vulnerability Type

- **Category:** Weak Password / Insufficient Cryptographic Protection
- **Affected Component:** Password-protected PDF documents
- **Tool Used:** John the Ripper
- **Severity:** High
- **Status:** Confirmed

### Attack Method

1. Identified the password-protected PDF files.
2. Extracted the PDF password hash using an appropriate PDF hash-extraction
   utility.
3. Prepared the extracted hash for John the Ripper.
4. Performed an authorized offline password-cracking test.
5. Verified the recovered password against the PDF.

### Evidence
## Evidence

### PDF 1

<img width="982" height="847" alt="PDF 1 evidence" src="https://github.com/user-attachments/assets/79bfd9cb-5ade-45eb-b941-25bdec3ed52b" />

**Password:** `[123456]`
### PDF  2
<img width="977" height="837" alt="image" src="https://github.com/user-attachments/assets/7e9d8a6c-d905-40a5-81fd-7d66eb056171" />
**password:** `[password]`
### PDF  3
<img width="985" height="842" alt="image" src="https://github.com/user-attachments/assets/d49e7eda-7f22-4e31-a8b3-2d45a6c15e78" />
**password**  `[!@#$%^&]`



### PDF Password Cracking Results

| PDF | Password Attempts | Result | Attempts Required |
|---|---|---|---:|
| Patient PDF 1 | `123456` | Password Recovered | 1 |
| Patient PDF 2 | `[REDACTED]` | Password Recovered | 2 |
| Patient PDF 3 | `[REDACTED]` | Password Recovered | 3,535 |

### Observation

All three password-protected PDFs were successfully opened during the
authorized password-strength assessment.

The results demonstrate that weak or predictable passwords can be
recovered through offline password-cracking techniques.

### Security Impact

An attacker who obtains encrypted PDF files could potentially recover
their passwords if weak credentials are used, resulting in unauthorized
disclosure of sensitive patient information.

### Recommendation

- Use long, unique, randomly generated passwords.
- Avoid predictable passwords such as `123456`.
- Use appropriate document encryption.
- Protect sensitive patient documents with strong access controls.
- Never store or publish recovered passwords in source repositories.

  ## 📋 Findings

| # | Finding | Severity | Status |
|---|---|---|---|
| 1 | SQL Injection in Admin Login | High | Confirmed |
| 2 | Weak PDF Password Protection | High | Confirmed |


## 📚 Key Learning

This lab helped me understand how penetration testers
systematically move from reconnaissance and scanning to
enumeration, vulnerability identification, validation,
documentation, and remediation.

---

## ⚠️ Disclaimer

This project was conducted for educational and authorized
cybersecurity training purposes.

Testing was limited to the scope and authorization provided
for the lab. No unauthorized access, data extraction, or
disruption of services was intended.
linkedin:https://www.linkedin.com/in/md-nazeerullaa-51211133a/








