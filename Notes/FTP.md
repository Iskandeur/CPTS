# FTP (File Transfer Protocol)

FTP is a standard network protocol used for transferring computer files between a client and server on a computer network.

## Key Concepts

*   Active vs Passive Mode
*   Authentication (Anonymous, User/Pass)
*   Common Commands (`ls`, `cd`, `get`, `put`)
*   Security Considerations (Plain text credentials)

## Tools

*   Command-line `ftp` client
*   FileZilla
*   [[Nmap]] scripts (`ftp-anon`, etc.)

## Example: Anonymous Login Interaction

After discovering an open FTP port (e.g., via [[Nmap]]) that allows anonymous login, we can connect using the command-line `ftp` utility.

```shell-session
Iskandeur@htb[/htb]$ ftp -p 10.129.42.253

Connected to 10.129.42.253.
220 (vsFTPd 3.0.3)
Name (10.129.42.253:user): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.

ftp> ls
227 Entering Passive Mode (10,129,42,253,158,60).
150 Here comes the directory listing.
drwxr-xr-x    2 ftp      ftp          4096 Feb 25 19:25 pub
226 Directory send OK.

ftp> cd pub
250 Directory successfully changed.

ftp> ls
227 Entering Passive Mode (10,129,42,253,182,129).
150 Here comes the directory listing.
-rw-r--r--    1 ftp      ftp            18 Feb 25 19:25 login.txt
226 Directory send OK.

ftp> get login.txt
local: login.txt remote: login.txt
227 Entering Passive Mode (10,129,42,253,181,53).
150 Opening BINARY mode data connection for login.txt (18 bytes).
226 Transfer complete.
18 bytes received in 0.00 secs (165.8314 kB/s)

ftp> exit
221 Goodbye.
```

In this example:
1. We connect to the FTP server.
2. Log in as `anonymous` (no password needed).
3. Use `ls` to list files/directories.
4. Use `cd` to change directory.
5. Use `get` to download a file (`login.txt`).
6. Inspect the downloaded file locally. 