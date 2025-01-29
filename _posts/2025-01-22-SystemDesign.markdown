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
- Sulotion : use load balanacer (load balancer) or elastic load balancer (low latency)







