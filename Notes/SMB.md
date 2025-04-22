# SMB (Server Message Block)

SMB is a network file sharing protocol that allows applications on a computer to read and write to files and to request services from server programs in a computer network.

Primarily used by Windows, but implementations like Samba exist for Unix-like systems.

## Key Concepts

*   File and Printer Sharing
*   Authentication (NTLM, Kerberos)
*   Versions (SMBv1, SMBv2, SMBv3)
*   Common Ports (TCP 139, 445)
*   Enumeration Techniques (Shares, Users, OS info)

## Tools

*   [[smbclient]]
*   `smbmap`
*   `enum4linux` / `enum4linux-ng`
*   [[Nmap]] scripts (`smb-os-discovery`, `smb-enum-shares`, etc.) 