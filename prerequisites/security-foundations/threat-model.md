# Threat Modeling — Learning to Ask “What Could Go Wrong?”

When beginners hear the term “threat modeling,” it often sounds complex and formal.
It feels like something only senior engineers do.

In reality, threat modeling is just **structured thinking** about risk.

It is the habit of slowing down and asking:
> “If someone uses this system in a bad or unexpected way, what could go wrong?”

This document teaches that habit step by step.

---

## Why Threat Modeling Exists

When building systems, engineers usually focus on:
- How things should work
- Normal users
- Happy paths

Attackers focus on:
- Edge cases
- Assumptions
- Misuse

Threat modeling exists to **force us to think beyond happy paths** — before attackers do.

---

## Threat Modeling Is Not About Being Perfect

Threat modeling does **not** mean:
- Predicting every attack
- Knowing every vulnerability
- Designing perfect security

It means:
- Identifying obvious risks early
- Reducing unnecessary exposure
- Making better design decisions

Even simple thinking is better than none.

---

## Our Example System (We’ll Go Slow)

We’ll use the same system again:

A notes application where:
- Users can create notes
- Users can read their own notes
- Users can edit their own notes
- Users should not access other users’ notes

We’ll threat model **one feature**:
> “View a note”

---

## Step 1: Identify the Assets

First, ask:
> “What are we trying to protect?”

For the “view note” feature, assets include:
- The content of the note
- User identity
- Ownership information
- Availability of the app

If losing or corrupting something would be bad, it’s an asset.

---

## Step 2: Identify the Actors

Next, ask:
> “Who interacts with this feature?”

Actors include:
- The note owner
- Other authenticated users
- Unauthenticated users
- Automated scripts
- Internal services

Not all actors are malicious — but any actor can behave unexpectedly.

---

## Step 3: Identify Entry Points

Now ask:
> “How can someone interact with this feature?”

Entry points might be:
- A browser request
- A mobile app request
- An API endpoint like `/notes/{id}`
- Internal service calls

Every entry point is a place where things can go wrong.

---

## Step 4: Identify Assumptions (Very Important)

This is where most security bugs hide.

Common assumptions might be:
- “Users will only request their own note IDs”
- “The frontend hides other notes”
- “Only authenticated users can call this endpoint”

Threat modeling means asking:
> “What if this assumption is false?”

---

## Step 5: Ask “What Could Go Wrong?”

Now combine everything.

Examples:
- What if a user changes the note ID in the request?
- What if note IDs are predictable?
- What if a user guesses someone else’s note ID?
- What if requests are automated at scale?

At this stage:
- You don’t need attack names
- You don’t need frameworks
- Plain language is enough

---

## Step 6: Map Risks to CIA

For each risk, ask:

- Does this leak data? → Confidentiality
- Does this allow unauthorized changes? → Integrity
- Does this affect system usability? → Availability

Example:
- Accessing someone else’s note → Confidentiality failure
- Editing someone else’s note → Integrity failure
- Flooding the endpoint → Availability failure

This keeps your thinking structured.

---

## Step 7: Think About Mitigations

Now ask:
> “What would reduce this risk?”

Examples:
- Ownership checks on the server
- Rate limiting
- Logging suspicious access
- Monitoring unusual patterns

You are not designing perfect security.
You are reducing obvious risk.

---

## Where STRIDE Fits (Optional Vocabulary)

You may hear about a framework called **STRIDE**.

STRIDE is just a way to **name common types of problems**:

- **S**poofing → pretending to be someone else
- **T**ampering → changing data you shouldn’t
- **R**epudiation → denying actions
- **I**nformation disclosure → leaking data
- **D**enial of service → making systems unavailable
- **E**levation of privilege → gaining more power

Important:
> STRIDE does not add new ideas — it labels ones you already thought about.

For example:
- Accessing another user’s note → Information disclosure
- Editing another user’s note → Tampering
- Flooding the API → Denial of service

If STRIDE helps you organize thoughts, use it.
If not, plain language is enough.

---

## Threat Modeling Is Ongoing

Threat modeling should happen:
- When features are added
- When systems change
- When assumptions change

Many breaches happen because:
- Threat models were never updated
- Systems evolved, but thinking didn’t

---

## Threat Modeling in Interviews

Interviewers often ask:
- “What could go wrong here?”
- “What would you worry about?”
- “What would you check first?”

They are not testing frameworks.
They are testing **how you think**.

Clear, structured reasoning matters more than buzzwords.

---

## When You’re Ready to Move On

You are ready to continue if:
- You can threat model a simple feature
- You can question assumptions
- You can explain risks in plain language

Threat modeling is not about fear.
It is about awareness.

That awareness is a core security skill.
