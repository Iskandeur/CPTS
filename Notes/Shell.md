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
    - [[Powershell]] (Modern, more powerful object-oriented shell and scripting language)

## Use in Penetration Testing ("Getting a Shell")

In pentesting, "getting a shell" means gaining interactive command-line access to a compromised target system.

### Methods of Obtaining a Shell

- Exploiting a network service vulnerability.
- Exploiting a web application vulnerability (e.g., Remote Code Execution - RCE).
- Obtaining valid credentials and logging in remotely (e.g., via [[SSH]]).
- Uploading and executing malicious code (e.g., via file upload vulnerability).

### Types of Shell Connections

- **[[Reverse Shell]]**
    - **Concept:** Target machine connects *back* to the attacker machine.
    - **Pros:** Often bypasses firewalls (target initiates outbound connection, which is usually less restricted).
    - **Cons:** Attacker needs a listening port open and reachable from the target.
    - **Setup:** Attacker starts a listener (e.g., using [[Netcat|nc]], `pwncat`, Metasploit) on their machine; exploit payload on target tells it to connect back to attacker's IP and listener port.
- **[[Bind Shell]]**
    - **Concept:** Attacker connects *to* a listener opened on the target machine.
    - **Pros:** Simpler setup on the target.
    - **Cons:** Target machine needs an open port accessible *by* the attacker (often blocked by firewalls).
    - **Setup:** Exploit payload starts a listener (e.g., `nc -lp <port> -e /bin/bash`) on the target; attacker connects using [[Netcat|nc]] `<target_ip> <port>`.
- **[[Web Shell]]**
    - **Mechanism:** A script (e.g., PHP, ASP, JSP) uploaded to a web server that accepts commands via HTTP requests (e.g., through URL parameters or POST data) and executes them on the server.
    - **Interaction:** Often semi-interactive or non-interactive (execute one command, see output). Can sometimes be upgraded to a fully interactive reverse/bind shell.
    - **Use Case:** Common result of exploiting web application vulnerabilities (e.g., file upload, RCE).

### Shell Payloads

Small scripts or commands used to establish these shell connections can be written in many languages (Python, Perl, Bash, [[Powershell]], PHP, etc.) depending on what the target system supports. 