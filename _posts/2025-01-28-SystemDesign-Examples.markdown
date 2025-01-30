---
layout: single
title:  "System Design Examples"
date:   2025-01-28 12:35:00 +0100
published: true
---

# Concept: Long Polling

- **Examples**: Simple chat or comment systems where real-time but slightly delayed updates (near real-time) are acceptable, Notification systems for less frequent updates (e.g., Gmail’s "new email" alert), Legacy systems where WebSockets aren’t feasible.
- **Concept**: Long Polling 

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

  
# Concept: Web Sockets

- **Examples**: Live chat and collaboration tools (Slack, Google Docs, etc.), Multiplayer online games with real-time state synchronization, Live sports/financial dashboards that need to push frequent updates.
- **Concept**: Web Socket
- 
### WebSockets
WebSockets provide a full-duplex, persistent connection between the client and the server.

Once established, both parties can send data to each other at any time, without the overhead of repeated HTTP requests.

### How Do WebSockets Work?
- Handshake: Client sends an HTTP request with Upgrade: websocket.
- Connection: If supported, the server upgrades the connection to WebSocket (switching from http:// to ws://). After the handshake, client and server keep a TCP socket open for communication.
- Full-Duplex Communication: Once upgraded, data can be exchanged bidirectionally in real time until either side closes the connection.
 
# Choosing the Right Solution
Both methods achieve real-time updates, but your choice depends on your project’s requirements:

Complexity and Support
- Long Polling is easier to implement using standard libraries. Any environment that supports HTTP can handle it, often without extra packages.
- WebSockets require a bit more setup and a capable proxy environment (e.g., support in Nginx or HAProxy). However, many frameworks (e.g., Socket.io) - simplify the process significantly.

Scalability and Performance
Long Polling can become resource-intensive with a large number of simultaneous clients, due to multiple open connections waiting on the server side.
WebSockets offer a more efficient, persistent connection and scale better for heavy, frequent data streams.

Type of Interaction
Long Polling fits scenarios where data updates aren’t super frequent. If new data arrives every few seconds or minutes, long polling might be enough.
WebSockets are better for high-frequency updates or two-way communication (e.g., multiple participants editing a document or interacting in a game).

Network Constraints
Long Polling typically works even in older networks or those with strict firewalls.
WebSockets might face issues in certain corporate or older mobile environments, though this is less of a problem as the standard becomes more widespread.

While both achieve real-time communication, WebSockets are generally more efficient for truly real-time applications, while Long Polling can be simpler to implement for less demanding scenarios.

### Alternative Solutions Worth Considering
1. Server-Sent Events (SSE)
Allows the server to push messages to the client over HTTP.

It's simpler than WebSockets for one-way communication, but not full-duplex.

Best suited for use cases like news feeds, real-time notifications, and status updates.

2. MQTT
Commonly used in IoT for lightweight publish-subscribe messaging.

Specialized for device-to-device or device-to-server communication with minimal overhead.

3. Libraries like Socket.io
Provides an abstraction over WebSockets for easier real-time communication.

Automatically falls back to long polling if WebSockets are unsupported.

Ensures cross-browser compatibility with robust and reliable performance.

# Reference: 
- algomaster@substack.com
