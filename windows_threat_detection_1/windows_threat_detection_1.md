# Windows Threat Detection 1 — TryHackMe

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** Windows Threat Detection 1  

---

## Questions & Answers

### Intro to Initial Access

Q: Which MITRE technique ID describes Initial Access via a vulnerable mail server?  
A: T1190  

Q: Which Initial Access method relies on a user opening a malicious email attachment?  
A: Phishing  

---

### Initial Access via RDP

Q: Which user seems to be most actively brute-forced by botnets?  
A: Administrator  

Q: Which IP managed to breach the host via RDP (Logon Type 10)?  
A: 203.205.34.107  

Q: Can you get the real Workstation Name (hostname) of the threat actor?  
A: DESKTOP-QNBC4UU  

---

### Initial Access via Phishing

Q: Run the www.skype.com file from the Phishing Case 1 folder, which flag do you get?  
A: THM{misleading_extension}  

Q: From which URL does the malicious LNK download the next stage malware?  
A: http://wp16.hqywlqpa.thm:8000/cgi-bin/f  

Q: What is the name of the double-extension file you see there?  
A: best-cat.jpg.exe  

---

### Continuing Phishing Topic

Q: Which file did the user download via the web browser?  
A: C:\\Users\\Administrator\\Downloads\\top-cats.zip  

Q: In which folder did the user unarchive the suspicious file?  
A: C:\\Users\\Administrator\\Pictures  

Q: What is the process ID of the launched phishing malware?  
A: 5484  

Q: Which malicious domain did the malware try to connect to?  
A: rjj.store  

---

### USB Malware Propagation

Q: Which USB file was launched by the user?  
A: E:\\Open Sandisk 4GB USB.exe  

Q: Which suspicious file did the malware drop to the disk?  
A: C:\\Users\\Public\\Documents\\winupdate.exe  

Q: To which other USB did the malware propagate?  
A: F:  

---

## Notes

### Initial Access

Initial Access:
first stage of an attack where the threat actor gains access to the target system  

---

### Exposed Services

T1133 / External Remote Services:
threat actors search for exposed RDP, VNC, or SSH services with weak passwords  

T1190 / Exploit Public-Facing Application:
attackers exploit vulnerable or misconfigured web applications/services  

---

### User-Driven Methods

T1566 / Phishing:
users are tricked into opening malicious attachments or links  

T1091 / Removable Media:
malware spreads through infected USB devices  

---

### Initial Access via RDP

Typical attack flow:
- network scan  
- RDP brute force  
- successful login  
- further malicious actions  

Indicators:
- many failed logons  
- Logon Type 10 events  
- repeated authentication attempts against Administrator account  

---

### Phishing

Common phishing techniques:
- misleading file extensions  
- malicious LNK shortcuts  
- double-extension executables  

Examples:
- www.skype.com.exe  
- best-cat.jpg.exe  

Malicious LNK:
downloads next-stage malware from external URL  

---

### Malware Behaviour

Observed actions:
- downloaded ZIP archive  
- extracted suspicious files  
- launched malware process  
- connected to malicious domain  

Indicators of compromise:
- suspicious domains  
- unexpected processes  
- files dropped in public directories  

---

### USB Propagation

Malware can:
- execute from removable media  
- copy itself to other USB devices  
- use fake executable names to trick users  

Example:
Open Sandisk 4GB USB.exe  

Dropped payload:
C:\\Users\\Public\\Documents\\winupdate.exe  
