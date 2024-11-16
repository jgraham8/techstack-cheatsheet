# Spring Boot Testing

## Table of Contents
- [Spring Boot Testing](#spring-boot-testing)
  - [Table of Contents](#table-of-contents)
  - [Introduction to Spring Boot Testing](#introduction-to-spring-boot-testing)
    - [Adding Testing Dependencies](#adding-testing-dependencies)
  - [Unit Testing with JUnit and Mockito](#unit-testing-with-junit-and-mockito)
    - [Example Service Class](#example-service-class)
    - [Writing a Unit Test with JUnit](#writing-a-unit-test-with-junit)
    - [Using Mockito for Mocking](#using-mockito-for-mocking)
  - [Integration Testing](#integration-testing)
    - [Basic Integration Test](#basic-integration-test)
  - [Configuration for Database Testing](#configuration-for-database-testing)
    - [Testing Controllers](#testing-controllers)
      - [Using @WebMvcTest](#using-webmvctest)
    - [Testing Repositories](#testing-repositories)
      - [Example Repository Test with @DataJpaTest](#example-repository-test-with-datajpatest)

## Introduction to Spring Boot Testing
Spring Boot simplifies testing by providing various tools and configurations. Key dependencies include `spring-boot-starter-test`, which bundles libraries like JUnit, Mockito, and AssertJ.

### Adding Testing Dependencies
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

## Unit Testing with JUnit and Mockito
### Example Service Class
```java
@Service
public class UserService {
    public String getUserGreeting(String name) {
        return "Hello, " + name + "!";
    }
}
```
### Writing a Unit Test with JUnit
```java
@SpringBootTest
public class UserServiceTest {
    
    @Autowired
    private UserService userService;
    
    @Test
    public void testGetUserGreeting() {
        String result = userService.getUserGreeting("John");
        assertEquals("Hello, John!", result);
    }
}
```
### Using Mockito for Mocking
```java
@RunWith(MockitoJUnitRunner.class)
public class UserServiceTest {

    @InjectMocks
    private UserService userService;

    @Test
    public void testGreetingWithMock() {
        // Mock behavior if needed
        assertEquals("Hello, Mock!", userService.getUserGreeting("Mock"));
    }
}
```
## Integration Testing
### Basic Integration Test
```java
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
@AutoConfigureMockMvc
public class UserControllerIntegrationTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    public void shouldReturnDefaultMessage() throws Exception {
        mockMvc.perform(get("/api/hello"))
               .andExpect(status().isOk())
               .andExpect(content().string("Hello, World!"));
    }
}
```
## Configuration for Database Testing
Add @DataJpaTest to ensure only JPA components are loaded:

```java
@DataJpaTest
public class UserRepositoryTest {
    
    @Autowired
    private TestEntityManager entityManager;
    
    @Autowired
    private UserRepository userRepository;

    @Test
    public void whenFindByName_thenReturnUser() {
        User user = new User();
        user.setName("TestUser");
        entityManager.persistAndFlush(user);

        User found = userRepository.findByName("TestUser").get(0);
        assertEquals("TestUser", found.getName());
    }
}
```
### Testing Controllers
#### Using @WebMvcTest
```java
@WebMvcTest(UserController.class)
public class UserControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean
    private UserService userService;

    @Test
    public void testGetUser() throws Exception {
        when(userService.getUserGreeting("John")).thenReturn("Hello, John!");

        mockMvc.perform(get("/api/users/John"))
               .andExpect(status().isOk())
               .andExpect(content().string("Hello, John!"));
    }
}
```
### Testing Repositories
#### Example Repository Test with @DataJpaTest
```java
@DataJpaTest
public class UserRepositoryIntegrationTest {

    @Autowired
    private UserRepository userRepository;

    @Test
    public void testSaveAndRetrieveUser() {
        User user = new User();
        user.setName("TestUser");
        userRepository.save(user);

        Optional<User> foundUser = userRepository.findByName("TestUser").stream().findFirst();
        assertTrue(foundUser.isPresent());
        assertEquals("TestUser", foundUser.get().getName());
    }
}
```