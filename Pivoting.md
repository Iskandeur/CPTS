Alias: [[Tunneling]]

A technique used primarily during [[Lateral Movement]] (and sometimes [[Post-Exploitation]]) to route network traffic through a compromised host.

## Purpose

- Access network segments or hosts that are not directly reachable from the attacker's machine (e.g., internal networks, DMZs).
- Use the compromised host as a proxy to run scanning tools ([[Nmap]], etc.) or exploitation tools from the attacker's machine against internal targets.
- Bypass firewall rules that might prevent direct connection from the attacker's machine to internal targets.

## How it Works

- Leverages the compromised host's network connectivity.
- Creates a tunnel (e.g., using [[SSH]], [[Proxychains]], Metasploit's `portfwd` or `autoroute`, custom C2 channels) that forwards traffic from the attacker machine, through the compromised host, to the target internal system.

## Analogy

> Think of accessing a home printer (not accessible from the internet) by compromising a computer on the home network and using that computer to send the print job.

## Tools & Techniques

- **[[SSH]] Tunneling:**
    - Local Port Forwarding (`ssh -L`)
    - Remote Port Forwarding (`ssh -R`)
    - Dynamic Port Forwarding (`ssh -D` - creates a SOCKS proxy)
- **[[Proxychains]] / [[proxychains-ng]]:** Forces traffic from specified applications through a proxy (like one set up with `ssh -D`).
- **Metasploit Framework:**
    - `portfwd` command
    - `autoroute` module (routes traffic through a Meterpreter session)
- **[[socat]]**
- **Custom C2 frameworks:** Often include pivoting capabilities.

## Importance

- Essential for exploring internal networks after an initial compromise.
- Enables the use of familiar attacker tools against otherwise inaccessible targets.
- Key enabler for effective [[Lateral Movement]]. 