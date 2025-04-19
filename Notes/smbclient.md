# smbclient

`smbclient` is a command-line utility (part of the Samba suite) used to interact with [[SMB]] network shares, similar to an FTP client.

## Common Uses

*   Listing available shares on a server (`-L`)
*   Connecting to a share
*   Browsing directories (`ls`, `cd`)
*   Uploading/Downloading files (`put`, `get`)
*   Executing remote commands (less common)

## Key Options

*   `-L <host>`: List shares
*   `-N`: Suppress password prompt (for null/guest sessions)
*   `-U <username>`: Specify username
*   `//<server>/<share>`: Target server and share

## Example

After identifying an [[SMB]] service (e.g., via [[Nmap]]), `smbclient` can be used to list and interact with shares.

**1. Listing Shares (Anonymous/Null Session):**

```shell-session
Iskandeur@htb[/htb]$ smbclient -N -L \\\\10.129.42.253

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	users           Disk      
	IPC$            IPC       IPC Service (gs-svcscan server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available
```
This shows available shares (`print$`, `users`, `IPC$`). The `-N` suppresses the password prompt for a null session attempt.

**2. Connecting to a Share (Anonymous/Null Session - Fails):**

```shell-session
Iskandeur@htb[/htb]$ smbclient \\\\10.129.42.253\\users

Enter WORKGROUP\Iskandeur's password: 
Try "help" to get a list of possible commands.
smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*
smb: \> exit
```
Here, connecting anonymously (null session) failed (`NT_STATUS_ACCESS_DENIED`).

**3. Connecting to a Share (With Credentials):**

Let's try connecting with known credentials (`bob:Welcome1`).

```shell-session
Iskandeur@htb[/htb]$ smbclient -U bob \\\\10.129.42.253\\users

Enter WORKGROUP\bob's password: 
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Thu Feb 25 16:42:23 2021
  ..                                  D        0  Thu Feb 25 15:05:31 2021
  bob                                 D        0  Thu Feb 25 16:42:23 2021
		4062912 blocks of size 1024. 1332480 blocks available
smb: \> cd bob
smb: \bob\> ls
  .                                   D        0  Thu Feb 25 16:42:23 2021
  ..                                  D        0  Thu Feb 25 16:42:23 2021
  passwords.txt                       N      156  Thu Feb 25 16:42:23 2021
		4062912 blocks of size 1024. 1332480 blocks available
smb: \bob\> get passwords.txt 
getting file \bob\passwords.txt of size 156 as passwords.txt (0.3 KiloBytes/sec) (average 0.3 KiloBytes/sec)
smb: \bob\> exit
```
This time, using credentials allows access. We can navigate (`cd`), list files (`ls`), and download (`get`) the `passwords.txt` file. 