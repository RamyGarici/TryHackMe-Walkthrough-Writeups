# Vulnversity --- TryHackMe Write-Up

## Overview

**Room:** Vulnversity\
**Platform:** TryHackMe\
**Difficulty:** Easy

------------------------------------------------------------------------

## Reconnaissance

Initial scan using Nmap:

``` bash
nmap -sV MACHINE_IP
```


**Q: Scan the box; how many ports are open?**\
A: 6

**Q: What version of the squid proxy is running on the machine?**\
A: 4.10

**Q: How many ports will Nmap scan if the flag `-p-400` was used?**\
A: 400

**Q: What is the most likely operating system this machine is
running?**\
A: Ubuntu

**Q: What port is the web server running on?**\
A: 3333

**Q: What is the flag for enabling verbose mode using Nmap?**\
A: -v

------------------------------------------------------------------------

## Directory Enumeration

Directory brute-forcing using Gobuster:

``` bash
gobuster dir -u http://MACHINE_IP:3333 -w /usr/share/wordlists/dirbuster/directory-list-1.0.txt -t 50
```



**Q: What is the directory that has an upload form page?**\
A: /internal/

------------------------------------------------------------------------

## Web Server Compromise

The discovered `/internal/` directory contains a file upload form.


**Q: What common file type you'd want to upload to exploit the server is
blocked?**\
A: .php

**Q: What extension is allowed after running the above exercise?**\
A: .phtml

The server blocks `.php` files but allows `.phtml`, which is still
interpreted as PHP.

A reverse shell is uploaded using the allowed extension and executed
from the browser, resulting in a shell on the target machine.

------------------------------------------------------------------------

### Identify the Web Server User

``` bash
whoami
```

**Q: What is the name of the user who manages the webserver?**\
A: bill

------------------------------------------------------------------------

### User Flag

``` bash
cat /home/bill/user.txt
```

**Q: What is the user flag?**\
A: 8bd7992fbe8a6ad22a63361004cfcedb

------------------------------------------------------------------------

## Privilege Escalation

Search for SUID binaries:

``` bash
find / -perm -4000 2>/dev/null
```



**Q: On the system, search for all SUID files. Which file stands out?**\
A: /bin/systemctl

The `systemctl` binary can be abused to execute commands with elevated
privileges.

After exploiting the misconfiguration, root access is obtained.

------------------------------------------------------------------------

### Root Flag

``` bash
cat /root/root.txt
```

**Q: What is the root flag value?**\
A: a58ff8579f0a9270368d33a9966c7fd5

------------------------------------------------------------------------

