---

layout: single
title:  "Redis : Simple Guide"
date:   2025-02-25 14:46:24 +0100
published: true

---

# Redis Simple Guide



### **What is Redis?**
Redis (Remote Dictionary Server) is an **in-memory, key-value data store** known for **speed, simplicity, and scalability**. It stores data in **RAM**, making read and write operations extremely fast compared to traditional databases.
https://redis.io/

- **Performance:** Sub-millisecond response times  
- **Data Structures:** Supports Strings, Lists, Sets, Hashes, Sorted Sets, Bitmaps, etc.  
- **Persistence:** Can optionally save data to disk for durability  
- **Scalability:** Supports replication, clustering, and partitioning  
- **Pub/Sub & Streaming:** Supports real-time messaging  



## **Common Use Cases of Redis**

### **1. Caching (Most Popular Use Case)**
Redis is widely used for caching frequently accessed data, reducing database load and improving performance.  
**Example:**  
- Storing user sessions in a web app  
- Caching API responses  
- Caching database query results  


**Example in Python (FastAPI Cache with Redis)**  

```python
import redis

cache = redis.Redis(host="localhost", port=6379, decode_responses=True)

# Set cache
cache.setex("user:123", 3600, "John Doe")  # Expiry in 1 hour

# Get cache
print(cache.get("user:123"))  # Output: John Doe
```



### **2. Session Management & Authentication**
Since Redis is super fast, it's great for storing **user sessions** instead of using cookies or database sessions.  
**Example:**  
- Storing JWT session tokens  
- Keeping track of logged-in users  


**Example:** Storing session data  
```python
cache.set("session:abc123", "user_id_456", ex=3600)  # Expires in 1 hour
```



### **3. Real-time Analytics & Leaderboards**
Redis **Sorted Sets** (`ZSET`) help in **ranking systems**, making it ideal for leaderboards, analytics, and scoring systems.  
**Example:**  
- Gaming leaderboards  
- Real-time analytics  
- Top trending topics  


**Example:** Leaderboard in Redis  
```python
cache.zadd("game_leaderboard", {"player1": 100, "player2": 200})
print(cache.zrevrange("game_leaderboard", 0, -1, withscores=True))  # Highest first
```



### **4. Pub/Sub (Real-time Messaging & Notifications)**
Redis **Pub/Sub** allows applications to send real-time messages between users or services.  
**Example:**  
- Chat applications  
- Notifications & alerts  
- Real-time streaming data  


**Example:**  
**Publisher:**
```python
cache.publish("notifications", "New user signed up!")
```
**Subscriber:**
```python
pubsub = cache.pubsub()
pubsub.subscribe("notifications")

for message in pubsub.listen():
    print(message)  # Listen for new messages
```



### **5. Rate Limiting (API Throttling)**
Redis is great for **limiting API requests** (e.g., **only 10 requests per minute per user**).  
**Example:**  
- Prevent brute force login attacks  
- Throttle API usage  
- Limit form submissions  


**Example:**  
```python
user_ip = "192.168.1.1"
key = f"rate_limit:{user_ip}"
if cache.incr(key) == 1:
    cache.expire(key, 60)  # Allow 10 requests per minute

if int(cache.get(key)) > 10:
    print("Rate limit exceeded!")
```



### **6. Job Queues & Background Processing**
Redis **Lists** and **Streams** can be used as **task queues** for background processing.  
**Example:**  
- Celery task queues  
- Asynchronous job processing  


**Example:** Adding tasks to a queue  
```python
cache.lpush("task_queue", "send_email")
```

**Worker processing tasks**  
```python
while True:
    task = cache.rpop("task_queue")
    if task:
        print(f"Processing {task}")
```



## **Summary: Why Use Redis?**
| **Feature**            | **Benefit**                                      |
|----------------------|------------------------------------------------|
| **Super Fast**      | In-memory storage with sub-millisecond latency |
| **Flexible Data Types** | Supports strings, lists, sets, hashes, sorted sets |
| **Persistence**     | Can save snapshots to disk for durability       |
| **Replication**     | Master-slave replication for high availability  |
| **Pub/Sub**         | Real-time messaging for chat and notifications  |
| **Scalable**        | Supports clustering and partitioning            |




### **When to Use Redis?**

**Yes, use Redis when:**
- You need ultra-fast reads/writes  
- Caching frequently accessed data  
- Storing real-time leaderboard or analytics  
- Managing user sessions  
- Implementing rate limiting  


**Avoid Redis when:**
- You need **strong durability** (e.g., financial transactions)  
- Your dataset is **too large for RAM**  
- Complex **relational queries** are required



## Redis Installation on Ubuntu 22 OS

To install via Snap, run:

```
sudo apt update
sudo apt install redis-tools # for redis-cli
sudo snap install redis

sudo systemctl status snap.redis.server.service  # check status

# start , stop or reestart
sudo systemctl start snap.redis.server.service
sudo systemctl stop snap.redis.server.service
sudo systemctl restart snap.redis.server.service

# OR using snap
sudo snap start redis
sudo snap stop redis
sudo snap restart redis

# To get ping pong
redis-cli ping

# check the port
redis-cli info | grep port

# check chache params
CONFIG GET *

# chache stats
INFO MEMORY






```






