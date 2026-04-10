# IDOR --- TryHackMe

**Platform:** TryHackMe\
**Type:** Room\
**Difficulty:** Easy\
**Name:** IDOR

------------------------------------------------------------------------

## Questions & Answers (TryHackMe)

### IDOR

Q: What does IDOR stand for?\
A: Insecure Direct Object Reference

------------------------------------------------------------------------

### An IDOR Example

Q: What is the Flag from the IDOR example website?\
A: THM{IDOR-VULN-FOUND}

------------------------------------------------------------------------

### Finding IDORs in Encoded IDs

Q: What is a common type of encoding used by websites?\
A: base64

------------------------------------------------------------------------

### Finding IDORs in Hashed IDs

Q: What is a common algorithm used for hashing IDs?\
A: md5

------------------------------------------------------------------------

### Finding IDORs in Unpredictable IDs

Q: What is the minimum number of accounts you need to create to check
for IDORs between accounts?\
A: 2

------------------------------------------------------------------------

### A Practical IDOR Example

Q: What is the username for user id 1?\
A: adam84

Q: What is the email address for user id 3?\
A: j@fakemail.thm

------------------------------------------------------------------------

## Notes

### IDOR

-   IDOR is a Broken Access Control vulnerability.
-   Occurs when an application exposes direct object references (IDs)
    without proper authorization checks.
-   Allows attackers to access data belonging to other users.

------------------------------------------------------------------------

### Common Testing Areas

-   URLs (e.g., ?id=1)
-   API endpoints
-   Hidden form fields
-   JSON responses

------------------------------------------------------------------------

### Techniques

-   Incrementing/decrementing IDs
-   Switching IDs between accounts
-   Testing with multiple users
-   Decoding encoded values (Base64)
-   Cracking hashes (MD5)

------------------------------------------------------------------------

### Tools

-   Browser DevTools (Network tab)
-   Burp Suite
-   CrackStation

------------------------------------------------------------------------

### Detection

-   If you can access another user's data by modifying an ID → IDOR
    vulnerability confirmed.
