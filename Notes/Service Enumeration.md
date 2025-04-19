A category of [[Information Gathering]]. Follows [[Infrastructure Enumeration]].

Focuses on identifying network services running on discovered hosts that allow interaction over the network (or locally). This involves understanding [[Network Ports]] and the [[Network Protocols]] they use.

## Goal

For each discovered service:
- Identify the service (e.g., [[HTTP]], [[SSH]], [[SMB]], [[DNS]], [[SMTP]]).
- Determine the specific software and **version** running.
- Understand the **purpose** of the service within the environment.
- Gather any information the service provides (e.g., banners, configuration details).

## Methods

- **[[Port Scanning]]**: Using tools like [[Nmap]] to identify open [[Network Ports|ports]] and the services listening on them.
- **Service Detection (`-sV`):** Attempts to determine the version of the service running on open ports. Often involves [[Banner Grabbing]] and probing.
- **Script Scanning (`-sC` or `--script`):** Runs default or specified [[Nmap Scripting Engine (NSE)|NSE scripts]] against targets for vulnerability detection, advanced enumeration, etc.
- **OS Detection (`-O`):** Attempts to identify the target operating system.
- **Traceroute (`--traceroute`):** Maps the network hops to the target.

## Importance

- **Version Identification:** Crucial for [[Vulnerability Research]]. Outdated versions often have known [[CVE]]s.
- **Understanding Functionality:** Helps infer the host's role and potential attack vectors.
- **Finding Misconfigurations:** Default credentials, exposed management interfaces, etc.
- **Identifying Non-Standard Services:** Services running on unexpected [[Network Ports|ports]].

## Administrator Reluctance

Administrators may avoid updating services due to fear of breaking functionality ("if it ain't broke, don't fix it"). This often leads to known vulnerabilities remaining unpatched, creating opportunities for exploitation. 

### Techniques

- **Port Scanning:** Identifying open TCP/UDP ports.
- **[[Banner Grabbing]]:** Capturing information passively provided by services upon connection.
- **Service-Specific Probing:** Sending crafted requests to identify service details (e.g., querying [[SMB]] for shares, [[SNMP]] for configuration). 