## Description

Banner grabbing is an enumeration technique used to gather information about services running on open ports. By connecting to a service, we can often retrieve a "banner" - a text response that typically includes the software name and version.

This information is valuable for identifying potential vulnerabilities associated with specific software versions.

## Example using Netcat

One tool commonly used for basic banner grabbing is [[Netcat]]. We can connect to a port, such as the default [[SSH]] port (`22`), and observe the response:

```shell-session
Iskandeur@htb[/htb]$ nc 10.10.10.10 22

SSH-2.0-OpenSSH_8.4p1 Debian-3
```

In this case, the banner `SSH-2.0-OpenSSH_8.4p1 Debian-3` reveals the [[SSH]] server software and version.

Web server headers provide a good picture of what is hosted on a web server. They can reveal the specific application framework in use, the authentication options, and whether the server is missing essential security options or has been misconfigured. 
We can use [[cURL]] to retrieve server header information from the command line. [[cURL]] is another essential addition to our penetration testing toolkit, and familiarity with its many options is encouraged.

```shell-session
Iskandeur@htb[/htb]$ curl -IL https://www.inlanefreight.com

HTTP/1.1 200 OK
Date: Fri, 18 Dec 2020 22:24:05 GMT
Server: Apache/2.4.29 (Ubuntu)
Link: <https://www.inlanefreight.com/index.php/wp-json/>; rel="https://api.w.org/"
Link: <https://www.inlanefreight.com/>; rel=shortlink
Content-Type: text/html; charset=UTF-8
```

Another handy tool is [EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness), which can be used to take screenshots of target web applications, fingerprint them, and identify possible default credentials.


## Other Tools

Other tools can also perform banner grabbing, often more systematically:

*   [[Nmap]]: Includes scripts and options specifically for service version detection, which relies heavily on banner grabbing (e.g., the `-sV` option).
*   [[Telnet]]: Can also be used for manual connections.
* [[cURL]]: For web servers
* EyeWitness
*   Specialized scripts or tools.

<!-- Lookup, maybe it's a technique also used by [[Nmap]] ? -->
<!-- Yes, Nmap uses banner grabbing extensively, especially with -sV -->
