---
layout: post
title: How to improve API latency through caching
tags: [API, Redis, Spring, Caching]
author : Chris Kahehia
---

An API's performance can be affected by a variety of factors such as inefficient code, network latency, server overload etc, to ensure your API performs adequetly in the real world it is imparative to monitor the latency of your API since an elevated API latency can negatively impact your end-user's experience and lead to chun. However, there are different ways to improve API performance and reduce the latency such as allocating more resources to the server, implementing caching, reviewing the code etc. In this article we will discuss ***How to improve API latency through caching*** with a real world example.

One might wonder what is **API Latency**? well, API latency is the amount of time an API takes to respond to a request. this time is separated into two namely  **Queue Time**  and  **Service Time**.
 - **Queue time :** is the sum of (the time between the start of sending the request from the client and the start of the server processing the request ) and (the time between the end of the server sending the response and the end of the client processing the response)
 - **Service time :** is the time between the start of the server receiving the request and the end of the server sending the response.

![api-latency](/assets/img/api_latency.png){:class="img-responsive"}


In order to implement this technique, we will create one **spring boot REST application** that will have CRUD operations, then we will apply **Redis Cache** feature in the **Retrieve**, **Update** and **Delete** Operations. Below is a step by step procedure on how to do so:-

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
    logging.level.org.springframework.jdbc.datasource.init.ScriptUtils=debug
    spring.jpa.hibernate.ddl-auto=none

    spring.datasource.url=jdbc:postgresql://localhost:5432/redis_example
    spring.datasource.username=postgres
    spring.datasource.password=password

    spring.cache.type=redis
    spring.cache.redis.cache-null-values=true
```
### Step 4: Create an Entity class as Product.java
Create an entity class ***Product.java*** that has a NoArgsContructor, AllArgsConstructor, Getters and Setters, ToString, EqualsAndHashCode and RequiredArgsConstructor
``` java
@Entity
@Table(name = "products")
public class Product implements Serializable {
    private static final long serialVersionUID = 4L;
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private  Long prodId;
    private String productName;
    //NoArgsConstructor
    //AllArgsConstructor
    //getters and setters
    //ToString
    //EqualsAndHashCode
    //RequiredArgsConstructor

}
```
### Step 5: Create a repository interface as ProductRepository.java
Create a Repository Interface as ***ProductRepository.java*** which extends JpaRepository<Product, Long> as below: -
```java
@Repository
public interface ProductRepository extends JpaRepository<Product, Long> {
}
```
### Step 6: Create Service Interface and implement the service.
In the service layer create an interface ***ProductService.java*** and add the methods to be implemented. Create a class ***ProductServiceImpl.java*** that implements the above interface. On the implementation of the interface we will add anotations to apply Caching mechanism offered by redis. We will use the following annotations:-

### Step 7: Add Caching anotation @EnableCaching at starter class
In order to implement Redis cache on spring boot we will use four annotations: -
```java
@SpringBootApplication
@EnableCaching
public class RedisApplication {

	public static void main(String[] args) {
		SpringApplication.run(RedisApplication.class, args);
	}

}
```
### Step 8: Create RestController class as ProductRestController.java
