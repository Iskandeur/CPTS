Fundamental concepts for understanding network communication and identifying services during [[Information Gathering]].

## Definition

- **Definition:** Virtual endpoints for network connections, managed by the operating system.
- **Function:** Allow a host to differentiate between various types of incoming/outgoing traffic and direct it to the correct application or service.
- **Analogy:** Like specific doors or windows on a house (system) designated for certain deliveries (traffic types).
- **Numbering:** Each transport protocol ([[TCP]], [[UDP]]) has its own set of 65,535 ports (0-65535).

## Port Ranges

- **Port 0** is a reserved port in TCP/IP networking and is not used in TCP or UDP messages. If anything attempts to bind to port 0 (such as a service), it will bind to the next available port above port 1,024 because port 0 is treated as a "wild card" port.
- **Well-Known Ports (0-1023):** Assigned by IANA to standard, widely used services (e.g., 80 for [[HTTP]], 443 for [[HTTPS]], 22 for [[SSH]]). Usually require root/administrator privileges to bind to.
- **Registered Ports (1024-49151):** Assigned by IANA for specific applications or services (e.g., 3389 for [[RDP]], 5432 for [[PostgreSQL]]).
- **Dynamic/Private/Ephemeral Ports (49152-65535):** Used for temporary client-side connections or private services.

## Importance for Pentesters

- **Service Identification:** Scanning for open ports (Port Scanning) is a primary way to identify running services during [[Service Enumeration]].
- **Vulnerability Mapping:** Knowing the standard port for a service helps identify potentially vulnerable services (e.g., finding port 21 open suggests an [[FTP]] server).
- **Non-Standard Ports:** Services running on unexpected ports can indicate attempts at obscurity or misconfiguration.
- **Memorization:** Familiarity with common ports (21, 22, 23, 25, 53, 80, 161, 389, 443, 445, 3389, etc.) significantly speeds up analysis during assessments.

## Learning Resources

- [Common Ports Cheat Sheet (StationX)](https://www.stationx.net/common-ports-cheat-sheet/)
- [Common Ports PDF (PacketLife - Archived)](https://web.archive.org/web/20240315102711/https://packetlife.net/media/library/23/common-ports.pdf)
- [Top 1000 Nmap Ports (Nullsweep)](https://nullsec.us/top-1-000-tcp-and-udp-ports-nmap-default/)
