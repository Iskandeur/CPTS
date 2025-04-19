Alias: [[CVE]]

A system for identifying, defining, and cataloging publicly disclosed cybersecurity vulnerabilities.

- **Website:** [cve.org](https://www.cve.org/)
- **Managed by:** MITRE Corporation, sponsored by CISA (US Dept. of Homeland Security).

## Format

Each vulnerability is assigned a unique identifier: `CVE-YYYY-NNNNN`
- `YYYY`: Year the CVE ID was assigned or the vulnerability was published.
- `NNNNN`: Sequence number (can have 4 or more digits).

## Purpose

- Provides a standardized identifier for a specific vulnerability across different platforms, tools, and databases.
- Facilitates [[Vulnerability Research]] and tracking.
- Enables correlation between vulnerability scanners, threat intelligence, and patch management systems.

## Usage in Pentesting

- During [[Vulnerability Research]], identified software versions are checked against CVE databases (like [[NVD]], [[CVEdetails]]) to find known vulnerabilities.
- CVE IDs are often referenced in [[Reporting]] to clearly identify vulnerabilities found.

See also: [[National Vulnerability Database (NVD)]], [[CVSS]] 