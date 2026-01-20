# Web Basics for Security — Understanding How the Web Actually Works

Most modern security roles deal with web systems.

If you understand how the web works at a basic level,
security concepts like authentication, sessions, TLS, and APIs will make sense.

This document explains **just enough web basics** to reason about security —
no frontend frameworks, no deep protocol details.

---

## What “The Web” Really Is

At its core, the web is simple:

- A **client** (browser, mobile app) sends a request
- A **server** receives the request
- The server sends back a response

Everything else builds on top of this.

Security exists because:
> Clients and servers do not automatically trust each other.

---

## The Client–Server Model

### The Client
- Usually a browser or mobile app
- Controlled by the user
- Can be modified
- Can send any request it wants

### The Server
- Runs backend code
- Enforces rules
- Protects data
- Makes final decisions

📌 **Security rule:**  
Never trust the client to enforce security.

---

## What Is an HTTP Request?

An HTTP request is a message sent from the client to the server.

It contains:
- The **method** (GET, POST, etc.)
- The **path** (what resource is being requested)
- **Headers** (metadata)
- Sometimes a **body** (data)

Example (simplified):
GET /notes/123

This request alone says nothing about:
- Who the user is
- Whether they are allowed to access note 123

Security checks must happen on the server.

---

## What Is an HTTP Response?

The server responds with:
- A **status code** (success, error)
- **Headers**
- A **body** (data)

Example:
- 200 → Success
- 401 → Not authenticated
- 403 → Not authorized

These codes matter in security because:
- They reveal system behavior
- They influence client actions
- They can leak information if misused

---

## Statelessness (Very Important)

HTTP is **stateless**.

This means:
- Each request is independent
- The server does not remember previous requests automatically

So how does the server know who you are?

The answer is **state management** — usually via:
- Cookies
- Tokens
- Sessions

Security bugs often come from misunderstanding statelessness.

---

## Cookies (Plain Explanation)

Cookies are small pieces of data:
- Stored by the browser
- Sent automatically with requests

They are commonly used to:
- Store session identifiers
- Track logged-in users

Security risks arise if cookies:
- Are accessible to JavaScript when they shouldn’t be
- Are sent over insecure connections
- Are not scoped properly

Cookies are powerful — and dangerous if misused.

---

## Headers That Matter for Security

You don’t need to know all headers.
Some common security-relevant ones include:
- Authorization
- Cookie
- Content-Type
- Origin
- Referer

Headers are user-controlled input.
They must be validated.

---

## Same-Origin Concept (High Level)

Browsers apply rules about:
- Which websites can access which data

This is called the **same-origin concept**.

It helps prevent:
- One site reading another site’s data

But:
- It is a browser protection
- It does not protect the server

Servers must still enforce security.

---

## Common Beginner Mistakes

Many security issues come from assumptions like:
- “The UI prevents this”
- “The browser won’t allow that”
- “The client already validated it”

Attackers bypass clients.
Servers must enforce rules.

---

## How This Connects to Security Topics

Understanding web basics helps you reason about:
- Authentication
- Authorization
- Sessions
- CSRF
- API security
- Rate limiting

You’ll see these ideas again in Phase 1.

---

## When You’re Ready to Move On

You are ready to continue if:
- You understand the client–server model
- You know requests can be modified
- You understand that HTTP is stateless

That’s enough to start thinking about web security.

You don’t need more than this — yet.


