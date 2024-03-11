---
title: Spring Annotations

hide:
  - tags
tags:
  - Spring Security Annotations




---

# Spring Annotations

---------

## Spring Security Annotations

 
Spring Security provides a set of annotations that allow you to secure your application at the method level. These
annotations enable you to control access to specific methods based on user roles, permissions, or other security
conditions.

### 1. **@Secured**:

This annotation is used to secure methods by specifying which roles are allowed to access them. You can
use this annotation on methods or classes.

Example:

```java
import org.springframework.security.access.annotation.Secured;

    @Service
    public class MyService {
        
        @Secured("ROLE_ADMIN")
        public void adminOnlyMethod() {
            // Method accessible only to users with ROLE_ADMIN
        }
    }
```

### 2. **@PreAuthorize and @PostAuthorize**:

These annotations provide a more fine-grained control over method security by
allowing you to specify security expressions using SpEL (Spring Expression Language).

 - `@PreAuthorize`: Specifies a condition that must be met before a method is invoked.
- `@PostAuthorize`: Specifies a condition that must be met after a method is invoked.

Example:

```java
import org.springframework.security.access.prepost.PreAuthorize;
import org.springframework.security.access.prepost.PostAuthorize;

    @Service
    public class MyService {
        
        @PreAuthorize("hasRole('ADMIN')")
        public void adminOnlyMethod() {
            // Method accessible only to users with ROLE_ADMIN
        }
        
        @PostAuthorize("returnObject.owner == authentication.name")
        public Object getOwnedObject() {
            // Method returns object owned by the current user
        }
    }
```

### 3. **@RolesAllowed**:

Similar to `@Secured`, this annotation specifies which roles are allowed to access a method. It is
part of the Java EE security annotations and is supported in Spring Security.

Example:

```java
import javax.annotation.security.RolesAllowed;

    @Service
    public class MyService {
        
        @RolesAllowed("ROLE_ADMIN")
        public void adminOnlyMethod() {
            // Method accessible only to users with ROLE_ADMIN
        }
    }
```

### 4. **@PreFilter and @PostFilter**:

These annotations allow you to filter method parameters or return values based on a
security expression.

- `@PreFilter`: Filters the input collection before executing the method.
- `@PostFilter`: Filters the return collection after executing the method.

Example:

```java
import org.springframework.security.access.prepost.PreFilter;
import org.springframework.security.access.prepost.PostFilter;

    @Service
    public class MyService {
        
        @PreFilter("filterObject.owner == authentication.name")
        public void processObjects(List<Object> objects) {
            // Method processes objects owned by the current user
        }
        
        @PostFilter("filterObject.owner == authentication.name")
        public List<Object> getOwnedObjects() {
            // Method returns a list of objects owned by the current user
        }
    }
```

### 5. **@Secured, @PreAuthorize, and @PostAuthorize in Web Layer**:

These annotations can also be used in the web layer to
secure controller methods.

Example:

```java
    import org.springframework.security.access.annotation.Secured;
    import org.springframework.security.access.prepost.PreAuthorize;
    import org.springframework.security.access.prepost.PostAuthorize;
    
    @Controller
    public class MyController {
        
        @Secured("ROLE_ADMIN")
        @GetMapping("/admin")
        public String adminPage() {
            // Controller method accessible only to users with ROLE_ADMIN
        }
        
        @PreAuthorize("hasRole('USER')")
        @PostMapping("/user")
        public String userAction() {
            // Controller method accessible only to users with ROLE_USER
        }
        
        @PostAuthorize("returnObject.owner == authentication.name")
        @GetMapping("/owned-object")
        public Object getOwnedObject() {
            // Controller method returns object owned by the current user
        }
    }
```

### 6. **@Secured vs. @PreAuthorize/@PostAuthorize**:

While both `@Secured` and `@PreAuthorize`/`@PostAuthorize` serve
similar purposes, there are differences in their usage and flexibility.

- `@Secured` is a simple annotation that checks if the user has at least one of the specified roles. It does not
      support complex SpEL expressions.
- `@PreAuthorize` and `@PostAuthorize` offer more flexibility as they support SpEL expressions, allowing you to
      define intricate access control logic based on method parameters, return values, or any other contextual
      information.

Example:

```java
// Using @Secured
@Secured({"ROLE_ADMIN", "ROLE_USER"})
public void securedMethod() {
// Method accessible to users with ROLE_ADMIN or ROLE_USER
}

    // Using @PreAuthorize
    @PreAuthorize("hasRole('ADMIN') and #entity.owner == authentication.name")
    public void preAuthorizeMethod(Entity entity) {
        // Method accessible to users with ROLE_ADMIN and if entity owner matches authenticated user
    }
```

### 7. **@EnableGlobalMethodSecurity**:

This annotation is used at the configuration level to enable method-level security
annotations such as `@Secured`, `@PreAuthorize`, etc. You can configure which annotation types to enable and
customize their behavior.

Example:

```java
@Configuration
@EnableGlobalMethodSecurity(securedEnabled = true, prePostEnabled = true)
public class MethodSecurityConfig extends GlobalMethodSecurityConfiguration {
// Configuration for method-level security annotations
}
```

By using `@EnableGlobalMethodSecurity`, you can enable method-level security annotations globally across your
application, providing consistent and centralized security enforcement.

Certainly, let's delve into a couple more annotations:

### 8. **@AuthenticationPrincipal**:

This annotation allows you to inject the currently authenticated principal directly
into a method parameter. It is particularly useful when you need access to the user details within a method.

Example:

```java
   import org.springframework.security.core.annotation.AuthenticationPrincipal;
   import org.springframework.security.core.userdetails.UserDetails;
   
   @Service
   public class UserService {
       
       public void processUserDetails(@AuthenticationPrincipal UserDetails userDetails) {
           // Access userDetails to perform user-specific operations
       }
   }
```

In this example, the `processUserDetails` method can access the details of the currently authenticated user via
the `userDetails` parameter.

### 9. **@Secured, @PreAuthorize, and @PostAuthorize with Parameters**:

These annotations support passing method parameters to SpEL expressions for dynamic access control.

Example:

```java
   @Service
   public class ProductService {
       
       @PreAuthorize("#productId != null and hasPermission(#productId, 'Product', 'read')")
       public void viewProductDetails(Long productId) {
           // Method logic to view product details
       }
   }
```

Here, the `viewProductDetails` method uses `@PreAuthorize` to ensure that the user has permission to read the
specified product identified by `productId`.

These annotations and techniques offer additional capabilities for fine-tuning security in your Spring applications,
allowing you to inject user details directly into methods and dynamically control access based on method parameters.


---------

## Spring MVC Annotations


### Overview of Spring MVC Annotations

Spring MVC is a powerful module within the Spring Framework that helps build web applications. Annotations in Spring MVC simplify the configuration and functionality mapping, making the development process more intuitive and less prone to errors. Below is a guide to some of the most commonly used Spring MVC annotations, organized by their roles in the framework.

### Controller Layer Annotations

#### `@Controller`
- **Purpose**: Indicates that a class serves the role of a controller in the MVC pattern. Controllers handle incoming web requests and return responses.
- **Example Usage**:
  ```java
  @Controller
  public class MyController { }
  ```

#### `@RestController`
- **Purpose**: A convenience annotation that combines `@Controller` and `@ResponseBody`. It indicates that the class is a controller where every method returns a domain object instead of a view.
- **Example Usage**:
  ```java
  @RestController
  public class MyRestController { }
  ```

#### `@RequestMapping`
- **Purpose**: Maps HTTP requests to handler methods of MVC and REST controllers. It can be applied at the class or method level.
- **Example Usage**:
  ```java
  @RequestMapping("/greet")
  public String greet() {
    return "Hello, World";
  }
  ```

### Method Parameter Annotations

#### `@RequestParam`
- **Purpose**: Binds request parameters to a method parameter in your controller.
- **Example Usage**:
  ```java
  public String greet(@RequestParam(name = "name") String name) {
    return "Hello, " + name;
  }
  ```

#### `@PathVariable`
- **Purpose**: Binds a URI template variable to a method parameter.
- **Example Usage**:
  ```java
  @RequestMapping("/user/{id}")
  public User getUser(@PathVariable("id") Long id) {
    return userService.getUserById(id);
  }
  ```

#### `@RequestBody`
- **Purpose**: Binds the HTTP request body to a domain object. Typically used in RESTful controllers.
- **Example Usage**:
  ```java
  @PostMapping("/user")
  public User createUser(@RequestBody User user) {
    return userService.saveUser(user);
  }
  ```

#### `@RequestHeader`
- **Purpose**: Binds a request header to a method parameter.
- **Example Usage**:
  ```java
  public String greetWithLanguage(@RequestHeader("Accept-Language") String language) {
    return "Greetings in " + language;
  }
  ```

### Response-Related Annotations

#### `@ResponseBody`
- **Purpose**: Indicates that the return type of the method should be written directly to the HTTP response body. Used with `@Controller` annotation.
- **Example Usage**:
  ```java
  @RequestMapping("/name")
  @ResponseBody
  public String getName() {
    return "John Doe";
  }
  ```

#### `@ResponseStatus`
- **Purpose**: Marks a method or exception class with the status code and reason that should be returned.
- **Example Usage**:
  ```java
  @ResponseStatus(HttpStatus.NOT_FOUND, reason = "User not found")
  public class UserNotFoundException extends RuntimeException { }
  ```

### Data Binding and Validation Annotations

#### `@ModelAttribute`
- **Purpose**: Binds a method parameter or method return value to a named model attribute, exposed to a web view.
- **Example Usage**:
  ```java
  @ModelAttribute("user")
  public User createUserModel() {
    return new User();
  }
  ```

#### `@Valid`

- **Purpose**: Ensures that a model attribute is validated with the configured validation framework (typically JSR-303/JSR-380 Bean Validation).
- **Example Usage**:
  ```java
  public String submit(@Valid @ModelAttribute("user") User user, BindingResult result) {
    if (result.hasErrors()) {
      return "userForm";
    }
    return "submitSuccess";
  }
  ```

 
### Asynchronous Processing Annotations

#### `@Async`
- **Purpose**: Marks a method to be executed asynchronously, allowing the caller to continue processing without waiting for the method to complete.
- **Example Usage**:
  ```java
  @Async
  public CompletableFuture<String> processAsync() {
    // Asynchronous operation
    return CompletableFuture.completedFuture("Processed");
  }
  ```

#### `@EnableAsync`
- **Purpose**: Enables Spring's asynchronous method execution capability within the application context, typically placed on a configuration class.
- **Example Usage**:
  ```java
  @Configuration
  @EnableAsync
  public class AsyncConfig { }
  ```

### Cross-Origin Resource Sharing (CORS) Annotations

#### `@CrossOrigin`
- **Purpose**: Enables CORS on specific handler classes or methods, allowing resources to be accessed from a different domain than the one that served them.
- **Example Usage**:
  ```java
  @CrossOrigin(origins = "http://example.com")
  @GetMapping("/cors-enabled")
  public String corsEnabledMethod() {
    return "CORS enabled";
  }
  ```

### RESTful Service Annotations

#### `@RestControllerAdvice`
- **Purpose**: A convenience annotation that combines `@ControllerAdvice` and `@ResponseBody`, providing a global exception handling mechanism for RESTful controllers.
- **Example Usage**:
  ```java
  @RestControllerAdvice
  public class RestExceptionHandler {
    @ExceptionHandler(value = Exception.class)
    public ResponseEntity<Object> handleException(Exception e) {
        return new ResponseEntity<>("Error occurred", HttpStatus.INTERNAL_SERVER_ERROR);
    }
  }
  ```

#### `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, `@PatchMapping`
- **Purpose**: Specific shortcut annotations for HTTP GET, POST, PUT, DELETE, and PATCH methods, simplifying the mapping of HTTP operations to handler methods.
- **Example Usage**:
  ```java
  @GetMapping("/users")
  public List<User> listUsers() {
    return userService.findAll();
  }
  ```

### Session and Cookie Handling Annotations

#### `@SessionAttribute`
- **Purpose**: Used for binding a method parameter or method return value to a session attribute.
- **Example Usage**:
  ```java
  @GetMapping("/get")
  public String getSessionAttribute(@SessionAttribute("user") User user) {
    return "User from session: " + user.getName();
  }
  ```

#### `@CookieValue`
- **Purpose**: Binds a method parameter to the value of an HTTP cookie.
- **Example Usage**:
  ```java
  @GetMapping("/cookie")
  public String readCookie(@CookieValue("sessionId") String sessionId) {
    return "Session ID: " + sessionId;
  }
  ```

### Handling Request Metadata

#### `@RequestAttribute`
- **Purpose**: Binds a method parameter to a request attribute.
- **Example Usage**:
  ```java
  @GetMapping("/attribute")
  public String getRequestAttribute(@RequestAttribute("attr") String attr) {
    return "Request attribute value: " + attr;
  }
  ```


### Web Application Security Annotations

Spring MVC seamlessly integrates with Spring Security to protect web applications. While Spring Security itself is a broad topic, certain annotations directly impact how security is managed within Spring MVC applications. These annotations help define security constraints at the controller level, enhancing the declarative control over application security.

#### `@PreAuthorize` / `@PostAuthorize`
- **Purpose**: These annotations are used to express security constraints on methods. `@PreAuthorize` can decide if a method can be executed based on the given expression before the method is invoked. `@PostAuthorize` allows for the same after the method's execution, often evaluating the returned value.
- **Example Usage**:
  ```java
  @PreAuthorize("hasRole('ADMIN')")
  public String getAdminData() {
    return "Sensitive Admin Data";
  }
  ```

#### `@Secured`
- **Purpose**: Similar to `@PreAuthorize`, but it's less flexible as it only allows specifying roles directly without complex SpEL expressions.
- **Example Usage**:
  ```java
  @Secured("ROLE_USER")
  public String getUserData() {
    return "User Data";
  }
  ```

### Testing Annotations in Spring MVC

Spring MVC provides a set of annotations specifically designed to simplify testing MVC applications by setting up test contexts, mocking web application aspects, and performing requests and assertions in a test-friendly environment.

#### `@WebMvcTest`
- **Purpose**: Used for Spring MVC tests that focus on Spring MVC components, such as controllers. It auto-configures the Spring MVC infrastructure for unit tests.
- **Example Usage**:
  ```java
  @WebMvcTest(controllers = UserController.class)
  public class UserControllerTest { }
  ```

#### `@MockBean`
- **Purpose**: Adds mock objects to the Spring application context. The mock will replace any existing bean of the same type in the application context. If no bean of the same type is defined, a new one will be added.
- **Example Usage**:
  ```java
  @MockBean
  private UserService userService;
  ```

### Spring MVC Configuration Annotations

To support the configuration and customization of Spring MVC applications, several annotations are used to define beans, configure request mappings, and more, within the application context.

#### `@EnableWebMvc`
- **Purpose**: Adds this annotation to an `@Configuration` class to import the Spring MVC configuration from `WebMvcConfigurerAdapter`.
- **Example Usage**:
  ```java
  @Configuration
  @EnableWebMvc
  public class WebConfig implements WebMvcConfigurer { }
  ```

#### `@Configuration`
- **Purpose**: Indicates that the class has `@Bean` definition methods, so Spring container can process the class and generate Spring Beans to be used in the application.
- **Example Usage**:
  ```java
  @Configuration
  public class AppConfig { }
  ```

### Bean Lifecycle and Web Context Annotations

Understanding and managing the lifecycle of beans within the Spring MVC context is crucial for developing efficient and effective web applications.

#### `@PostConstruct` / `@PreDestroy`

- **Purpose**: Used within Spring Beans to denote methods that should be executed after the bean's initialization and before the bean's destruction, respectively.
- **Example Usage**:
  ```java
  @PostConstruct
  public void init() {
    // Initialization code
  }
  
  @PreDestroy
  public void cleanup() {
    // Cleanup code
  }
  ```

---

## Spring Boot Annotations

Spring Boot simplifies the development of Spring applications by offering convention over configuration, aiming to reduce the amount of setup and configuration required to get a Spring application up and running. It provides a set of annotations to streamline the configuration process, manage application behavior, and automate much of the routine work involved in setting up a Spring application. Below, we explore some of the key Spring Boot annotations and their purposes.

### Core Spring Boot Annotations

#### `@SpringBootApplication`
- **Purpose**: Serves as a convenience annotation that combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`. It's typically used on the main application class to enable auto-configuration, component scanning, and to register extra configurations.
- **Example Usage**:
  ```java
  @SpringBootApplication
  public class MyApp {
      public static void main(String[] args) {
          SpringApplication.run(MyApp.class, args);
      }
  }
  ```

### Auto-Configuration and Component Scanning

#### `@EnableAutoConfiguration`
- **Purpose**: Automatically configures your application based on the dependencies present on the classpath. This simplifies the development process by minimizing the need for explicit configuration.
- **Usage Context**: While `@SpringBootApplication` includes this annotation, `@EnableAutoConfiguration` can be used alone to customize behavior.

#### `@ComponentScan`
- **Purpose**: Configures component scanning directives for the Spring application context, enabling the automatic detection of Spring components via classpath scanning.
- **Usage Note**: Included in `@SpringBootApplication`, but can be used separately to define custom scan paths.

### Configuration and Beans

#### `@Configuration`
- **Purpose**: Indicates that a class is a source of bean definitions. It's used to define beans and application context configuration information.
- **Example Usage**:
  ```java
  @Configuration
  public class AppConfig {
      @Bean
      public MyBean myBean() {
          return new MyBean();
      }
  }
  ```

#### `@Bean`
- **Purpose**: Marks a method to define a bean to be managed by the Spring container. It's used within classes annotated with `@Configuration`.
- **Example Usage**:
  ```java
  @Bean
  public MyService myService() {
      return new MyServiceImpl();
  }
  ```

### Conditional Annotations

#### `@Conditional`
- **Purpose**: Specifies that a component or configuration should only be registered if the specified conditions are met.
- **Example Usage**:
  ```java
  @Conditional(MyCondition.class)
  public class ConditionalBean { }
  ```

#### `@ConditionalOnClass`, `@ConditionalOnMissingBean`, `@ConditionalOnProperty`
- **Purpose**: Part of a series of annotations to conditionally enable auto-configuration based on presence or absence of classes, beans, or properties.
- **Usage Context**: Useful for creating auto-configuration that adapts to the application's environment and classpath.

### Web Application Development

#### `@RestController`, `@RequestMapping`
- **Purpose**: `@RestController` is a specialized version of `@Controller` for RESTful controllers, and `@RequestMapping` maps HTTP requests to handler methods of MVC and REST controllers.
- **Spring Boot Context**: Spring Boot auto-configures the DispatcherServlet and other web components when web dependencies are on the classpath, simplifying MVC and REST controller development.

### Running and Testing

#### `@SpringBootTest`
- **Purpose**: Used to provide a bridge between Spring Boot test features and JUnit. It allows for loading an ApplicationContext and having beans auto-configured in a test environment.
- **Example Usage**:
  ```java
  @SpringBootTest
  public class MyApplicationTests {
      @Test
      public void contextLoads() { }
  }
  ```
 

---




