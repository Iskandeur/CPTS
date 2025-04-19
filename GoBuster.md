#new 
After discovering a web application, it is always worth checking to see if we can uncover any hidden files or directories on the webserver that are not intended for public access. We can use a tool such as [ffuf](https://github.com/ffuf/ffuf) or [GoBuster](https://github.com/OJ/gobuster) to perform this directory enumeration. Sometimes we will find hidden functionality or pages/directories exposing sensitive data that can be leveraged to access the web application or even remote code execution on the web server itself.

#### Directory/File Enumeration

GoBuster is a versatile tool that allows for performing DNS, vhost, and directory brute-forcing. The tool has additional functionality, such as enumeration of public AWS S3 buckets. For this module's purposes, we are interested in the directory (and file) brute-forcing modes specified with the switch `dir`. Let us run a simple scan using the `dirb` `common.txt` wordlist.

```shell-session
Iskandeur@htb[/htb]$ gobuster dir -u http://10.10.10.121/ -w /usr/share/seclists/Discovery/Web-Content/common.txt

===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.10.121/
[+] Threads:        10
[+] Wordlist:       /usr/share/seclists/Discovery/Web-Content/common.txt
[+] Status codes:   200,204,301,302,307,401,403
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

An HTTP status code of `200` reveals that the resource's request was successful, while a 403 HTTP status code indicates that we are forbidden to access the resource. A 301 status code indicates that we are being redirected, which is not a failure case. It is worth familiarizing ourselves with the various [[HTTP status codes]]. The `Web Requests` Academy Module also covers HTTP status codes further in-depth.

The scan was completed successfully, and it identifies a WordPress installation at `/wordpress`. WordPress is the most commonly used CMS (Content Management System) and has an enormous potential attack surface. In this case, visiting `http://10.10.10.121/wordpress` in a browser reveals that WordPress is still in setup mode, which will allow us to gain remote code execution (RCE) on the server.

![WordPress language selection screen with a list of languages and a 'Continue' button.](https://academy.hackthebox.com/storage/modules/77/wordpress.png)

#### DNS Subdomain Enumeration

There also may be essential resources hosted on subdomains, such as admin panels or applications with additional functionality that could be exploited. We can use `GoBuster` to enumerate available subdomains of a given domain using the `dns` flag to specify DNS mode. First, let us clone the [[SecLists]] GitHub [repo](https://github.com/danielmiessler/SecLists), which contains many useful lists for fuzzing and exploitation:

#### Install SecLists

```shell-session
Iskandeur@htb[/htb]$ git clone https://github.com/danielmiessler/SecLists
```

```shell-session
Iskandeur@htb[/htb]$ sudo apt install seclists -y
```

Next, add a DNS Server such as 1.1.1.1 to the `/etc/resolv.conf` file. We will target the domain `inlanefreight.com`, the website for a fictional freight and logistics company.

```shell-session
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

This scan reveals several interesting subdomains that we could examine further. The [Attacking Web Applications with Ffuf](https://academy.hackthebox.com/module/details/54) module goes into more details about web enumeration and fuzzing.
