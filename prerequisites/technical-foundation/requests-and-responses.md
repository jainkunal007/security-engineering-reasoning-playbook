# Requests and Responses — What Computers Actually Say to Each Other

In the previous document, we learned one key idea:

> The web is a conversation between computers.

Now we’ll slow that conversation down and look at:
- What is being sent
- What is being received
- Why this matters for security

No jargon yet — just clarity.

---

## A Conversation Needs Messages

When two people talk:
- One person asks something
- The other responds

Computers do the same thing.

On the web:
- The **client** sends a **request**
- The **server** sends a **response**

Everything you see on a website comes from this pattern.

---

## What Is a Request? (Plain Meaning)

A **request** is simply:
> “I am asking for something.”

When you:
- Open a page
- Click a button
- Submit a form

Your browser sends a request to the server.

That request describes:
- What you want
- Where you want it from

---

## A Very Simple Request Example

Imagine this message sent to a server:
I want to see note number 123


That’s the idea of a request.

In reality, computers send this in a structured format, but conceptually:
- It is still just asking for something

Important:
> A request does NOT automatically mean you are allowed to get it.

---

## What Is a Response? (Plain Meaning)

A **response** is the server’s reply.

It can say:
- “Yes, here it is”
- “No, you are not allowed”
- “Something went wrong”

The server always decides what response to send.

---

## A Very Simple Response Example

The server might respond with:

- “Here is note 123”
- “You are not logged in”
- “You are not allowed to see this note”

This decision is where **security lives**.

---

## Requests Do Not Contain Trust

This is a very important idea.

A request can say anything:
- “I am user Alice”
- “I own note 123”
- “I am an admin”

But the server must assume:
> “This could be a lie.”

Requests are **claims**, not truth.

---

## Why This Matters for Security

If a server believes requests blindly:
- Users can access other users’ data
- Users can perform actions they shouldn’t
- Systems break easily

Security exists to:
- Verify requests
- Check permissions
- Decide what is allowed

---

## Requests Can Be Repeated

Another important idea:
> Requests can be sent again and again.

A user can:
- Refresh a page
- Click a button repeatedly
- Automate requests with scripts

So the server must think:
- “What if this happens many times?”
- “What if this happens very fast?”

This is where availability problems start.

---

## Requests Can Be Changed

Requests are not fixed.

Attackers can:
- Change numbers
- Change values
- Add extra data
- Remove data

For example:
- Change note ID from 123 to 124
- Repeat requests automatically

The server must never assume:
> “The request will look reasonable.”

---

## Responses Can Leak Information

Even responses matter for security.

For example:
- Different error messages
- Different response times
- Different behavior

Attackers observe responses to learn:
- What exists
- What is protected
- What is misconfigured

So responses must be designed carefully.

---

## One Pattern to Remember

Always think in this pattern:
Request → Server Decision → Response


Security happens in the **server decision**.

---

## What We Are Still Not Covering

We still have not talked about:
- HTTP
- URLs
- Cookies
- Login
- Sessions

That’s intentional.

Right now, you only need to understand:
> Requests ask. Servers decide. Responses answer.

---

## When You’re Ready to Move On

You are ready to continue if:
- You understand what a request is
- You understand what a response is
- You know requests can lie, repeat, and change

In the next document, we’ll answer the question:
> “How does the server remember who you are?”


