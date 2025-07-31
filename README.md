# 🧪 Penetration Testing Report – OWASP Juice Shop

**Project Type:** Web Application Pentest  
**Platform:** OWASP Juice Shop (Local Docker Instance)  
**Tester:** Siti Aisyah Amat Jalani  
**Date:** [Insert Date]  
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
| IDOR          | High     | `/api/Feedbacks/2` | 7.5 |
| Stored XSS    | Medium   | Search bar        | 6.1 |
| SQL Injection | High     | `/rest/user/login` | 8.1 |

---

## 🔓 Vulnerability 1: IDOR (Insecure Direct Object Reference)

- **Affected URL:** `/api/Feedbacks/2`  
- **Method:** Manipulated feedback ID to access other users' data  
- **Payload:**  
  ```http
  GET /api/Feedbacks/2 HTTP/1.1
  Host: localhost:3000
