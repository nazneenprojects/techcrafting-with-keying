---

layout: single
title:  "System Design Examples"
date:   2025-01-28 12:35:00 +0100
published: true
---

## Examples and Concepts:

- **Examples**: Online Games , Simple chat or comment systems where real-time but slightly delayed updates (near real-time) are acceptable, Notification systems for less frequent updates (e.g., Gmail’s "new email" alert), Legacy systems where WebSockets aren’t feasible.
- **Concept**: Long Polling , Web Sockets

# Long Polling
### Long Polling
Long polling is a technique that mimics real-time behavior by keeping HTTP requests open until the server has data.

Long Polling is an enhancement over traditional polling. In regular polling, the client repeatedly sends requests at fixed intervals (e.g., every second) to check for updates. This can be wasteful if no new data exists.

Long Polling tweaks this approach: the client asks the server for data and then “waits” until the server has something new to return or until a timeout occurs.

### How Does Long Polling Work?
Client sends a request to the server, expecting new data.

Server holds the request open until it has an update or a timeout is reached.

If there's new data, the server immediately responds.

If there’s no new data and the timeout is reached, the server responds with an empty or minimal message.

Once the client receives a response—new data or a timeout—it immediately sends a new request to the server to keep the connection loop going.

Pros ✅
- Simple to implement (uses standard HTTP).

- Supported universally since it uses standard HTTP, and it works reliably through firewalls and proxies.

Cons ❌
- Higher latency after each update (client must re-establish connection).

- Resource-heavy on servers (many open hanging requests).

  
  # Web Sockets
 
