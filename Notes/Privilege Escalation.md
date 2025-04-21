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

Let us take an example of running the Linux script from `PEASS` called `LinPEAS`:

```shell-session
Iskandeur@htb[/htb]$ ./linpeas.sh
...SNIP...

Linux Privesc Checklist: https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist
 LEYEND:
  RED/YELLOW: 99% a PE vector
  RED: You must take a look at it
  LightCyan: Users with console
  Blue: Users without console & mounted devs
  Green: Common things (users, groups, SUID/SGID, mounts, .sh scripts, cronjobs)
  LightMangenta: Your username


====================================( Basic information )=====================================
OS: Linux version 3.9.0-73-generic
User & Groups: uid=33(www-data) gid=33(www-data) groups=33(www-data)
...SNIP...
```

As we can see, once the script runs, it starts collecting information and displaying it in an excellent report. Let us discuss some of the vulnerabilities that we should look for in the output from these scripts.

#### Kernel Exploits

Whenever we encounter a server running an old operating system, we should start by looking for potential kernel vulnerabilities that may exist. Suppose the server is not being maintained with the latest updates and patches. In that case, it is likely vulnerable to specific kernel exploits found on unpatched versions of Linux and Windows.

For example, the above script showed us the Linux version to be `3.9.0-73-generic`. If we Google exploits for this version or use `searchsploit`, we would find a `CVE-2016-5195`, otherwise known as `DirtyCow`. We can search for and download the [DirtyCow](https://github.com/dirtycow/dirtycow.github.io/wiki/PoCs) exploit and run it on the server to gain root access.

The same concept also applies to Windows, as there are many vulnerabilities in unpatched/older versions of Windows, with various vulnerabilities that can be used for privilege escalation. We should keep in mind that kernel exploits can cause system instability, and we should take great care before running them on production systems. It is best to try them in a lab environment and only run them on production systems with explicit approval and coordination with our client.

#### Vulnerable Software

Another thing we should look for is installed software. For example, we can use the `dpkg -l` command on Linux or look at `C:\Program Files` in Windows to see what software is installed on the system. We should look for public exploits for any installed software, especially if any older versions are in use, containing unpatched vulnerabilities.


## Escalation via Credentials

Obtaining credentials for a higher-privileged user (e.g., through [[Pillaging]] or [[Kerberoasting]]) and simply logging in as that user *is* a form of privilege escalation. 