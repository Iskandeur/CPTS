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

- Protocol Understanding: Knowing whether a service uses [[TCP]] or [[UDP]] influences how it's scanned and potentially exploited. 