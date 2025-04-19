A core phase in [[Penetration Testing]], often initiated during [[Post-Exploitation]].

Involves using an already compromised system to access other systems within the same network.

## Goal

- Expand access within the target network.
- Reach specific target systems or data stores that were not directly accessible initially.
- Compromise additional user accounts, especially privileged ones ([[Domain Admin]], etc.).
- Test the effectiveness of network segmentation and internal security controls.
- Simulate the spread of an attack like ransomware.

## Importance

- Demonstrates the potential scope of a breach originating from a single compromised host.
- Often required to achieve high-impact objectives (e.g., compromising domain controllers).
- Tests internal security posture (e.g., Are workstations allowed to communicate directly? Are credentials reused? Is network traffic monitored?).
- Highlights the liability risk for organizations (e.g., failure to protect customer data across the network).

## Typical Sub-Phases (Iterative Cycle)

1.  **[[Pivoting]] / [[Tunneling]]:** Establish connectivity from the compromised host to other internal network segments or hosts.
2.  **[[Evasive Testing]]:** Consider detection potential for internal scanning and movement.
3.  **[[Information Gathering]] (Internal Recon):** Scan the internal network from the perspective of the compromised host. Identify live hosts, open ports, running services, potential targets.
4.  **[[Vulnerability Assessment]] (Internal):** Analyze internal systems for vulnerabilities, misconfigurations, weak permissions, trust relationships.
5.  **[[Exploitation]] (Internal / Privilege):** Exploit vulnerabilities found on other internal systems. Leverage credentials obtained during [[Pillaging]] or [[Privilege Escalation]].
6.  **[[Post-Exploitation]] (on new host):** Repeat post-exploitation steps (Pillaging, Persistence, Privilege Escalation) on newly compromised systems.

This cycle repeats as access expands across the network. 