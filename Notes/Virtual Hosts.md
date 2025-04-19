# Virtual Hosts

A virtual host is a feature of web servers that allows a single server (with one IP address) to host multiple domain names (e.g., `site1.com`, `site2.com`). The server uses the `Host` header in the [[HTTP]] request to determine which website to serve.

## Enumeration

Identifying virtual hosts associated with a target IP address is important during [[Web Enumeration]] as different virtual hosts might host different applications or have different security configurations.

Techniques involve manipulating the `Host` header while making requests to the target IP.

## Tools

*   `[[GoBuster]]` (`vhost` mode)
*   `ffuf` (`-H "Host: FUZZ.<domain>"`)
*   Burp Suite Intruder 