## Vulnerability 1: IDOR (Insecure Direct Object Reference)

**Basic Scanning**
- Use Nmap to discover open ports and service details:

  ``` nmap -sV -Pn -p- localhost```

<img width="657" height="198" alt="image" src="https://github.com/user-attachments/assets/cc6c9828-bf5c-4dc2-ac7f-af8705614596" /><br></br>
<img width="655" height="62" alt="image" src="https://github.com/user-attachments/assets/95df67f7-38af-4568-aeb8-8398829434f2" />


- Check HTTP Headers

Use `curl`:

```curl -I http://localhost:3000```

<img width="654" height="280" alt="image" src="https://github.com/user-attachments/assets/40805941-a3ea-4c6e-9411-367498914e10" /><br></br>

<!-- Missing security headers (e.g., CSP, X-Frame-Options)

Server version info (e.g., Express) -->

- **Affected URL:** ` /rest/user/2`  
- **Method:** Manipulated feedback ID to access other users' data  
- **Payload:**  
  ```http
  GET /rest/user/2 HTTP/1.1
  Host: localhost:3000
-	**Fix:** Implement authorization checks for user-owned objects.

<img width="834" height="229" alt="image" src="https://github.com/user-attachments/assets/f20d6f4a-de71-4c2c-9845-8f0fe7d728aa" /><br></br>

- Manipulate request by changing request URLs from `GET /rest/user/1 HTTP/1.1` into `GET /rest/user/2 HTTP/1.1` <br></br>

- Next, I execute IDOR challenge with the intercepting the Feedback section by changing the ID 1 → 2 (GET /rest/products/2/reviews/)<br></br>

<img width="513" height="147" alt="image" src="https://github.com/user-attachments/assets/6bd2b3a5-615d-40e1-b191-81ad372e6c69" /><br></br>

- Result shows another user’s feedback appears = IDOR vulnerability with a message `yOur fir3wall needs m0r3 muscl3` by the account `uvogin@juice-sh.op`
<br></br>

<img width="385" height="407" alt="image" src="https://github.com/user-attachments/assets/91c5f79c-cb79-476b-8c64-0d15852a6d22" />
<br></br>

- Lastly, I execute forged review by post a review as another user and edit any user's existing reviews which shows security vulnerability. 
<br></br>

<img width="1012" height="395" alt="image" src="https://github.com/user-attachments/assets/26887c68-1d61-445f-8dd4-a061a724258c" />
<br></br>
⸻

## ⚠️ Vulnerability 2: Stored XSS
- **Vector:** Search bar input
- **Payload:** <script>alert("1")</script>
- **Impact:** Executes script on all pages rendering search term
- **Fix:** Input sanitization and output encoding.
<br></br>

<img width="678" height="557" alt="image" src="https://github.com/user-attachments/assets/5b3ea1ed-d472-4897-a704-eb55929f6711" /><br></br>
⸻

## 🧨 Vulnerability 3: SQL Injection
- **Endpoint:** /rest/user/login
- **Payload:** ' OR 1=1 --
- **Impact:** Bypasses authentication
- **Fix:** Use parameterized SQL queries.

<img width="299" height="331" alt="image" src="https://github.com/user-attachments/assets/72f5c0f2-c0e0-4655-b54b-b72d1b7b467b" /><br></br>

<img width="1121" height="168" alt="image" src="https://github.com/user-attachments/assets/d4330ac0-3239-4a75-9c45-dc8d74770083" />

- Successfully intercepted login request with the SQL injection.

⸻

