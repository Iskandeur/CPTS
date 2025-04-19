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

## Other Tools

Other tools can also perform banner grabbing, often more systematically:

*   [[Nmap]]: Includes scripts and options specifically for service version detection, which relies heavily on banner grabbing (e.g., the `-sV` option).
*   [[Telnet]]: Can also be used for manual connections.
*   Specialized scripts or tools.

<!-- Lookup, maybe it's a technique also used by [[Nmap]] ? -->
<!-- Yes, Nmap uses banner grabbing extensively, especially with -sV -->
