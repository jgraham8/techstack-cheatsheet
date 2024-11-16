# Spring Boot Basics

## Table of Contents
- [Spring Boot Basics](#spring-boot-basics)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Creating a Spring Boot Application](#creating-a-spring-boot-application)
    - [Using Spring Initializr](#using-spring-initializr)
    - [Sample Project Structure](#sample-project-structure)
  - [Main Class](#main-class)
  - [Application Properties and Configuration](#application-properties-and-configuration)
    - [Common Configurations](#common-configurations)
  - [Annotations Overview](#annotations-overview)
    - [Essential Annotations](#essential-annotations)
    - [Example Controller](#example-controller)
  - [Running and Packaging the Application](#running-and-packaging-the-application)
    - [Run the Application](#run-the-application)
    - [Build the Application](#build-the-application)
    - [Run the JAR](#run-the-jar)

## Introduction
Spring Boot simplifies Java-based web application development. It provides pre-configured templates and minimizes boilerplate code.

## Creating a Spring Boot Application

### Using Spring Initializr
Visit [start.spring.io](https://start.spring.io/) to create a Spring Boot project with dependencies.

### Sample Project Structure
```plaintext
src
├── main
│   ├── java
│   │   └── com.example.demo
│   │       └── DemoApplication.java
│   └── resources
│       └── application.properties
```

## Main Class

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

## Application Properties and Configuration
### Common Configurations

```plaintext
server.port=8081
spring.datasource.url=jdbc:postgresql://localhost:5432/mydb
spring.datasource.username=user
spring.datasource.password=pass
```

## Annotations Overview
### Essential Annotations
- @SpringBootApplication: Marks the main class of a Spring Boot application.
- @RestController: Combines @Controller and @ResponseBody.
- @RequestMapping: Maps HTTP requests to handler methods.
- @GetMapping, @PostMapping: Simplified request mappings.
  
### Example Controller
```java
@RestController
@RequestMapping("/api")
public class MyController {
    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, World!";
    }
}
```

## Running and Packaging the Application
### Run the Application
```bash
./mvnw spring-boot:run
```
### Build the Application
```bash
./mvnw package
```
### Run the JAR
```bash
java -jar target/demo-0.0.1-SNAPSHOT.jar
```
