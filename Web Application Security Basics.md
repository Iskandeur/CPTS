Fundamental concepts for understanding and testing web applications.

## [[Web Server]]

- **Definition:** Backend software (e.g., Apache, Nginx, IIS) that handles [[HTTP]]/[[HTTPS]] requests from client browsers.
- **Function:** Receives requests, routes them to the appropriate web application component or static file, and sends back responses.
- **Common Ports:** Typically listens on [[TCP]] port `80` ([[HTTP]]) and `443` ([[HTTPS]]), but can be configured on non-standard ports.
- **Security Importance:** As web applications are often internet-facing, vulnerabilities in the web server software itself or the applications it hosts can lead to compromise of the backend server and potentially the internal network.

## Web Application Attack Surface

Web applications present a vast attack surface due to their complexity and interaction with user input. Common areas to test include:
- Authentication and Authorization
- Session Management
- Input Validation (handling user-supplied data)
- Cryptography implementation
- Server-side logic
- Client-side code
- Configuration of the web server and application framework

## [[OWASP Top 10]]

A standard awareness document representing a broad consensus about the most critical security risks to web applications. It provides a good starting point for web application security assessments.

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