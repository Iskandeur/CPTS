A specific type of [[Information Gathering]] performed during the [[Post-Exploitation]] phase.

Focuses on searching for and collecting sensitive information *locally* on a compromised host or accessible network shares.

## Goal

- Find data that demonstrates the impact of the compromise.
- Discover credentials, keys, tokens, or configuration files that enable [[Privilege Escalation]] or [[Lateral Movement]].
- Understand the role of the compromised host within the network.
- Gather business-relevant information as defined by the [[Rules of Engagement (RoE)]].

## Targets

- User directories (Downloads, Documents, Desktop)
- Configuration files (web servers, applications, services)
- Scripts ([[Powershell]], Bash, Python - may contain hardcoded credentials)
- Password vaults / KeePass databases
- Browser history and saved passwords
- Email archives (.pst files)
- Network shares ([[SMB]], [[NFS]])
- Registry keys (Windows)
- SSH keys
- Log files
- Specific document types (.xlsx, .docx, .txt, .pdf)

## Network Context

Pillaging also involves analyzing the local host's network configuration to understand its place and potential reach:

| Category     | Examples        |
| :----------- | :-------------- |
| Interfaces   | IP Addresses, Subnets |
| Routing       | Routing Tables  |
| DNS Settings | DNS Servers     |
| ARP Cache    | Neighboring Hosts |
| Services      | Listening Ports |
| VPN Configs  | VPN Details     |
| Shares        | Mounted Drives  |
| Network Traffic | `netstat`, Packet Captures (if possible/necessary) |

Understanding network context helps plan [[Lateral Movement]].

## Importance

- Directly shows the *value* an attacker can gain from compromising a host.
- Often provides the keys (credentials, info) needed to move deeper into the network.
- Example: Finding a password policy requiring only 8 non-special characters suggests [[Brute Force]] or password guessing might be effective against other accounts. 