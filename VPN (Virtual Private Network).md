Alias: [[VPN]]

A technology that creates a secure, encrypted connection (tunnel) over a less secure network, such as the public internet.

## Purpose

- **Remote Access:** Allows users to connect securely to a private network (e.g., corporate network) from a remote location.
- **Privacy/Anonymity (Limited):** Can obscure the user's public IP address and encrypt traffic from local network eavesdropping (e.g., on public Wi-Fi).
- **Bypass Restrictions:** Can circumvent geo-blocking or network/firewall restrictions.

## Types (Remote Access)

- **Client-Based VPN:** Requires specific client software (e.g., [[OpenVPN]], Cisco AnyConnect) installed on the user's machine to establish the connection.
    - *Benefit:* Typically provides full network access as if directly connected (subject to firewall rules).
- **SSL VPN (Clientless):** Uses a web browser as the client to connect to an SSL VPN gateway.
    - *Benefit:* No dedicated client software needed.
    - *Limitation:* Often restricts access to specific web-based applications or resources, though some can provide broader network access.

## Use in Penetration Testing

- **Connecting to Lab Environments:** Essential for accessing private lab networks like [[Hack The Box (HTB)]], TryHackMe, or custom corporate labs.
    - *Example HTB Connection (using OpenVPN):* `sudo openvpn <username>.ovpn`
    - Verify connection with `ifconfig` (look for `tun0` adapter) or `netstat -rn` (check routing table).
- **Obscuring Attacker IP (External Tests):** Using a commercial VPN service or a [[VPS (Virtual Private Server)]] as a jump box can help avoid blocks from the target or the tester's own ISP during external scans.
- **Accessing Internal Networks (During Engagements):** Clients may provide VPN access as the starting point for an [[Internal Penetration Test]].

## Security Considerations

- **Commercial VPN Privacy:** Claims of "no logging" by commercial VPN providers should be treated with skepticism. They do not guarantee true anonymity.
- **Hostile Lab Networks:** When connected to shared lab VPNs (like HTB), treat the network as **hostile**. Assume other users may try to scan or attack your machine.
    - **Mitigation:**
        - Connect *only* from a dedicated, isolated [[Testing Environment Setup|attack VM]].
        - Harden the VM: Disable password SSH login, firewall unnecessary ports, don't run unnecessary services (web servers, etc.).
        - Do not store sensitive client data or personal information on VMs used for shared labs.
- **VPN Service Security:** The security of the VPN itself depends on the provider's implementation, protocols used (e.g., OpenVPN, WireGuard, PPTP - avoid older/weaker ones), and configuration. 