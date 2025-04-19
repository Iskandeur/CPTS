A category of [[Information Gathering]]. Follows [[Service Enumeration]].

Focuses on examining individual hosts (servers, workstations) identified during [[Infrastructure Enumeration]] and [[Service Enumeration]].

## Goal

- Identify the Operating System ([[OS]]) and version.
- Confirm running services and versions (cross-reference with [[Service Enumeration]]).
- Discover detailed configuration information.
- Identify potential misconfigurations or vulnerabilities specific to the host.
- Understand the host's role and context within the network.

## Scope

Applies to both external and internal perspectives. Internal enumeration often reveals more services and information, as administrators may be less strict with internal-facing systems.

> Administrators often consider internal services "secure" simply because they are not directly exposed to the internet, leading to potential carelessness and vulnerabilities.

## Methods

- **OS Fingerprinting:** Using tools like [[Nmap]] with specific scan types (`-O`).
- **Service-Specific Enumeration:** Deep dives into discovered services (e.g., enumerating [[SMB]] shares, querying [[SNMP]], exploring [[HTTP]] directories).
- **Authenticated Scans:** If credentials are available (e.g., from [[OSINT]] or previous exploits), performing scans as an authenticated user often reveals significantly more information.

## Importance

- Provides detailed information needed for [[Vulnerability Research]] and [[Exploitation]].
- Helps identify potential targets for [[Privilege Escalation]] or [[Lateral Movement]].
- Uncovers host-specific weaknesses. 