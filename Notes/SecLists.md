[SecLists](https://github.com/danielmiessler/SecLists) is a collection of multiple types of lists used during security assessments, collected in one place. It includes usernames, passwords, URLs, sensitive data patterns, fuzzing payloads, web shells, and more.

It is commonly used for tasks like [[Web Enumeration]] (directory/file discovery), [[Password Cracking]], and [[Fuzzing]].

## Installation

There are multiple ways to obtain SecLists:

**1. Git Clone (Recommended for latest version):**

```shell-session
Iskandeur@htb[/htb]$ git clone https://github.com/danielmiessler/SecLists
```

**2. Package Manager (e.g., apt on Debian/Ubuntu):**

_(Note: Package manager versions might be slightly older)_ 
```shell-session
Iskandeur@htb[/htb]$ sudo apt update && sudo apt install seclists -y
```
