A common type of [[Penetration Test]].

## Perspective

Simulates an attacker who has already gained initial access to the internal corporate network.
This could represent:
- A malicious insider (disgruntled employee, etc.).
- An attacker who has successfully breached the perimeter (e.g., via malware, phishing, or exploiting an external vulnerability).
- An "assumed breach" scenario, skipping the external phase to focus purely on internal security.

## Goal

- Assess the security posture *within* the network perimeter.
- Identify vulnerabilities on internal servers, workstations, and network devices.
- Test network segmentation effectiveness.
- Evaluate internal monitoring and detection capabilities.
- Attempt to gain access to sensitive internal resources (databases, file shares, domain controllers).
- Escalate privileges within the internal network, often aiming for [[Domain Admin]] or equivalent.

## Methodology

Typically starts *after* initial access is assumed or achieved. Heavy focus on:
- [[Information Gathering]] (Internal Recon - network scanning, service discovery within internal ranges)
- [[Host Enumeration]] (internal systems)
- [[Vulnerability Assessment]] (internal focus - misconfigurations, weak permissions, patch levels)
- [[Pillaging]] (searching compromised hosts for credentials, sensitive data)
- [[Privilege Escalation]] (local and domain)
- [[Lateral Movement]] (pivoting between systems, accessing shares, using discovered credentials)
- [[Active Directory]] attacks (Kerberoasting, Pass-the-Hash, etc.)

## Access Requirements

- May be executed immediately following a successful [[External Penetration Test]] breach.
- Often starts with the tester being given network access (e.g., a network drop, credentials for a standard user account).
- May require testing isolated networks with no internet access, necessitating physical on-site presence. 