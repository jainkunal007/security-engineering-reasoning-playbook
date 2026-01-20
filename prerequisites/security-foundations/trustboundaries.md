# Trust Boundaries — Understanding Where Security Problems Begin

When people imagine hacking, they often imagine something complex:
- Advanced tools
- Deep technical tricks
- Highly skilled attackers

In reality, most security problems start much earlier and much simpler.

They start when a system **trusts something it should not**.

This document explains what that means.

---

## First: What Does “Trust” Mean in Security?

In everyday life, trust means:
- “I believe this person will behave correctly”

In security, trust means:
- “I assume this thing will not try to break my system”

That thing could be:
- A user
- A browser
- Another service
- A piece of data

Every time a system makes an assumption like that, it is trusting something.

---

## What Is a Trust Boundary? (Plain Definition)

A **trust boundary** is a place in a system where:
- Something untrusted meets something trusted
- An assumption is made
- A decision must be enforced

In simple words:

> A trust boundary is the line where you must stop and say:  
> “I cannot assume this is safe anymore.”

Security problems happen when systems **forget to stop and check**.

---

## A Simple System We’ll Use

We’ll use the same example throughout this document.

Imagine a very simple notes application:
- Users can create notes
- Users can read their own notes
- Users can edit their own notes
- Users should not see or edit other users’ notes

This system looks simple, but it already contains many trust boundaries.

---

## Trust Boundary #1: The User and the Application

Let’s start with the user.

The application **cannot trust the user**.

Why?
Because users:
- Can modify requests
- Can send unexpected inputs
- Can intentionally try to break rules

Even if:
- The user is logged in
- The UI hides buttons
- The app “looks safe”

The backend must assume:
> “This user might try something unexpected.”

This is a trust boundary.

📌 **Important idea:**  
The system must *verify*, not *assume*.

---

## Trust Boundary #2: Browser (Client) vs Server

Another very important boundary exists between:
- The browser (client)
- The backend server

The browser:
- Is controlled by the user
- Can be modified
- Can send fake or altered requests

The server:
- Enforces rules
- Protects data
- Makes final decisions

If the server trusts the browser to behave correctly, security breaks.

Example:
- The browser says: “Give me note ID 123”
- The server must check: “Does this user own note 123?”

If the server does not check, anyone can access anything.

📌 **This is why you’ll hear:**  
“Never trust the client.”

---

## Trust Boundary #3: User vs Other Users

In our notes app:
- User A should not access User B’s notes

This creates a boundary between users.

A common mistake:
- The system checks only “Is the user logged in?”
- But forgets to check “Is this the right user?”

Result:
- User A can read or edit User B’s notes

Nothing fancy happened.
No encryption was broken.
No hacking tools were used.

The system simply trusted the wrong thing.

This is one of the most common security bugs.

---

## Trust Boundary #4: Normal User vs Admin

Admins are more powerful than normal users.

This creates a **high-risk trust boundary**.

Admin features often:
- Skip checks
- Assume trusted input
- Have more access

If a normal user can:
- Trigger admin functionality
- Reuse admin APIs
- Access admin endpoints

Then a small bug becomes a serious breach.

📌 **Key idea:**  
The more power something has, the more carefully it must be protected.

---

## Trust Boundary #5: One Service vs Another Service

Modern applications are made of many services.

For example:
- API service
- Database
- Background worker
- Logging service

A common dangerous assumption is:
> “This is an internal service, so it’s safe.”

But if one service is compromised:
- Attackers can move to others
- Internal trust collapses

This is why “internal” does not mean “secure”.

---

## Why Trust Boundaries Cause Most Security Bugs

Security bugs happen when:
- Assumptions are wrong
- Checks are missing
- Validation is skipped
- Systems change but trust rules don’t

Many breaches are not caused by attackers being clever.
They are caused by systems being **too trusting**.

---

## How Trust Boundaries Relate to CIA

Trust boundaries directly affect:
- **Confidentiality** → data leaks across boundaries
- **Integrity** → unauthorized changes cross boundaries
- **Availability** → abuse crosses boundaries

When you analyze a system, ask:
> “Where does trust change here?”

That question alone will reveal most risks.

---

## Why Interviewers Care About This

Interview questions often sound like:
- “What would you validate?”
- “Where would you put checks?”
- “What assumptions are dangerous?”

They are really asking:
> “Do you understand trust boundaries?”

If you do, you already know how to start answering.

---

## When You’re Ready to Move On

You are ready to continue if:
- You can explain what a trust boundary is in your own words
- You can identify at least one boundary in a simple app
- You understand that assumptions are risky

From now on, try to notice:
- Where trust changes
- Where checks should exist
- Where things could go wrong

That’s how security thinking begins.
