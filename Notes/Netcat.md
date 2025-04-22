---
aliases: [ncat, nc]
---

## Overview

Netcat (`nc`, often called `ncat` in newer versions) is a fundamental network utility for interacting with TCP and UDP ports. It's often referred to as the "Swiss-army knife" for TCP/IP networking.

## Key Uses in Penetration Testing

Netcat is used extensively in penetration testing for various tasks:

*   **Connecting to Shells:** Its primary use is often for establishing [[Reverse Shell|reverse shells]] or connecting to [[Bind Shell|bind shells]] (covered in detail elsewhere).
*   **Port Interaction / [[Banner Grabbing]]:** `netcat` can connect to any listening port to interact directly with the service or grab its banner to identify the running software.
    *   **Example:** Connecting to an [[SSH]] port (`22`) to retrieve its banner:
        ```shell-session
        Iskandeur@htb[/htb]$ nc 10.10.10.10 22

        SSH-2.0-OpenSSH_8.4p1 Debian-3
        ```
*   **File Transfer:** Can be used to transfer files between machines (details covered elsewhere).
*   **Port Scanning:** Can perform basic [[Port Scanning]] (though tools like `[[Nmap]]` are more specialized).

## Availability

*   **Linux:** Comes pre-installed on most Linux distributions.
*   **Windows:** A version can be downloaded from the [Nmap project page](https://nmap.org/download.html) (as `ncat.exe`).
*   **Windows PowerShell Alternative:** [PowerCat](https://github.com/besimorhino/powercat) is a popular PowerShell implementation.

## Related Tools

*   [[Socat]]: A more advanced utility with additional features like enhanced port forwarding and device connectivity.