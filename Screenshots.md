## Vulnerability 1: IDOR (Insecure Direct Object Reference)

**Basic Scanning**
- Use Nmap to discover open ports and service details:

  ``` nmap -sV -Pn -p- localhost```

<img width="657" height="198" alt="image" src="https://github.com/user-attachments/assets/cc6c9828-bf5c-4dc2-ac7f-af8705614596" /><br></br>
<img width="655" height="62" alt="image" src="https://github.com/user-attachments/assets/95df67f7-38af-4568-aeb8-8398829434f2" />


- Check HTTP Headers

Use `curl`:

```curl -I http://localhost:3000```

<img width="654" height="280" alt="image" src="https://github.com/user-attachments/assets/40805941-a3ea-4c6e-9411-367498914e10" />

<!-- Missing security headers (e.g., CSP, X-Frame-Options)

Server version info (e.g., Express) -->
