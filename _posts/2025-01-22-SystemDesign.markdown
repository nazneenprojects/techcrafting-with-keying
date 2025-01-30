---
layout: single
title:  "System Design Notes"
date:   2025-01-23 15:46:24 +0100
published: true
---


### How to evealuate system design -
- Simplicity 
- Fidelity : all the requirements are met
- Cost Effectiveness


### Parameters to evaluate :

| Params          | Local        | Cloud Service |
|-----------------|:------------:|--------------:|
| Simplicity      | Lower        | Higher        |
| Fidelity        | Equivalent   | Equivalent    |
| Cost of Impl    | Higher       | Lower         |



### Cloud Service Providers :
- server
- serverless

### server Vs serverless :

| Params          | Local        | Cloud Service |
|-----------------|:------------:|--------------:|
| Ease of Use     | Lower        | Higher        |
| Efficiency      | Higher       | Lower         |
| Responsiveness  | Higher       | Lower         |



### Latency and Throughput Definitions:

Latency: Time delay between initiating a request and receiving a response. Measures how quickly a single task or transaction is completed.

Throughput: Number of tasks or transactions processed in a given time period. Measures overall system capacity and performance.

Simple analogy:
- Latency = Speed of a single delivery truck
- Throughput = Total number of packages delivered by all trucks in a day

Key differences:
- Low latency means fast individual responses
- High throughput means processing many tasks simultaneously

### Webpages will load wéither one from below option:
1. Serverless api : Expensive and difficult to set up, stores static pages
2. CDN (content delivery network) : server spread across the globe, Dynamic Data will be stored here in DB.

   Note : CDN do not stores dynamic data. if it tries to do this, it will case update problem due to low latency and difficult to monitor consisteny.

### How does the internet work?
- Webpage - Router - ISP - DNS - (website DN to IP address)
- then ISP routes the request to specific CDN to render webpage

### How to choose DB ?

| Params             | SQL | NoSQL |
|--------------------|:---:|:-----:|
| Simplicity         | Yes |  No   |
| Fidelity           | Yes |  No   |
| Cost Effectiveness | Yes |  Yes  |

### Debugging the trenches -
- Logging & Monitoring. Example Cloudwatch
- Observalibity and Anamoly Detection. Example, Google Analytics.
- Check if your system is reliable by : 1. Check for points of failure by which entire system may collapse ? 2. Any external dependncy is prone to failure

### How to avoid such failure problems?
- Redundancy (having multiple vendors / providers)
- Cloud services are known for their reliability. This is one reason to move all your services under a single cloud like AWS, GCP or Azure.
- Graceful Degradation. (Giving clear message on webpage)

### Hard Questions Examples
 - Should I go with Microservice architecture?
 - Will using Nodejs is better option?
 - Implementing new features such as real time video / photo rendering. Parametrs to consider - Tech Cost, Frequency of usgae, cost of storing data
   
(Note: Meet all requirements : 1. Simple 2. Optimization)

Externally visible code pieces:
- API agrrement
- SLAs 

### When the serverless become expensive ? Serverless or Server-More?
- Option 1 - Server : host & manage own servers
- Option 2 - mirgating to another cloud
- Option 3 - cheaper alternative solution : 1. Reserve entire instances for our company. 2. Book larger instance
- Drawback - Not able to reserve capacity efficiently. No availability of auto-scaling, instance is single point of failure. Using a fleet of smaller servers.
- Problem with having multiple small servers - redirecting request in case one of the instance crahses 2. Judiciously utilising all the resources avaialble.
- Sulotion : use load balanacer (Round robin algo) or elastic load balancer (low latency)


### Load Balanacing Algorithms
- Stateless : Routing Logic is within function. Example Round Robin
- Stateful: Routing logic is stored in memory (state = Memory) Example, Least connections

### Scaling
- Horizontal scaling
- Vertical scaling
- Hybrid scaling (vertical scaling followed by Horizonztal scaling) and use Weightes Round Robin Algorithm

### Database - like memory, cache-like Recall
- Example , Product Page is slow :
- Checks the api calls through logs and network tab in browser
- Check CDN
- Chec page speed
- Check getting list of product list from server is taking time
  
#### How to reduce latency?
  - Get the data a system needs close to it
  - Asynchronous call to server and then DB fetch is faster
  - Server side caching : Stores data using Map , Key-Value, List
  - Static data load from CDN
  - Caching approach - 1. In memory Cache 2. Centralized Cache

### In Memory Cache
   - Extremly fast
   - Simple to implement,
   - Restarting the server requires re-populating the cache (cons)
   - Difficult to maintain data consistency across all the caches (cons)
   - Great for scenariois where the need is extremely low latency 
     
### Centralized Cache
  - Data duplication is much lesser
  - Scaling the cache is easier
  - Example. Redis, Memcached

Example, On e-commerce website t shirts data are stored such as - Most Popular T shirts, New arrivals, Users Recently Viewed
  
### How is data distributed among cache servers?
Option 1 : Whatever the servers asks for 
Option 2 : Strategically place data to avoid duplication ( Sharding : Spliting data into cache according to property. Hashing technique : hasg (t-shirt_id) ). 
Its Load balancing. No duplication.

Problem - What if one of the cache server crashes
Solution - Auto-recover the system

Problem - one of the cache server crshaed
- Removal of server
- Addition of server

Problem - Cache warmup or readiness takes lot of time
Solution - Consistent Hashing

### Cache Implementation -
- Drawback :  Inconsistent data between DB and cache
- Solution : Update Cache infrequently
  
- Drawback :  Objects in cache are very heavey
- Solution : Store only necessasry data

- Problem : To get the Most popular data into cache after some time interval
- Solution : set - Cache Expiry
  
- Problem : To deisgn the cache consistent with DB - Update to the DB, read from the cache
- Solution : Consistent Cache with WRITE Policy

  Redis offers :
  1. write-through policy
     - All updates to the cache are also updated in the DB  (First update DB and then update Cache)
     - Payment data cache
       
  2. write behind policy
     - All updates go only to the cache initially and the DB is updated later (First update cahce and then update DB)
     - Number of views to the product stored in cache
  3. write-aside policy
  4. write-around policy

  Mem cached by Meta offers many features too. One below -
  1. Look-aside Cache
     - Keep Cache and DB as separate entity. Update the DB independently and update the cache independently.
       
 ### Cache designing Access Patterns
- Example Cache can have info on :
   - Most Popular
   - New Arrivals
   - User's Recently viewed
     - only top 1000 active users : a. Most frequent users b. Most recently active users
       #### Eviction Policy:
     - a. Most frequent users :Use  "Least frequently used (LFU)" to delete the entry for top 1000 active users if cache needs space
     - b. Most recently active users : "Least Recently Used (LRU)" to de


