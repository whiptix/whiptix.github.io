---
layout: post
title: How to improve API latency through caching
tags: [API, Redis, Spring, Caching]
author : Chris Kahehia
---

An API's performance can be affected by a variety of factors, therefore to ensure your API performs adequetly in the real world it is imparative to monitor API latency as it plays a significant role in the overall API's performance. An elevated API latency can negatively impact your end-user's experience and lead to chun. 
One might wonder what is **API Latency**? well, API latency is the amount of time an API takes to respond to a request. this time is separated into two namely  **Queue Time**  and  **Service Time**.

> - **Queue time :** is the sum of (the time between the start of sending the request from the client and the start of the server processing the request ) and (the time between the end of the server sending the response and the end of the client processing the response)

> - **Service time :** is the time between the start of the server receiving the request and the end of the server sending the response.

![api-latency](/assets/img/api_latency.png){:class="img-responsive"}

While there are different causes of Elevated API Latency for instance inefficient code, network latency, server overload etc. In this article we will discuss on how to improve API Latency through caching as this technique helps in making DB calls faster by reducing the number of Network calls there by reducing service time.

In order to implement this, we will create one **spring boot application** that will have CRUD operations. then we will apply **Redis Cache** feature in the **Retrieve**, **Update** and **Delete** Operations.

### Step #1: Install Redis Server
Redis stands for **RE**mote **DI**ctionary **S**ever, it is an in-memory database that persists on disk and uses key-value data model. Redis can be used as an **In-Memory Database**, as a **Cache** or a **Message Broker(MQ)** in all these usecases redis server instance need to be started to do so we will follow the below steps:-
 - [Download Redis for windows 5.0.14.1](https://github.com/tporadowski/redis/releases 'Download Redis for windows 5.0.14.1')
 - Click on the resultant **.zip** file and extract it to a folder.
 - on the extracted folder double click on the **redis-server.exe** to start Redis Server.

![redis-server](/assets/img/redis_sever.png){:class="img-responsive"}

### Step #2: Create Spring boot REST application using [Spring Initializr](https://start.spring.io 'Spring Initializr')
Let's create a spring boot application using [Spring Initializr](https://start.spring.io 'Spring Initializr') and add the following dependacies Spring Web, Spring Data JPA, PostgreSQL Driver, Spring Data Redis(Access+Driver) and Spring Boot DevTools.
![spring-initializr](/assets/img/spring_redis.png){:class="img-responsive"}

### Step #3: Update application.properies
Update the application properties, to point the datasoource to your database update the database user and password. Update spring cache type and cache null values.
your ***application.propeties*** file should have the following: -
```java

```