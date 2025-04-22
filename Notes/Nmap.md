`Nmap` (Network Mapper) is a powerful, open-source tool for network discovery, security auditing, and [[Information Gathering]]. It uses raw IP packets to determine hosts available on the network, services (application name and version) those hosts are offering, operating systems (and OS versions) they are running, types of packet filters/firewalls in use, and dozens of other characteristics.

## Core Scanning Techniques

### Basic Scan (Top 1000 TCP Ports)

By default, `nmap <target>` scans the 1,000 most common TCP ports. This is fast but may miss services on less common ports.

```shell-session
Iskandeur@htb[/htb]$ nmap 10.129.42.253

Starting Nmap 7.80 ( https://nmap.org ) at 2021-02-25 16:07 EST
Nmap scan report for 10.129.42.253
Host is up (0.11s latency).
Not shown: 995 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 2.19 seconds
```

### Full Port Scan (`-p-`)

To scan all 65,535 TCP ports, use the `-p-` option. This is much slower but more comprehensive.

### Version Detection (`-sV`)

Instructs `Nmap` to probe open ports to determine service/version info. This involves interacting with the service.

### Default Script Scan (`-sC`)

Runs a set of default scripts against the target. These scripts perform various checks, like looking for anonymous FTP access, getting web page titles, or checking SMB security modes. This is equivalent to `--script=default`.

### Combining Techniques

A common and informative scan combines these options:

```shell-session
Iskandeur@htb[/htb]$ nmap -sV -sC -p- 10.129.42.253

Starting Nmap 7.80 ( https://nmap.org ) at 2021-02-25 16:18 EST
Nmap scan report for 10.129.42.253
Host is up (0.11s latency).
Not shown: 65530 closed ports
PORT    STATE SERVICE     VERSION
21/tcp  open  ftp         vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxr-xr-x    2 ftp      ftp          4096 Feb 25 19:25 pub
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.14.2
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp  open  ssh         OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
80/tcp  open  http        Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: PHP 7.4.3 - phpinfo()
139/tcp open  netbios-ssn Samba smbd 4.6.2
445/tcp open  netbios-ssn Samba smbd 4.6.2
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_nbstat: NetBIOS name: GS-SVCSCAN, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-02-25T21:21:51
|_  start_date: N/A

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 233.68 seconds
```

## Understanding Nmap Output

*   **PORT:** The [[Network Ports|port number]] and protocol (e.g., `21/tcp`).
*   **STATE:** The state of the port (`open`, `closed`, `filtered`).
    *   `open`: A service is listening.
    *   `closed`: The port is accessible, but no service is listening.
    *   `filtered`: Nmap cannot determine the state, often due to a firewall.
*   **SERVICE:** The common service associated with the port (e.g., `ftp`, `ssh`, `http`).
*   **VERSION:** Detailed information about the service and its version, obtained via `-sV`.
*   **Script Output:** Results from `-sC` or specific `--script` runs, often providing valuable enumeration details (e.g., `ftp-anon`, `http-title`, `smb-os-discovery`).
*   **OS Guessing:** Nmap can make educated guesses about the OS based on TCP/IP stack fingerprinting (`-O`) or inferred from service versions (`-sV`). This is often included in the `Service Info` line or dedicated OS detection results.

## Nmap Scripting Engine (NSE)

The [[Nmap Scripting Engine (NSE)]] allows users to write (and use pre-written) scripts to automate a wide variety of networking tasks. Scripts can perform more advanced [[Service Enumeration]], vulnerability detection, exploitation, and more.

*   **Running Default Scripts:** Use `-sC`.
*   **Running Specific Scripts:** Use `--script <script-name or category>`. You can specify comma-separated names or use categories like `vuln`, `discovery`, `exploit`.
*   **Finding Scripts:** Use `locate *.nse` or check the `/usr/share/nmap/scripts/` directory (or equivalent).

### NSE Example: Banner Grabbing

The `banner` script specifically attempts to grab the service banner.

```shell-session
# Example: Grab banner from FTP service on multiple hosts
Iskandeur@htb[/htb]$ nmap -sV --script=banner -p21 10.10.10.0/24 
```

### NSE Example: SMB OS Discovery

The `smb-os-discovery` script queries the SMB service (typically on port 445) for OS details.

```shell-session
Iskandeur@htb[/htb]$ nmap --script smb-os-discovery.nse -p445 10.10.10.40

Starting Nmap 7.91 ( https://nmap.org ) at 2020-12-27 00:59 GMT
Nmap scan report for doctors.htb (10.10.10.40)
Host is up (0.022s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds

Host script results:
| smb-os-discovery: 
|   OS: Windows 7 Professional 7601 Service Pack 1 (Windows 7 Professional 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1:professional
|   Computer name: CEO-PC
|   NetBIOS computer name: CEO-PC\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2020-12-27T00:59:46+00:00

Nmap done: 1 IP address (1 host up) scanned in 2.71 seconds
```

## Next Steps After Nmap

Once Nmap identifies open ports and services, the next step in [[Service Enumeration]] is often to interact directly with those services using specific client tools. For example:

*   Use [[Netcat]] or `telnet` for manual [[Banner Grabbing]] and basic interaction.
*   Use an [[FTP]] client (like the command-line `ftp`) to explore FTP servers.
*   Use [[smbclient]] or other tools to enumerate [[SMB]] shares.
*   Browse web services identified on ports like 80 or 443 using a web browser or tools like [[cURL]].

Refer to specific notes on these protocols and tools for interaction details.
