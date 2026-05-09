# Principles of Security — TryHackMe

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** Principles of Security  

---

## Questions & Answers

### CIA Triad

Q: What element of the CIA triad ensures that data cannot be altered by unauthorised people?  
A: Integrity  

Q: What element of the CIA triad ensures that data is available?  
A: Availability  

Q: What element of the CIA triad ensures that data is only accessed by authorised people?  
A: Confidentiality  

---

### Principles of Privileges

Q: What does the acronym "PIM" stand for?  
A: Privileged Identity Management  

Q: What does the acronym "PAM" stand for?  
A: Privileged Access Management  

Q: If you wanted to manage the privileges a system access role had, what methodology would you use?  
A: PAM  

Q: If you wanted to create a system role that is based on a user's role/responsibilities within an organisation, what methodology is this?  
A: PIM  

---

### Security Models Continued

Q: What is the name of the model that uses the rule "can't read up, can read down"?  
A: The Bell-LaPadula Model  

Q: What is the name of the model that uses the rule "can read up, can't read down"?  
A: The Biba Model  

Q: If you were military, what security model would you use?  
A: The Bell-LaPadula Model  

Q: If you were a software developer, what security model would the company perhaps use?  
A: The Biba Model  

---

### Threat Modelling & Incident Response

Q: What model outlines "Spoofing"?  
A: STRIDE  

Q: What does the acronym "IR" stand for?  
A: Incident Response  

Q: You are tasked with adding measures to improve the integrity of data. What STRIDE principle is this?  
A: Tampering  

Q: An attacker has penetrated your organisation and stolen data. It is your task to return the organisation to business as usual. What incident response stage is this?  
A: Recovery  

---

## Notes

### CIA Triad

CIA triad:
information security model used when creating security policies  

3 sections:
- confidentiality  
- integrity  
- availability  

Confidentiality:
protects data from unauthorised access and misuse  

Integrity:
ensures information stays accurate and consistent unless authorised changes are made  

Availability:
data must be accessible and available to authorised users when needed  

---

### Principles of Privileges

Access levels depend on:
- the user's role/function in the organisation  
- the sensitivity of the information  

PIM:
Privileged Identity Management  
maps organisational roles to system access roles  

PAM:
Privileged Access Management  
manages what privileges/access a role has  

---

### Security Models

#### Bell-LaPadula Model

used for confidentiality  

rule:
- no read up  
- no write down  

advantages:
- simple to implement  
- works well with real-world hierarchies  

disadvantages:
- users may still know an object's existence  
- relies heavily on trust  

---

#### Biba Model

used for integrity  

rule:
- no write up  
- no read down  

advantages:
- simple implementation  
- improves integrity  

disadvantages:
- many access levels  
- can slow business operations  

example:
doctor may not be able to read nurse notes  

---

### Threat Modelling

Threat modelling:
process of reviewing, improving, and testing security controls in an organisation  

main principles:
- preparation  
- identification  
- mitigations  
- review  

effective threat model includes:
- threat intelligence  
- asset identification  
- mitigation capabilities  
- risk assessment  

---

### STRIDE Framework

STRIDE:
- Spoofing  
- Tampering  
- Repudiation  
- Information Disclosure  
- Denial of Service  
- Elevation of Privilege  

Spoofing:
pretending to be another user/system  

Tampering:
modifying data or systems  

Repudiation:
lack of logging/accountability  

Information Disclosure:
exposing sensitive data  

Denial of Service:
making systems/resources unavailable  

Elevation of Privilege:
gaining higher permissions than intended  

---

### Incident Response

Security breach = incident  

Incidents classified by:
- urgency  
- impact  

Handled by:
CSIRT (Computer Security Incident Response Team)  

IR stages:
- preparation  
- identification  
- containment  
- eradication  
- recovery  
- lessons learned  
