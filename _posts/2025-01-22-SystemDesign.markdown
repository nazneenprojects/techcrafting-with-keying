---

layout: single
title:  "System Design Notes"
date:   2025-01-23 15:46:24 +0100
published: true
---

# System Design Notes
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


   







