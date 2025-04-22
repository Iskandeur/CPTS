Port scanning is a fundamental technique used in [[Information Gathering]] to identify open [[Network Ports]] on a target host or network. By probing these ports, we can determine which services are potentially running and listening for connections.

This process is crucial for understanding the attack surface and often precedes [[Service Enumeration]]. Tools like [[Nmap]] are commonly used for port scanning.

Network scanning involves probing target systems for open ports, identifying running services, and potentially detecting the operating system and version. It's a fundamental step in penetration testing, providing insights into potential vulnerabilities. The choice of scan type depends on the objectives, network conditions, desired stealth, and reliability. (Future links: [[TCP Scan Types]], [[UDP Scan Types]])

## Key Concepts

*   **Open Port:** Indicates a service is actively listening on that port.
*   **Closed Port:** Indicates that the host received the probe but no service is listening on that port.
*   **Filtered Port:** Indicates that the probe was likely blocked by a firewall or other filtering mechanism, and the state (open or closed) cannot be determined.
*   **Scan Types:** Different techniques exist (e.g., TCP SYN scan, TCP Connect scan, UDP scan) with varying levels of speed, stealth, and reliability. (Future links: `[[TCP Scan Types]]`, `[[UDP Scan Types]]`)

## Common Tools

*   [[Nmap]]
*   `masscan` (needs creation?)
*   Built-in OS tools (less common for comprehensive scans) 
