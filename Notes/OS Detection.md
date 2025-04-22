# OS Detection

OS Detection (or OS Fingerprinting) is the process of determining the operating system running on a remote host.

## Techniques

*   **Active Fingerprinting:** Sending probes and analyzing responses (TCP/IP stack fingerprinting).
*   **Passive Fingerprinting:** Analyzing network traffic (e.g., TTL values, TCP window sizes).
*   **Application-Level Fingerprinting:** Inferring OS based on banners, behaviors, or specific characteristics of services running on the host (e.g., [[SSH]] versions, [[HTTP Headers|HTTP Server headers]], [[SMB]] details).

## Tools

*   [[Nmap]] (`-O` for active TCP/IP fingerprinting; `-sV` provides clues via service versions)
*   `p0f` (passive fingerprinting)
*   Specialized [[Nmap Scripting Engine (NSE)|NSE scripts]] (e.g., `smb-os-discovery.nse`) 