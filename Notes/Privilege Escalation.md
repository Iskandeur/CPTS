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

Privesc checklists exist, one excellent resource is [HackTricks](https://book.hacktricks.xyz), which has an excellent checklist for both [Linux](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html) and [Windows](https://book.hacktricks.wiki/en/windows-hardening/checklist-windows-privilege-escalation.html) local privilege escalation. Another excellent repository is [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings), which also has checklists for both [Linux](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md) and [Windows](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md).
#new 

### Enumeration Scripts
Many of the above commands may be automatically run with a script to go through the report and look for any weaknesses. We can run many scripts to automatically enumerate the server by running common commands that return any interesting findings. Some of the common Linux enumeration scripts include [LinEnum](https://github.com/rebootuser/LinEnum.git) and [linuxprivchecker](https://github.com/sleventyeleven/linuxprivchecker), and for Windows include [Seatbelt](https://github.com/GhostPack/Seatbelt) and [JAWS](https://github.com/411Hall/JAWS).

Another useful tool we may use for server enumeration is the [Privilege Escalation Awesome Scripts SUITE (PEASS)](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite), as it is well maintained to remain up to date and includes scripts for enumerating both Linux and Windows.

>Note: These scripts will run many commands known for identifying vulnerabilities and create a lot of "noise" that may trigger anti-virus software or security monitoring software that looks for these types of events. This may prevent the scripts from running or even trigger an alarm that the system has been compromised. In some instances, we may want to do a manual enumeration instead of running scripts.


## Escalation via Credentials

Obtaining credentials for a higher-privileged user (e.g., through [[Pillaging]] or [[Kerberoasting]]) and simply logging in as that user *is* a form of privilege escalation. 