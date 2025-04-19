A common type of [[Penetration Test]].

## Perspective

Simulates an attacker with **no prior access** to the internal network, operating from the public internet (an anonymous external perspective).

## Goal

- Assess the security of the organization's external network perimeter.
- Identify vulnerabilities in internet-facing systems (web servers, VPN endpoints, mail servers, etc.).
- Determine if sensitive data can be accessed from the outside.
- Attempt to gain unauthorized access to the internal network from the external perimeter.

## Common Scope

- Public IP address ranges.
- Public-facing web applications and APIs.
- VPN gateways.
- Mail servers (e.g., testing for open relays, vulnerabilities).
- DNS servers.

## Methodology

Typically involves heavy use of:
- [[Open-Source Intelligence (OSINT)]]
- [[Infrastructure Enumeration]] (external focus)
- [[Service Enumeration]] (on discovered external services)
- [[Host Enumeration]] (on discovered external hosts)
- [[Vulnerability Assessment]]
- [[Exploitation]] (targeting external services)
- Potentially leading to [[Post-Exploitation]] and initial internal access if perimeter is breached.

## Considerations

- **ISP Blocking:** Performing scans from a residential ISP may lead to blocks. Using a [[VPN]] or [[VPS (Virtual Private Server)]] is recommended.
- **Stealth:** Client requirements for stealth ([[Evasive Testing]]) vary. Some want a quiet approach, others may want a hybrid approach to test detection capabilities (e.g., [[IDS]]/[[IPS]], [[WAF]]). 