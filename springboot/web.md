# Spring Boot Web Development

## Table of Contents
- [Spring Boot Web Development](#spring-boot-web-development)
  - [Table of Contents](#table-of-contents)
  - [Introduction to Spring MVC](#introduction-to-spring-mvc)
  - [Creating Controllers](#creating-controllers)
  - [Handling Requests and Responses](#handling-requests-and-responses)
    - [Path Variables and Query Parameters](#path-variables-and-query-parameters)
  - [Serving Static Content](#serving-static-content)

## Introduction to Spring MVC
Spring MVC is part of the Spring framework for building web applications. It uses the Model-View-Controller design pattern.

## Creating Controllers
```java
@RestController
@RequestMapping("/users")
public class UserController {
    @GetMapping("/{id}")
    public User getUser(@PathVariable Long id) {
        // Retrieve user by ID logic here
    }

    @PostMapping
    public User createUser(@RequestBody User user) {
        // Create user logic here
    }
}
```

## Handling Requests and Responses
### Path Variables and Query Parameters
```java
@GetMapping("/search")
public List<User> searchUsers(@RequestParam String name) {
    // Search logic here
}
```
## Serving Static Content
```plaintext
Location: src/main/resources/static
Example: A file at src/main/resources/static/index.html will be served at http://localhost:8080/index.html.
```