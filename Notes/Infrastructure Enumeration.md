A category of [[Information Gathering]].

Focuses on mapping the target organization's network infrastructure, both internal and external.

## Goal

- Understand the company's position on the internet and intranet.
- Identify key network components and their relationships.
- Create a list of potential target hosts and IP addresses.
- Gather information about security measures in place.

## Methods

- Uses [[Open-Source Intelligence (OSINT)]] findings.
- Employs initial *active* scans (requires careful consideration of scope and [[Rules of Engagement (RoE)]]).
- Leverages services like [[DNS]] to map servers and hosts.

## Targets

- Name servers
- Mail servers
- Web servers
- Cloud instances ([[AWS]], [[Azure]], [[GCP]], etc.)
- IP address ranges ([[CIDR]])
- Domains and subdomains

## Process

1.  Gather initial data from [[OSINT]].
2.  Perform active reconnaissance (e.g., DNS lookups, zone transfers if possible, targeted port scans on known infrastructure).
3.  Map discovered hosts, IP addresses, and domains.
4.  Compare findings against the official scope defined in the [[Rules of Engagement (RoE)]].
5.  Attempt to identify security products or defenses (e.g., [[WAF]], [[IDS]]/[[IPS]]) to inform [[Evasive Testing]] strategy.

## Importance

- Provides targets for [[Service Enumeration]] and [[Host Enumeration]].
- Helps understand network segmentation and architecture.
- Crucial for both external and internal [[Penetration Test]]s.
