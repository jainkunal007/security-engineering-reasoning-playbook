# The CIA Triad — How Security Engineers Reduce Chaos

When people first start learning security, everything feels overwhelming.

There are:
- Vulnerabilities
- Attacks
- Protocols
- Tools
- Frameworks

It feels like you’re supposed to worry about *everything*.

Security engineers needed a way to simplify this chaos.

That’s where the CIA triad comes from.

Not as definitions to memorize — but as a way to ask:
“What could go wrong here?”

---

## Think of CIA as Three Questions

Every system you will ever look at can fail in only three fundamental ways:

1. Can someone see something they shouldn’t? (Confidentiality)
2. Can someone change something they shouldn’t? (Integrity)
3. Can someone stop others from using it? (Availability)

That’s it.

Every security incident you read about maps back to one (or more) of these.

---

## A Simple System We’ll Reuse

Imagine a very simple application:
- You can create notes
- Only you should be able to read them
- Only you should be able to edit them
- You should be able to access them when needed

We’ll use this system to understand CIA.

---

## Confidentiality — “Who Can See This?”

Confidentiality is about preventing **unauthorized access to information**.

In o
