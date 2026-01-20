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

