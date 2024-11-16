
# Spring Boot JPA and Database Access

## Table of Contents
1. [Setting Up JPA](#setting-up-jpa)
2. [Creating Entities](#creating-entities)
3. [Defining Repositories](#defining-repositories)
4. [Using Spring Data JPA Queries](#using-spring-data-jpa-queries)

## Setting Up JPA

### Adding Dependencies
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
</dependency>
```

## Configuring application.properties
```plaintext
spring.datasource.url=jdbc:postgresql://localhost:5432/mydb
spring.datasource.username=user
spring.datasource.password=pass
spring.jpa.hibernate.ddl-auto=update
```

## Creating Entities

```java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String email;
    // Getters and setters
}
```

## Defining Repositories
```java
public interface UserRepository extends JpaRepository<User, Long> {
    List<User> findByName(String name);
}
```

## Using Spring Data JPA Queries
### Derived Query Methods
```java
List<User> findByEmailContaining(String emailFragment);
```

### Custom Queries with @Query
```java
@Query("SELECT u FROM User u WHERE u.name = :name")
List<User> findUsersByName(@Param("name") String name);
```