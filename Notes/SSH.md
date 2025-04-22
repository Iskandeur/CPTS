## Overview

[Secure Shell (SSH)](https://en.wikipedia.org/wiki/SSH_\(Secure_Shell\)) is a network protocol that runs on port `22` by default. It provides users, particularly system administrators, a secure way to access computers remotely.

SSH operates on a client-server model, connecting a user running an SSH client application (like `OpenSSH`) to an SSH server running on the remote host.

## Authentication

SSH can be configured with:

*   **Password Authentication:** Traditional username and password login.
*   **Public-Key Authentication:** Passwordless login using an [SSH public/private key pair](https://serverpilot.io/docs/how-to-use-ssh-public-key-authentication/).

## Uses

SSH is versatile and can be used for:

*   Remotely accessing systems on the same network or over the internet.
*   Facilitating connections to resources in other networks using [port forwarding](Port Forwarding) or proxying.
*   Transferring files to and from remote systems using related protocols like [SCP](SCP) or [SFTP](SFTP).

## Penetration Testing Context

During penetration tests or real-world assessments, attackers often obtain credentials (cleartext passwords or SSH private keys) that allow direct connection to a system via SSH.

An SSH connection offers several advantages over typical [[Reverse Shell|reverse shells]]:

*   **Stability:** SSH sessions are generally more stable.
*   **Functionality:** Provides a full interactive shell.
*   **Pivoting:** Can act as a "jump host" to enumerate and attack other internal network hosts.
*   **File Transfer:** Easily transfer tools and exfiltrate data.
*   **Persistence:** Can be used to set up persistent access.

If credentials (username `Bob`, IP `10.10.10.10`) are obtained, you can connect using the following format:

```shell-session
Iskandeur@htb[/htb]$ ssh Bob@10.10.10.10

Bob@remotehost's password: *********

Bob@remotehost#
```

It's also common to find local private keys on compromised systems or to add an attacker's public key to the target user's `authorized_keys` file to gain passwordless SSH access (discussed further in privilege escalation or persistence sections).

SSH is an essential tool for secure remote connections and also enables techniques like port forwarding, which can be very useful.

