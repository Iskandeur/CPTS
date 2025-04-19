`GoBuster` is a versatile command-line tool used for brute-forcing URIs (directories and files), DNS subdomains, and Virtual Host names on target web servers. It helps uncover hidden content and infrastructure during [[Web Enumeration]] and [[Information Gathering]].

## Modes

GoBuster operates in several modes, specified by a command-line switch:

*   `dir`: Directory/file brute-forcing.
*   `dns`: DNS subdomain enumeration.
*   `vhost`: Virtual host brute-forcing (on target web server).
*   `s3`: Enumeration of public AWS S3 buckets.

## Directory/File Enumeration (`dir` mode)

This mode is used to find existing (but potentially unlinked) directories and files on a web server by trying names from a [[Wordlists|wordlist]].

```shell-session
# Usage: gobuster dir -u <target_url> -w <wordlist_path> [options]
Iskandeur@htb[/htb]$ gobuster dir -u http://10.10.10.121/ -w /usr/share/seclists/Discovery/Web-Content/common.txt

===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.10.121/
[+] Threads:        10
[+] Wordlist:       /usr/share/seclists/Discovery/Web-Content/common.txt
[+] Status codes:   200,204,301,302,307,401,403 # Default codes indicating existence
[+] User Agent:     gobuster/3.0.1
[+] Timeout:        10s
===============================================================
2020/12/11 21:47:25 Starting gobuster
===============================================================
/.hta (Status: 403)
/.htpasswd (Status: 403)
/.htaccess (Status: 403)
/index.php (Status: 200)
/server-status (Status: 403)
/wordpress (Status: 301)
===============================================================
2020/12/11 21:47:46 Finished
===============================================================
```

Example with common.txt from [[SecLists]]: `gobuster dir -u http://94.237.51.163:33863 -w /usr/share/seclists/Discovery/Web-Content/common.txt`

**Interpreting Results:**

*   Pay attention to the [[HTTP status codes]]. `200 OK` usually means found, `301 Moved Permanently` or `302 Found` indicate redirects (also often interesting), `403 Forbidden` means found but not accessible, `401 Unauthorized` requires authentication.
*   In the example, `/wordpress` (Status: 301) indicates a likely WordPress installation.

## DNS Subdomain Enumeration (`dns` mode)

This mode tries to find valid subdomains for a given domain using a wordlist.

**Prerequisite:** Ensure your system has a working DNS resolver configured (e.g., in `/etc/resolv.conf`).

```shell-session
# Usage: gobuster dns -d <domain> -w <wordlist_path> [options]
# Wordlist typically from SecLists: Discovery/DNS/subdomains-top1million-*.txt or similar
Iskandeur@htb[/htb]$ gobuster dns -d inlanefreight.com -w /usr/share/SecLists/Discovery/DNS/namelist.txt 

===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Domain:     inlanefreight.com
[+] Threads:    10
[+] Timeout:    1s
[+] Wordlist:   /usr/share/SecLists/Discovery/DNS/namelist.txt
===============================================================
2020/12/17 23:08:55 Starting gobuster
===============================================================
Found: blog.inlanefreight.com
Found: customer.inlanefreight.com
Found: my.inlanefreight.com
Found: ns1.inlanefreight.com
Found: ns2.inlanefreight.com
Found: ns3.inlanefreight.com
===============================================================
2020/12/17 23:10:34 Finished
===============================================================
```

This scan reveals several subdomains worth further investigation.

## Virtual Host Enumeration (`vhost` mode)

*(This section can be expanded later)*

This mode is used to find virtual host names configured on a target IP address. It modifies the `Host` header in HTTP requests.
