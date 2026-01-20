# The Attacker Mindset — Thinking Beyond “Normal Use”

When people start learning security, they often think:
- “Users won’t try that”
- “Why would anyone do this?”
- “This is an edge case”

Attackers live in edge cases.

Understanding security starts with understanding **how attackers think** — not because attackers are smarter, but because they look at systems differently.

---

## Attackers Are Not Always Hackers

A common misconception is that attackers are:
- Highly skilled
- Deeply technical
- Using advanced tools

In reality, attackers can be:
- Curious users
- Script kiddies
- Automated bots
- Disgruntled insiders
- Opportunistic outsiders

Many attacks are:
- Simple
- Repetitive
- Automated

Security breaks more often due to **assumptions**, not sophistication.

---

## How Attackers Look at Systems

Engineers usually ask:
- “How is this supposed to work?”

Attackers ask:
- “What happens if I don’t follow the rules?”
- “What if I repeat this 10,000 times?”
- “What if I change this one value?”
- “What if I use this feature in a weird way?”

This difference in thinking is the attacker mindset.

---

## Our Example System (Again)

We’ll continue with the same notes application:
- Users create, read, and edit notes
- Users should only access their own notes

An attacker does not care about the intended design.
They care about what the system *allows*.

---

## Attackers Love Defaults

Defaults are designed for convenience, not safety.

Examples:
- Default permissions
- Default configurations
- Default limits
- Default error messages

In the notes app:
- What happens if no rate limit is set?
- What happens if error messages reveal note IDs?
- What happens if ownership checks are missing by default?

Attackers look for what was **not explicitly protected**.

---

## Attackers Abuse Normal Features

Many attacks don’t look like attacks.

They look like:
- Normal requests
- Normal actions
- Normal users — just at scale or with intent

Examples in the notes app:
- Repeatedly guessing note IDs
- Creating thousands of notes
- Rapidly calling the same endpoint
- Using features in unintended combinations

Security issues often come from **abuse**, not exploits.

---

## Attackers Think in Scale

A single request may be harmless.
A million requests are not.

Attackers ask:
- “What happens if I automate this?”
- “What happens if I run this overnight?”
- “What happens if I do this from many IPs?”

Many availability and abuse problems come from:
- Missing limits
- Missing monitoring
- Missing assumptions about scale

---

## Attackers Chain Small Issues

Attackers rarely rely on one big bug.

They chain:
- Small information leaks
- Minor validation gaps
- Weak assumptions

Example chain:
1. Error messages reveal note IDs  
2. Note IDs are predictable  
3. Ownership checks are missing  

Each issue alone seems small.
Together, they break security.

---

## Attackers Don’t Care About Intent

Attackers do not care that:
- “This wasn’t meant to be public”
- “This is an internal feature”
- “This is only for admins”

They care only about:
> “Can I reach it?”

If something is reachable, it is attackable.

---

## Attacker Mindset and CIA

Attackers naturally target:
- **Confidentiality** → Can I see data?
- **Integrity** → Can I change data?
- **Availability** → Can I disrupt service?

They don’t use these terms — but their actions map directly to them.

---

## Attacker Mindset in Interviews

Interviewers often test this indirectly.

They may ask:
- “How could this be abused?”
- “What would an attacker try first?”
- “What assumptions are risky?”

They want to see if you can step outside the “happy path”.

You don’t need to sound paranoid.
You need to sound **aware**.

---

## What the Attacker Mindset Is NOT

The attacker mindset is not:
- Distrusting everyone
- Assuming all users are malicious
- Designing for worst-case scenarios only

It is:
- Questioning assumptions
- Thinking about misuse
- Designing reasonable safeguards

---

## When You’re Ready to Move On

You are ready to continue if:
- You can think of at least one way to misuse a simple feature
- You understand that attackers abuse normal behavior
- You no longer assume systems are used as intended

This mindset will appear everywhere:
- Threat modeling
- Code reviews
- Interviews
- Real incidents

Once you see systems this way, you won’t unsee it.
