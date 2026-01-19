# The CIA Triad — In Practice (Not Definitions)

You may have heard of the CIA triad many times:
- Confidentiality
- Integrity
- Availability

Most people learn it as a definition.
Security engineers use it as a **decision-making lens**.

This document shows how CIA appears repeatedly across real systems — and why it keeps coming up in interviews and incidents.

---

## Why CIA Still Matters

CIA is not a checklist.
It is a way to ask one simple question:

> “What are we trying to protect, and how can it fail?”

Every security problem you’ll see maps to **at least one** of these three.

---

## Confidentiality (Who Can See This?)

Confidentiality is about **preventing unauthorized disclosure**.

### Common misunderstandings
- ❌ “Encryption means confidentiality is solved”
- ❌ “Only sensitive data needs confidentiality”

### In practice, confidentiality fails when:
- Secrets are logged
- Backups are exposed
- Debug endpoints leak data
- Access controls are too broad
- Metadata reveals sensitive information

### Examples
- HTTPS protects data *in transit*
- Encryption at rest protects against disk theft
- Access control protects against internal abuse

📌 **Key idea:**  
Confidentiality depends as much on *access decisions* as on cryptography.

---

## Integrity (Can This Be Changed?)

Integrity is about **preventing unauthorized modification**.

### Common misunderstandings
- ❌ “Integrity only means checksums”
- ❌ “If users are authenticated, integrity is guaranteed”

### In practice, integrity fails when:
- Authorization checks are missing
- Inputs are trusted too early
- Business logic can be abused
- One tenant can modify another tenant’s data

### Examples
- Authorization bugs
- Confused deputy problems
- Injection attacks
- Feature flag abuse

📌 **Key idea:**  
Most real-world breaches are **integrity failures**, not confidentiality failures.

---

## Availability (Can This Be Used When Needed?)

Availability is about **reliability under stress and attack**.

### Common misunderstandings
- ❌ “Availability is just uptime”
- ❌ “This is an ops problem, not security”

### In practice, availability fails when:
- Systems are easily abused
- Rate limiting is missing
- Dependencies fail unexpectedly
- Certificates expire
- Resource exhaustion is possible

### Examples
- DDoS attacks
- Brute-force login attempts
- Expired TLS certificates
- Unbounded API usage

📌 **Key idea:**  
Anything that can be abused can become an availability problem.

---

## CIA Is About Tradeoffs

You cannot maximize all three at the same time.

Examples:
- Strong authentication may reduce availability
- Aggressive rate limiting may impact usability
- Encryption can complicate recovery and debugging

Security engineers must **explain and justify tradeoffs**, not pretend they don’t exist.

---

## CIA in Real Systems

You’ll see CIA repeatedly in this repository:

- TLS → Confidentiality + Integrity
- Authentication → Integrity
- Authorization → Integrity
- Rate limiting → Availability
- Backups → Availability + Integrity
- Logging → Confidentiality tradeoffs

When reading future documents, ask:
> “Which part of CIA is this protecting?”

---

## CIA in Interviews

When you’re unsure how to answer a question, CIA is a safe anchor.

Example:
> “From a confidentiality perspective, I’d worry about…”  
> “From an integrity standpoint, the risk is…”  
> “Availability-wise, this could be abused by…”

This shows **structured thinking**, even if you don’t know every detail.

---

## What CIA Does NOT Do

CIA does **not**:
- Tell you how to implement controls
- Replace threat modeling
- Guarantee security

It helps you **frame the problem correctly**.

---

## When You’re Ready to Move On

You are ready to continue if:
- You can map common security issues to CIA
- You understand that most problems involve tradeoffs
- You can explain *why* a control exists, not just *what* it is

CIA will come up again — many times.

That’s intentional.
