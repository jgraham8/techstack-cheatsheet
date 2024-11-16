# Spring Boot Security

## Table of Contents
- [Spring Boot Security](#spring-boot-security)
  - [Table of Contents](#table-of-contents)
  - [Introduction to Spring Security](#introduction-to-spring-security)
  - [Basic Authentication Setup](#basic-authentication-setup)
    - [Adding Dependencies](#adding-dependencies)
  - [Default Configuration](#default-configuration)
  - [JWT Authentication](#jwt-authentication)
    - [Generating JWT Tokens](#generating-jwt-tokens)
  - [Method-Level Security](#method-level-security)
    - [Example Usage](#example-usage)

## Introduction to Spring Security
Spring Security provides comprehensive security services for Java applications.

## Basic Authentication Setup

### Adding Dependencies
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

## Default Configuration
Spring Boot enables basic authentication by default. For custom configurations:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.csrf().disable()
            .authorizeRequests()
            .anyRequest().authenticated()
            .and()
            .httpBasic();
    }
}
```
## JWT Authentication
JWT (JSON Web Token) is widely used for stateless authentication.

### Generating JWT Tokens
```java
public String generateToken(String username) {
    return Jwts.builder()
               .setSubject(username)
               .setIssuedAt(new Date())
               .setExpiration(new Date(System.currentTimeMillis() + 1000 * 60 * 60 * 10)) // 10 hours
               .signWith(SignatureAlgorithm.HS256, "secret_key")
               .compact();
}
```
## Method-Level Security
```java
@EnableGlobalMethodSecurity(prePostEnabled = true)
public class MethodSecurityConfig extends GlobalMethodSecurityConfiguration {
}
```
### Example Usage
```java
@PreAuthorize("hasRole('ADMIN')")
public void secureMethod() {
    // Method logic
}
```