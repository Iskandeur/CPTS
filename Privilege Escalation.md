A critical component of the [[Post-Exploitation]] phase.

Involves techniques to increase permissions from those initially obtained during [[Exploitation]] to a higher level (e.g., standard user to administrator or root).

## Goal

- Obtain higher privileges on a compromised system or within a domain.
- Gain access to more sensitive data, system configurations, or functionalities.
- Enable further actions like establishing more robust [[Persistence]], performing deeper [[Pillaging]], or facilitating [[Lateral Movement]].

## Importance

- Often unlocks access to critical systems or data needed to meet [[Penetration Test]] objectives.
- Demonstrates significant impact beyond initial access.
- Target privileges are typically:
    - **Linux:** `root`
    - **Windows:** `SYSTEM`, `Administrator`, Domain Administrator

## Types

- **Vertical Privilege Escalation:** Gaining higher privileges on the *same* system (e.g., user -> root).
- **Horizontal Privilege Escalation:** Gaining access to the account or resources of *another user* with similar privilege levels (less common usage of the term, often considered part of [[Lateral Movement]] or credential theft).

## Methods

*(Highly dependent on OS and environment)*

- **Exploiting Kernel Vulnerabilities:** Leveraging flaws in the OS kernel (requires specific [[CVE]]s applicable to the target).
- **Misconfigured Services:** Services running with excessive privileges that can be abused.
- **Insecure File Permissions:** Readable/writable sensitive files (e.g., `/etc/shadow`, configuration files with passwords), writable binaries or scripts run by privileged users.
- **Stored Credentials:** Finding passwords or keys during [[Pillaging]] (in files, scripts, registry, memory - e.g., using Mimikatz).
- **Abusing SUID/GUID Binaries (Linux):** Exploiting binaries that run with the permissions of their owner/group rather than the user executing them.
- **Exploiting Service Permissions (Windows):** Abusing weak permissions on services to modify their execution path or configuration.
- **DLL Hijacking:** Placing malicious DLLs to be loaded by privileged applications.
- **Unquoted Service Paths (Windows):** Exploiting spaces in service paths that are not properly quoted.
- **Credential Dumping:** Extracting credentials from memory (e.g., LSASS on Windows).
- **Token Impersonation/Theft (Windows):** Stealing access tokens from privileged processes or users.
- **Exploiting sudo Configuration (Linux):** Abusing `sudo` rules that allow specific commands to be run as root.

## Escalation via Credentials

Obtaining credentials for a higher-privileged user (e.g., through [[Pillaging]] or [[Kerberoasting]]) and simply logging in as that user *is* a form of privilege escalation. 