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
- **Banner Grabbing:** Capturing information passively provided by services upon connection.
- **Service-Specific Probing:** Using specialized clients or tools to interact with specific services and elicit version/configuration information.

## Importance

- **Version Identification:** Crucial for [[Vulnerability Research]]. Outdated versions often have known [[CVE]]s.
- **Understanding Functionality:** Helps infer the host's role and potential attack vectors.
- **Finding Misconfigurations:** Default credentials, exposed management interfaces, etc.
- **Identifying Non-Standard Services:** Services running on unexpected [[Network Ports|ports]].

## Administrator Reluctance

Administrators may avoid updating services due to fear of breaking functionality ("if it ain't broke, don't fix it"). This often leads to known vulnerabilities remaining unpatched, creating opportunities for exploitation. 