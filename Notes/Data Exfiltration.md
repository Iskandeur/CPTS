Part of the [[Post-Exploitation]] phase.

Involves transferring data from the compromised network or system to an external location controlled by the tester.

## Purpose

- **Demonstrate Impact:** Prove that sensitive data could be stolen by an attacker.
- **Achieve Objectives:** Fulfill specific goals outlined in the [[Rules of Engagement (RoE)]] related to accessing or acquiring data.
- **Test Defenses:** Evaluate the effectiveness of Data Loss Prevention (DLP) solutions, egress filtering, and network monitoring in detecting or blocking unauthorized data transfer.

## Process

1.  **Identify Target Data:** Locate sensitive information identified during [[Pillaging]] or other [[Post-Exploitation]] activities.
2.  **Stage Data (Optional):** Consolidate data into a single location or archive.
3.  **Choose Exfiltration Method:** Select a technique based on available tools, network restrictions, and [[Evasive Testing]] requirements.
4.  **Transfer Data:** Execute the exfiltration.
5.  **Verify Transfer:** Confirm data arrived at the destination.

## Methods (Examples)

- **Network Protocols:**
    - [[HTTP]]/[[HTTPS]] (e.g., POST requests, file uploads)
    - [[DNS]] Tunneling (encoding data in DNS queries)
    - [[ICMP]] Tunneling
    - [[FTP]]/[[SFTP]]/[[SCP]]
    - [[SMB]] (if external access allowed)
- **Covert Channels:** Using protocols in unintended ways.
- **Cloud Storage:** Uploading directly to services like Dropbox, Google Drive (may be blocked).
- **Web Shells:** Using an existing web shell to download files.
- **Physical Access:** USB drives (if physical access is in scope).
- **Command & Control (C2) Channels:** Leveraging existing C2 infrastructure if established.

## Critical Considerations

- **CLIENT PERMISSION:** **NEVER exfiltrate actual sensitive client data without explicit, written permission** documented in the [[Rules of Engagement (RoE)]] or obtained during the test.
- **Legal/Compliance:** Unauthorized exfiltration of real data (PII, PHI, financial data) can have severe legal consequences.
- **Use Fake Data:** It is often sufficient (and much safer) to create *bogus* data (e.g., fake credit card numbers, SSNs) that mimics the format of sensitive data and exfiltrate that instead. Confirm this approach with the client.
- **Data Handling Regulations:** Be aware of regulations governing the type of data potentially involved ([[HIPAA]], [[PCI DSS|PCI]], [[GDPR]], [[GLBA]], [[FISMA]], etc.) and frameworks the client follows ([[NIST]], [[ISO]], [[CIS Controls]], etc.).
- **Evidence:** Document the process carefully. Use screen recordings or screenshots showing the data source (hostname, IP, path, user) and successful exfiltration for [[Reporting]].
- **Immediate Notification:** If *real* sensitive data is identified, **notify the client immediately** as per the incident handling procedures in the [[Rules of Engagement (RoE)]]. They may wish to pause or redirect the test. 