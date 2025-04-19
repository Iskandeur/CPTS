#new 
We can connect to TCP port 22 with `netcat`:

Basic Tools

```shell-session
Iskandeur@htb[/htb]$ netcat 10.10.10.10 22

SSH-2.0-OpenSSH_8.4p1 Debian-3
```

As we can see, port 22 sent us its banner, stating that `SSH` is running on it. This technique is called `Banner Grabbing`, and can help identify what service is running on a particular port.

Lookup, maybe it's a technique also used by [[Nmap]] ?