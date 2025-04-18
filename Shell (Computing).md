A command-line interface (CLI) program that allows users to interact with an operating system by typing commands.

## Function

- Takes keyboard input from the user.
- Passes commands to the operating system kernel for execution.
- Displays output from commands.

## Common Shells

- **Linux/Unix:**
    - `sh` (Bourne Shell - original Unix shell)
    - `bash` (Bourne Again SHell - very common default on Linux, enhanced `sh`)
    - `zsh` (Z Shell - popular alternative with extra features)
    - `csh` / `tcsh` (C Shell / TENEX C Shell)
    - `ksh` (KornShell)
    - `fish` (Friendly Interactive SHell)
- **Windows:**
    - `cmd.exe` (Command Prompt - traditional)
    - `PowerShell` (Modern, more powerful object-oriented shell and scripting language)

## Use in Penetration Testing ("Getting a Shell")

In pentesting, "getting a shell" means gaining interactive command-line access to a compromised target system.

### Methods of Obtaining a Shell

- Exploiting a network service vulnerability.
- Exploiting a web application vulnerability (e.g., Remote Code Execution - RCE).
- Obtaining valid credentials and logging in remotely (e.g., via [[SSH]]).
- Uploading and executing malicious code (e.g., via file upload vulnerability).

### Types of Shell Connections

- **[[Reverse Shell]]**
    - **Mechanism:** The compromised target machine *initiates* a connection *back* to a listener controlled by the attacker on their attack machine.
    - **Use Case:** Very common. Often bypasses firewalls that block incoming connections to the target but allow outgoing connections.
    - **Setup:** Attacker starts a listener (e.g., using `nc`, `pwncat`, Metasploit) on their machine; exploit payload on target tells it to connect back to attacker's IP and listener port.
- **[[Bind Shell]]**
    - **Mechanism:** A listener is started *on the compromised target machine*, binding to a specific port. The attacker then *connects* from their machine *to* the target's listener port.
    - **Use Case:** Less common due to firewalls often blocking incoming connections. Useful if outgoing connections from the target are blocked, but incoming are allowed, or for internal pivoting.
    - **Setup:** Exploit payload starts a listener (e.g., `nc -lp <port> -e /bin/bash`) on the target; attacker connects using `nc <target_ip> <port>`.
- **[[Web Shell]]**
    - **Mechanism:** A script (e.g., PHP, ASP, JSP) uploaded to a web server that accepts commands via HTTP requests (e.g., through URL parameters or POST data) and executes them on the server.
    - **Interaction:** Often semi-interactive or non-interactive (execute one command, see output). Can sometimes be upgraded to a fully interactive reverse/bind shell.
    - **Use Case:** Common result of exploiting web application vulnerabilities (e.g., file upload, RCE).

### Shell Payloads

Small scripts or commands used to establish these shell connections can be written in many languages (Python, Perl, Bash, PowerShell, PHP, etc.) depending on what the target system supports. 