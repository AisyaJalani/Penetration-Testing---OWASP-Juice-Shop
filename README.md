# 🧪 Penetration Testing Report – OWASP Juice Shop

**Project Type:** Web Application Pentest  
**Platform:** OWASP Juice Shop (Local Docker Instance)  
**Tester:** Aisyah Jalani  
**Date:** July 20, 2025
**Tools Used:** Burp Suite, Nmap, Firefox, FoxyProxy, Docker

---

## 🔍 Executive Summary

This project simulates a black-box penetration test against OWASP Juice Shop to identify vulnerabilities commonly found in modern web applications. The goal was to replicate real-world attacker behavior, report findings with impact analysis, and propose mitigation strategies.

---

## 🧠 Methodology

- **Reconnaissance:** Service discovery, URL enumeration, endpoint mapping  
- **Exploitation:** Manual testing using Burp Suite, payloads for XSS/SQLi/IDOR  
- **Analysis:** Manual vulnerability validation and impact analysis  
- **Reporting:** Structured documentation with CVSS scoring and fixes

---

## 📋 Key Findings

| Vulnerability | Severity | Endpoint | CVSS |
|---------------|----------|----------|------|
| IDOR          | High     | ` /rest/products/2/reviews/` | 7.5 |
| Stored XSS    | Medium   | Search bar        | 6.1 |
| SQL Injection | High     | ` /rest/user/2` | 8.1 |

---

## 🔓 Vulnerability 1: IDOR (Insecure Direct Object Reference)

- **Affected URL:** ` /rest/user/2`  
- **Method:** Manipulated feedback ID to access other users' data  
- **Payload:**  
  ```http
  GET /rest/user/2 HTTP/1.1
  Host: localhost:3000
-	**Fix:** Implement authorization checks for user-owned objects.

⸻

## ⚠️ Vulnerability 2: Stored XSS
- **Vector:** Search bar input
- **Payload:** <script>alert("1")</script>
- **Impact:** Executes script on all pages rendering search term
- **Fix:** Input sanitization and output encoding.

⸻

## 🧨 Vulnerability 3: SQL Injection
- **Endpoint:** /rest/user/login
- **Payload:** ' OR 1=1 --
- **Impact:** Bypasses authentication
- **Fix:** Use parameterized SQL queries.

⸻

## 🧰 Tools & Technologies
- Docker (Juice Shop deployment)
- Burp Suite Community Edition
- Nikto, Nmap, SQLmap
- Firefox + FoxyProxy

⸻

## 📝 Lessons Learned
-	Importance of input validation and access control
-	Manual testing can uncover logic flaws missed by scanners
-	Learned to chain enumeration with exploitation
-	Practiced writing structured pentest reports with technical accuracy

⸻

## 📸 Screenshots

Screenshots of the lab <a href="https://github.com/AisyaJalani/Penetration-Testing---OWASP-Juice-Shop/blob/main/Screenshots.md">here</a>.

  
