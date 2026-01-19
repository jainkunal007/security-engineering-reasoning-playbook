# Trust Boundaries — Where Security Actually Breaks

When systems fail, they rarely fail randomly.

Most security failures happen at the same places again and again:
**where trust changes**.

These places are called **trust boundaries**.

If you understand trust boundaries, you understand where to look first in any system.

---

## What Is a Trust Boundary?

A trust boundary is a point in a system where:
- The level of trust changes
- Assumptions about behavior change
- Security guarantees must be re-evaluated

In simple terms:
> A trust boundary is where you stop trusting something as much as you did before.

Every time data crosses a trust boundary, the system is making an assumption.

Security problems happen when those assumptions are wrong.

---

## Our Running Example

We’ll continue using the same simple system:
- A notes application
- Users can create, read, and edit personal notes
- Only the owner should have access

This system has multiple trust boundaries — even though it looks simple.

---

## The Client ↔ Server Trust Boundary

One of the most important trust boundaries is between:
- The **client** (browser, mobile app)
- The **server** (backend)

The client is **not trusted**.

Even if:
- The user is logged in
- The UI hides certain buttons
- The request “looks normal”

An attacker can:
- Modify requests
- Replay requests
- Forge requests

If the server assumes the client behaves correctly, security breaks.

📌 **Key idea:**  
Never trust the client — trust the server’s checks.

---

## The User ↔ User Trust Boundary

In the notes app:
- User A should not access User B’s notes

This creates a trust boundary between users.

Security failures happen when:
- The system checks “is the user logged in?”
- But forgets to check “does this user own this note?”

This leads to:
- Broken access control
- Horizontal privilege escalation

📌 **Key idea:**  
Authentication does not imply authorization.

---

## The User ↔ Admin Trust Boundary

Admins are more trusted than regular users.

This boundary is dangerous.

If admin functionality:
- Is exposed accidentally
- Is not properly protected
- Can be triggered through normal user actions

Then:
- A small bug becomes a big breach

Many real incidents happen because admin tools:
- Reuse user APIs
- Skip validation
- Assume trusted input

📌 **Key idea:**  
Higher trust requires stronger protection.

---

## The Service ↔ Service Trust Boundary

Modern systems rarely have a single server.

Your notes app might have:
- An API service
- A database
- A background worker
- A logging service

These services communicate with each other.

Common dangerous assumptions:
- “This service is internal, so it’s safe”
- “Only trusted services can call this API”

If one service is compromised, these assumptions collapse.

📌 **Key idea:**  
Internal does not mean trusted.

---

## Trust Boundaries and Data Validation

Every time data crosses a trust boundary:
- It must be validated
- Its permissions must be checked
- Its intent must be verified

Skipping validation because:
- “It already passed earlier”
- “It came from a trusted source”

is a common cause of vulnerabilities.

---

## Trust Boundaries Change Over Time

Trust boundaries are not fixed.

They change when:
- Systems evolve
- Features are added
- Services are split
- New integrations are introduced

Security often breaks because:
- Old assumptions remain
- New boundaries are not recognized

📌 **Key idea:**  
Security reviews must be repeated when architecture changes.

---

## Trust Boundaries and CIA

Trust boundaries connect directly to CIA:
- Confidentiality fails when boundaries leak data
- Integrity fails when boundaries allow unauthorized changes
- Availability fails when boundaries allow abuse

When analyzing a system, ask:
> “What trust boundary is being crossed here?”

---

## Trust Boundaries in Interviews

Interviewers often ask questions that are really about trust boundaries.

Examples:
- “What would you validate here?”
- “Where would you enforce authorization?”
- “What assumptions are dangerous?”

If you can clearly explain trust boundaries, you can answer these questions confidently.

---

## When You’re Ready to Move On

You are ready to continue if:
- You can identify trust boundaries in a simple system
- You understand why assumptions are dangerous
- You know that most security bugs live at boundaries

From now on, you should start seeing trust boundaries everywhere.

That’s a good sign.
