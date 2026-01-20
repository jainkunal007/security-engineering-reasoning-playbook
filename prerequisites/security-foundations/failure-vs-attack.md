# Failure vs Attack — Why Security Issues Don’t Always Look Like Attacks

When people think about security problems, they usually imagine:
- Hackers breaking in
- Malicious intent
- Someone actively attacking the system

In reality, many serious security incidents do **not** start as attacks.

They start as **failures**.

Understanding the difference — and the connection — is critical in security.

---

## What Is a Failure?

A failure is when a system:
- Does not behave as intended
- Breaks under unexpected conditions
- Stops enforcing its own rules

Failures are often caused by:
- Misconfigurations
- Expired certificates
- Bugs
- Missing checks
- Incorrect assumptions

Failures are usually **not intentional**.

---

## What Is an Attack?

An attack is when someone:
- Intentionally tries to misuse the system
- Exploits a weakness
- Gains something they shouldn’t

Attacks require:
- Opportunity
- A weakness
- Access

Here’s the key idea:

> Failures often *create* the opportunity for attacks.

---

## Our Example System (Again)

We’ll continue using the same notes application:
- Users create, read, and edit notes
- Only the owner should have access
- The system should be available when needed

This system can fail — even without attackers.

---

## Example 1: Expired Certificate

Imagine:
- The TLS certificate expires
- Users can’t access the app
- The system becomes unavailable

This is a **failure**.

No attacker did anything.
But availability is broken.

Now imagine:
- Engineers temporarily disable HTTPS checks
- Traffic is sent unencrypted

Now the failure has **created a security risk**.

---

## Example 2: Missing Authorization Check

Imagine:
- A developer forgets an ownership check
- Users can access other users’ notes

This might be discovered accidentally.

That’s still a **security failure**.

But once someone notices it:
- It becomes an attack opportunity
- Confidentiality and integrity are now at risk

---

## Example 3: Debug Features Left Enabled

Imagine:
- Debug logging is enabled in production
- Logs contain note contents or user IDs

This was likely added for convenience.

No attack yet.

But if logs are accessible:
- Sensitive data leaks
- Attackers can use that information

A failure quietly turned into an attack surface.

---

## Why This Matters in Security

Security engineers don’t just think about:
- “How would someone attack this?”

They also think about:
- “What happens if this breaks?”
- “How could this failure be abused?”

Many real incidents are chains like this:
1. A small failure occurs  
2. Assumptions change  
3. An attacker notices  
4. Damage happens  

---

## Failure vs Attack and CIA

Failures and attacks both affect CIA:

- A failure can break **availability**
- A failure can weaken **confidentiality**
- A failure can bypass **integrity checks**

Attackers often wait for failures because:
- Systems are less defended
- Rules are temporarily relaxed
- Humans make rushed decisions

---

## Why Security Engineers Care About “Boring” Things

Things like:
- Certificate expiry
- Backups
- Configuration
- Defaults
- Error handling

These don’t sound exciting.
But they cause many real-world incidents.

Security is not only about stopping attackers.
It is also about **building systems that fail safely**.

---

## Failure vs Attack in Interviews

Interviewers may ask:
- “What happens if this fails?”
- “What if this dependency is down?”
- “What if this config is wrong?”

They are testing whether you:
- Think beyond active attackers
- Understand real-world conditions
- Can reason about risk under failure

Good answers often start with:
> “If this fails, the risk is…”

---

## What This Concept Is NOT

This does not mean:
- Every failure is a security incident
- Engineers should fear mistakes

It means:
- Failures change the threat landscape
- Systems should be designed with failure in mind

---

## When You’re Ready to Move On

You are ready to continue if:
- You understand that security issues don’t always start as attacks
- You can think about how failures change risk
- You no longer assume systems behave perfectly

This mindset will help you:
- Design safer systems
- Debug incidents
- Answer interview questions realistically

Security is as much about handling failure as it is about stopping attacks.
