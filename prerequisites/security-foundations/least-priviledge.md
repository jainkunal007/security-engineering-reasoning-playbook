# Least Privilege — Why “More Access” Is Usually the Problem

When people hear “least privilege,” they often think:
- “Give fewer permissions”
- “Lock everything down”
- “Security people are being restrictive”

That’s not what least privilege really means.

Least privilege is about **reducing the damage when something goes wrong**.

Because something *will* go wrong.

---

## What Does “Privilege” Mean?

In simple terms, privilege means:
- What actions something is allowed to perform
- What data it is allowed to access

Privileges exist everywhere:
- Users vs other users
- Users vs admins
- Services vs other services
- Applications vs databases

Every privilege is a form of trust.

---

## What Is Least Privilege? (Plain Meaning)

Least privilege means:
> “Give only the access that is needed — and nothing more.”

Not forever.  
Not for convenience.  
Only for what is required *right now*.

---

## Our Example System (Again)

We’ll continue using the notes application:
- Users create, read, and edit their own notes
- Users should not access others’ notes
- Admins may have extra capabilities

This simple system already shows why least privilege matters.

---

## Least Privilege for Users

In the notes app:
- A normal user should:
  - Read their own notes
  - Edit their own notes
- A normal user should **not**:
  - Read other users’ notes
  - Modify system settings
  - Access admin tools

If a normal user is given extra access “just in case”:
- Bugs become breaches
- Mistakes become incidents

---

## Least Privilege for Admins

Admins have powerful privileges.

Common mistakes:
- Using admin accounts for normal work
- Exposing admin APIs publicly
- Forgetting to add extra protections

If an admin account is compromised:
- The attacker gets everything

Least privilege means:
- Separating admin actions
- Protecting admin access more strongly
- Making admin actions rare and deliberate

---

## Least Privilege for Services

Applications often talk to other services:
- API → database
- Worker → storage
- App → logging system

A common mistake:
> “This service needs access, so let’s give it everything.”

In the notes app:
- The API service may need to read and write notes
- It does **not** need to:
  - Manage users
  - Change permissions
  - Access unrelated data

If one service is compromised, least privilege limits how far an attacker can go.

---

## Why Least Privilege Is Hard in Practice

Least privilege sounds simple.
It is not.

Common reasons it breaks:
- “We’ll restrict it later”
- “This is faster for now”
- “It’s internal, so it’s fine”
- “We don’t know exactly what it needs”

Over time:
- Permissions accumulate
- No one remembers why they were added
- Removing them feels risky

This is called **privilege creep**.

---

## Least Privilege and CIA

Least privilege protects:
- **Confidentiality** → limits data exposure
- **Integrity** → limits unauthorized changes
- **Availability** → limits blast radius of abuse

When least privilege fails, all three are at risk.

---

## Least Privilege in Interviews

Interviewers often ask:
- “Who should be allowed to do this?”
- “What permissions are required?”
- “What happens if this account is compromised?”

They are testing whether you think about:
- Damage containment
- Blast radius
- Realistic failure scenarios

You don’t need perfect answers.
You need **reasonable boundaries**.

---

## What Least Privilege Is NOT

Least privilege is not:
- Blocking all access
- Making systems unusable
- Saying “no” to everything

It is:
- Saying “only what’s needed”
- Revisiting decisions
- Reducing risk over time

---

## When You’re Ready to Move On

You are ready to continue if:
- You understand that access equals risk
- You can explain why extra permissions are dangerous
- You think about “what if this is compromised?”

Least privilege won’t prevent all incidents.
But it will limit how bad they become.

That’s why it matters so much.
