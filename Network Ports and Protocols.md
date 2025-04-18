Fundamental concepts for understanding network communication and identifying services during [[Information Gathering]].

## [[Network Ports]]

- **Definition:** Virtual endpoints for network connections, managed by the operating system.
- **Function:** Allow a host to differentiate between various types of incoming/outgoing traffic and direct it to the correct application or service.
- **Analogy:** Like specific doors or windows on a house (system) designated for certain deliveries (traffic types).
- **Numbering:** Each transport protocol ([[TCP]], [[UDP]]) has its own set of 65,535 ports (0-65535).

### Port Ranges

- **Well-Known Ports (0-1023):** Assigned by IANA to standard, widely used services (e.g., 80 for HTTP, 443 for HTTPS, 22 for SSH). Usually require root/administrator privileges to bind to.
- **Registered Ports (1024-49151):** Assigned by IANA for specific applications or services (e.g., 3389 for RDP, 5432 for PostgreSQL).
- **Dynamic/Private/Ephemeral Ports (49152-65535):** Used for temporary client-side connections or private services.

## Transport Protocols: [[TCP]] vs [[UDP]]

Define how data is transmitted between hosts.

- **[[TCP (Transmission Control Protocol)]]**
    - **Type:** Connection-oriented.
    - **Mechanism:** Establishes a reliable connection (three-way handshake: SYN, SYN-ACK, ACK) before data transfer. Guarantees ordered delivery and retransmits lost packets.
    - **Use Cases:** Situations requiring reliability (Web browsing - [[HTTP]]/[[HTTPS]], file transfer - [[FTP]], email - [[SMTP]], remote login - [[SSH]], [[SMB]], [[LDAP]], [[RDP]]).
    - **Analogy:** A registered letter requiring confirmation of delivery.
- **[[UDP (User Datagram Protocol)]]**
    - **Type:** Connectionless.
    - **Mechanism:** Sends data packets (datagrams) without establishing a prior connection. No guarantee of delivery, order, or error checking (left to the application).
    - **Use Cases:** Time-sensitive applications where speed is prioritized over perfect reliability (Streaming video/audio, [[DNS]], [[DHCP]], [[SNMP]], VoIP, online gaming).
    - **Analogy:** Sending a standard postcard - faster but no delivery guarantee.

## Importance for Pentesters

- **Service Identification:** Scanning for open ports ([[Port Scanning]]) is a primary way to identify running services during [[Service Enumeration]].
- **Vulnerability Mapping:** Knowing the standard port for a service helps identify potentially vulnerable services (e.g., finding port 21 open suggests an [[FTP]] server).
- **Non-Standard Ports:** Services running on unexpected ports can indicate attempts at obscurity or misconfiguration.
- **Protocol Understanding:** Knowing whether a service uses [[TCP]] or [[UDP]] influences how it's scanned and potentially exploited.
- **Memorization:** Familiarity with common ports/protocols (21, 22, 23, 25, 53, 80, 161, 389, 443, 445, 3389, etc.) significantly speeds up analysis during assessments.

### Learning Resources

- [Common Ports Cheat Sheet (StationX)](https://www.stationx.net/common-ports-cheat-sheet/)
- [Common Ports PDF (PacketLife - Archived)](https://web.archive.org/web/20240315102711/https://packetlife.net/media/library/23/common-ports.pdf)
- [Top 1000 Nmap Ports (Nullsweep)](https://nullsec.us/top-1-000-tcp-and-udp-ports-nmap-default/) 