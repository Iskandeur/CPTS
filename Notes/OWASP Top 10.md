A standard awareness document representing a broad consensus about the most critical security risks to [[Web Application|web applications]]. It provides a good starting point for web application security assessments.

- **Maintained by:** [[OWASP (Open Web Application Security Project)]]
- **Purpose:** Educate developers, designers, architects, managers, and organizations about the consequences of common web application security weaknesses.
- **Current List (2021):** *(See [OWASP Top 10 Project](https://owasp.org/www-project-top-ten/) for full details)*
    1.  **A01: Broken Access Control:** Failures in enforcing permissions.
    2.  **A02: Cryptographic Failures:** Weak or missing encryption, leading to sensitive data exposure.
    3.  **A03: Injection:** Flaws allowing untrusted data to be interpreted as commands or queries (e.g., [[SQL Injection (SQLi)]], Command Injection, [[Cross-Site Scripting (XSS)]]).
    4.  **A04: Insecure Design:** Fundamental design flaws missing threat modeling or secure design patterns.
    5.  **A05: Security Misconfiguration:** Insecure defaults, incomplete configurations, verbose errors, cloud service misconfigurations.
    6.  **A06: Vulnerable and Outdated Components:** Using libraries, frameworks, or other software modules with known vulnerabilities.
    7.  **A07: Identification and Authentication Failures:** Weaknesses in user identity verification, authentication, and session management.
    8.  **A08: Software and Data Integrity Failures:** Lack of protection against integrity violations (e.g., insecure updates, insecure deserialization).
    9.  **A09: Security Logging and Monitoring Failures:** Insufficient logging, monitoring, or response capabilities to detect and react to attacks.
    10. **A10: Server-Side Request Forgery (SSRF):** Flaws allowing an attacker to induce the server-side application to make requests to an unintended location.

*Note: The OWASP Top 10 is not exhaustive but covers the most common and impactful categories.* Familiarity with these categories is essential for web application pentesters. 