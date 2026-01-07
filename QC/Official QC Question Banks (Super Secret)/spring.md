# Unit: Spring

## Modules

* [Spring Core](#spring-core)
* [Spring MVC](#spring-mvc)
* [Spring AOP](#spring-aop)
* [Spring Data](#spring-data)
* [Spring Boot](#spring-boot)
* [Spring Security](#spring-security)

## Spring Core

### Importance: CRITICAL

[Back to top](#unit-spring)

* **What are Spring Projects and Spring Modules?**
  * Keywords, concepts, or topics that should be in the response:
    * *Spring Project:* Provide solutions to other issues faced by enterprise applications; Spring Boot, Spring Data, Spring Cloud, Spring HATEOAS
    * *Spring Module:* All Spring Modules share the same release version as the Spring Framework. They are part of the same project; Spring Core, Spring AOP, Spring Web MVC, Spring DAO, Spring ORM, Spring context, and Spring Web flow

* **What are the benefits of Spring?**
  * Keywords, concepts, or topics that should be in the response:
    * Core technologies: dependency injection, events, resources, validation, data binding, type conversion, SpEL, AOP.
    * Testing: mock objects, TestContext framework, Spring MVC Test, WebTestClient
    * Data Access: transactions, DAO support, JDBC, ORM, Marshalling XML

* **What is IOC and what does the IOC Container do?**
  * Keywords, concepts, or topics that should be in the response:
    * IoC: Inversion of control; Manages Dependency Injections; allows for loose coupling of objects
    * IoC Container: Creates the objects (beans), configures and assembles their dependencies, and manages their entire life cycle  
  * Possible follow-up questions:
    * **How does the IoC Container get the information about the beans?**
      * Configuration in the XML file or annotations

* **What is dependency injection and what are some of the benefits of using dependency injection?**
  * Keywords, concepts, or topics that should be in the response:
    * DI is when one object relies on another objects to run. Allows for objects that are dependent on the creation of another one to be loosely coupled instead of fully dependent

* **What types of dependency injection does Spring support?**
  * Keywords, concepts, or topics that should be in the response:
    * *Setter Dep Inj:* DI will be injected w/ help of getter/setter. To set the DI as Setter, you do it in the bean-config file under the `<property>` tag.
    * *Constructor DI:* DI done with constructors. Set it in the bean-config file under `<constructor-arg>` tag
    * *Field Injection:* the `@Autowired` annotation is a Spring component; thus, the bean is no longer a POJO and cannot be instantiated independently. Field injection cannot be used for final fields.

* **What is bean wiring? What about autowiring?**
  * Keywords, concepts, or topics that should be in the response:
    * *Bean Wiring:* the process of combining beans with Spring container. You should tell the container what beans are needed and how the container should use dependency injection to tie them together
    * *Autowiring:* the `@Autowired` annotation is used to inject the dependency into a bean (equivalent to ref XML tag/attribute); The Spring container can auto wire on the basis of the following parameters: *byName, byType, constructor, and autodetect*.
  * Possible follow-up questions:
    * **What are the different ways that Spring can wire beans?**
      * XML: The configuration file contains the definitions of the beans. When the Spring-based software application starts up, the beans are called and based on the Dependency Injection (DI), the beans are wired. In the file, the element needs to be declared and the `<constructor-arg>` and `<property>` elements need to be used.
      * Through a Java Class: A Spring Configuration class needs to be created and the class `@Configuration` needs to be annotated. The `@Configuration` tells Spring that the beans that should be wired are configured within this class.

### Spring Core - HIGH

[Back to top](#unit-spring)

* **What are Sterotype annotations? List some stereotype annotations. What are the differences between these?**
  * Keywords, concepts, or topics that should be in the response:
    * *Sterotype annotations:* markers for any class that fulfills a role within an application. This helps remove, or at least greatly reduce, the Spring XML configuration required for these components
      * `@Component`: generic stereotype used to declare an objects as a bean
      * `@Service`: marks a class as a Service for an application
      * `@Repository`: marks a class to be used as a for use with storing data within a repository or database; provides benefits for objects that would otherwise be utilized as a Data Access Object (DAO)
      * `@Controller`:  marks a class as a Spring MVC Controller which allow the use of handler mapping annotations; autodetected through classpath scanning

* **What are some differences between BeanFactory and ApplicationContext? Which one eagerly instantiates your beans?**
  * Keywords, concepts, or topics that should be in the response:
    * *Bean Factory:* loads beans on demand (lazy), more lightweight (better in memory-constrained systems), only supports Singleton and Prototype bean scopes
    * *Application Context:* loads beans on startup (eager), preferred method in enterprise applications, can handle all bean scopes, can use annotation-based dependency injection

* **What are the scopes of Spring beans? Which is default?**
  * Keywords, concepts, or topics that should be in the response:
    * singleton (Default): Returns a single bean instance per Spring IoC container.
    * prototype: Returns a new bean instance each time when requested.
    * request: Returns a single instance for every HTTP request call.
    * session: Returns a single instance for every HTTP session.
    * global session: global session scope is equal as session scope on portlet-based web applications.

### Spring Core - REGULAR

[Back to top](#unit-spring)

* **What is the Spring Bean lifecycle?**
  * Keywords, concepts, or topics that should be in the response:
    * The management of Beans, conducted by the BeanFactory or Application Context, includes instantiation, configuration and the eventual removal (or destruction) of beans. More specifically:
      * Beans are first instantiated.
      * Their properties are set
      * Any associated interfaces or objects are made aware of their existence.
      * The bean is made aware of any associated interfaces as well.
      * Any other methods, particularly custom created methods, are invoked
      * Then the bean is ready for use.
      * Once the bean is no longer used, it is marked for removal and a destroy method is invoked for the bean
      * Custom destroy methods are invoked, if any.
      * Bean is the destroyed.

* **What is the concept of component scanning and how would you set it up?**
  * Keywords, concepts, or topics that should be in the response:
    * You add `@ComponentScan` with the `@Configuration` method in order to allow Spring to scan all sub-packages within it. The output of the main() will contain all scanned beans.

* **What are the benefits and limitations of Java configuration?**
  * Keywords, concepts, or topics that should be in the response:
    * *Benefits:*
      * **Over XML:** Compile-Time Feedback due to Type-checking, Refactoring Tools for Java without special support/plugins work out of the box with Java Config
      * **Over Annotations:** Separation of concerns, Technology agnostic, Ability to integrate Spring with external libraries, The more centralized location of bean list
    * *Limitations:*
      * Configuration class/class methods cannot be final, All Beans have to be listed (for big applications, it might be a challenge compared to Component Scanning)

* **What does the `@Configuration` and `@Bean` annotations do?**
  * Keywords, concepts, or topics that should be in the response:
    * `@Configuration`: indicates that the class has `@Bean` definition methods
    * `@Bean`: indicates that a method produces a bean to be managed by the Spring container

* **What is `@Value` used for?**
  * Keywords, concepts, or topics that should be in the response:
    * Used at the field or method/constructor parameter level
    * Assigns default values to variables and method arguments and is commonly used for injecting values into configuration variables

* **What is Spring Expression Language? What can you reference using SpEL? What is the difference between `$` and `#` in `@value` expressions?**
  * Keywords, concepts, or topics that should be in the response:
    * *Spring Expression Language:* supports querying and manipulating an object graph at runtime
    * SpEl can refrence:
      * static field and method from class
      * Spring Bean property and methods
      * SpEL Variables
      * Object property and method on reference assgned to SpEL variables
      * Spring Application Environment variables
      * System properties and environment properties
    * *$:* can only do a Get
    * *#:* can do a Get and Set

## Spring MVC

### Spring MVC - CRITICAL

[Back to top](#unit-spring)

* **Explain the MVC architecture and how HTTP requests are processed in the architecture**
  * Keywords, concepts, or topics that should be in the response:
    * *Model View Controller*: Helps process requests and display information.
    * Client sends a req to a URL; hits a web container (like TomCat), looks into the web.xml and finds the mapped servlet, the Servlet processes the req.
    * To enable Spring MVC, we need to declare DispatcherServlet into the web.xml file
  * Possible follow-up questions:
    * **What is the role of the DispatcherServlet? What about the ViewResolver?**
      * *DispatcherServlet:* Receives all requests as Front Controller and provides a single entry point to the application. Mapping requests to correct Spring MVC controller. Consulting ViewResolvers to find correct View
      * *ViewResolver:* provides a mapping between view names and actual views. It enables you to render models in the browser without tying the implementation to specific view technology

* **What concerns is the controller layer supposed to handle vs the service layer?**
  * Keywords, concepts, or topics that should be in the response:
    * the controller is the manager, while the service is the worker
    * *Controller* handles incoming requests, does some checking/validation to figure out to which service(s) should the data from the request be sent to, and orchestrates those service calls
    * *Service* handles the business logic/algorithms/database calls/etc and returns the information back to the controller

* **What is the difference between `@Controller` and `@RestController`?**
  * Keywords, concepts, or topics that should be in the response:
    * `@Controller`: Marks class as Spring MVC controller
    * `@RestController`: Combination of `@Controller` and `@ResponseBody` for RESTful web services.

### Spring MVC - HIGH

[Back to top](#unit-spring)

* **How would you declare which HTTP requests you would like a controller to process?**
  * Keywords, concepts, or topics that should be in the response:
    * `@GetMapping`: mapping HTTP GET requests onto specific handler methods. Specifically, `@GetMapping` is a composed annotation that acts as a shortcut for `@RequestMapping`(method = RequestMethod. GET)
    * `@PostMapping`: mapping HTTP Post requests onto specific handler methods. Specifically, `@PostMapping` is a composed annotation that acts as a shortcut for `@RequestMapping`(method = RequestMethod. POST)
    * `@PutMapping`: mapping HTTP PUT requests onto specific handler methods. Specifically, `@PutMapping` is a composed annotation that acts as a shortcut for `@RequestMapping`(method = RequestMethod. PUT)

* **What is the control flow of the `DispatcherServlet`?**
  * Keywords, concepts, or topics that should be in the response:
    * Receives all requests as Front Controller  and provides a single entry point to the application
    * Mapping requests to correct Spring MVC controller
    * Consulting ViewResolvers to find correct View
    * Forwarding request to chosen View for rendering
    * Returning the response to the client
    * Creates web-context to initialize the web-specific beans like controllers, view resolvers, and handler mapping

* **How to declare the data format your controller expects from requests or will create in responses?**
  * Keywords, concepts, or topics that should be in the response:
    * Using the @RequestMapping annotation, you can specify what type of data format the controller will take by using the `consumes=""` parameter.
      * `@RequestMapping(value = "/clients", method = RequestMethod.POST, consumes="application/json")`
    * Using the `@ResponseBody` annotation, you can specify what you will get in the response by using the `ContentType type` parameter **OR** using the `@RequestMapping` and set a `produces=""` parameter.
      * `public void addClient(@RequestBody ContentType type, Model model) {}`
      * `@RequestMapping(value = "/clients-with-response-body", method = RequestMethod.GET, produces="application/json")`

### Spring MVC - REGULAR

[Back to top](#unit-spring)

* **How would you extract query and path parameters from a request URL in your controller?**
  * Keywords, concepts, or topics that should be in the response:
    * `@RequestParam` and `@PathVariable` can both be used to extract values from the request URI
    * `@RequestParam` bindings are similar to `@PathVariable` binding, however the query string mapping is not included in the handler mapping path attribute. The bindings are included in the parameter list much like `@PathVariable`

      * ```java
          public class MyController {
          @GetMapping(path="my_data") // query parameters aren't included in the mapping
          public ResponseEntity getData(@RequestParam LocalDateTime createdOn){...}
          }
        ```

    * `@PathVariable` is a two step process. First the variable path segment must be identified in the url path of the handler request mapping, then the segment is bound to a parameter in the handler's parameter list using `@PathVariable`

      * ```java
          public class MyController {
          @GetMapping(path="my_data/{id}") // {id} is the path variable
          public ResponseEntity getDataById(@PathVariable Integer id){...}
          }
        ```

* **How would you specify HTTP status codes to return from your controller?**
  * Keywords, concepts, or topics that should be in the response:
    * Use the `@ResponseStatus` annotation

* **How do you handle exceptions thrown in your code from your controller? What happens if you don’t set up any exception handling?**
  * Keywords, concepts, or topics that should be in the response:
  * Using HTTP Status Codes

    * ```java
      @ResponseStatus(value=HttpStatus.NOT_FOUND, reason="No such Order")  // 404
      public class OrderNotFoundException extends RuntimeException {
      // ...
      }
      ```

  * Using `@ExceptionHandler`

    * ```java
      @ExceptionHandler(DataIntegrityViolationException.class)
      public void conflict() {
      // Nothing to do
      }
      ```

  * Using `@ControllerAdvice` Classes: allows you to use exactly the same exception handling techniques but apply them across the whole application, not just to an individual controller

* **How would you consume an external web service using Spring?**
  * Keywords, concepts, or topics that should be in the response:
    * By using the RestTemplate which acts as a web client to make requests to web services. RestTemplate offers 3 types of methods for exchanging data with web service:
      * *ForEntity:* Request for the native exchange format returned by the server (JSON, XML, Text)
        * `getForEntity(...)`
      * *ForObject:* Deserialize the response into a Java pojo
        * `getForObject(...)`
      * *exchange:* Generic API for making web requests
        * `exchange(...)`
  * Possible follow-up questions:
    * **What are the advantages of using RestTemplate?**
      * It simplifies the interaction of RESTful Web Services on the client-side

## Spring Data

### Spring Data - CRITICAL

[Back to top](#unit-spring)

* **What is `@Query` used for?**
  * Keywords, concepts, or topics that should be in the response:
  * Used to write the sql queries in the spring boot application in order to get the desired result from the database
  * Can only be used to annotate repository interface methods

* **What is JPQL?**
  * Keywords, concepts, or topics that should be in the response:
  * Java Persistence Query Language
  * object-oriented query language which is used to perform database operations on persistent entities
  * Possible follow-up questions:
    * **What is the difference between JPQL and Native SQL?**
      * The main difference between SQL and JPQL is that SQL works with relational database tables, records and fields, whereas JPQL works with Java classes and objects. For example, a JPQL query can retrieve and return entity objects rather than just field values from database tables, as with SQL.

* **What is Spring ORM and Spring Data?**
  * Keywords, concepts, or topics that should be in the response:
  * *Spring ORM:* Object Relational Mapping. A technique or a Design Pattern used to access a relational database from an object-oriented language
  * *Spring Data:* provides standard implementation for common DAO methods allowing for the removal of the DAO implementation and only requiring the definition of the DAO interface methods
  * Possible follow-up questions:
    * **What is the difference between `JPARepository` and `CrudRepository`?**
      * | Topic | JPARepository | CrudRepository |
      | ------------------- | --------------- | ------------------ |
      | Hierarchy | JPA extend crudRepository and PagingAndSorting repository | Crud Repository is the base interface and it acts as a marker interface. |
      | Batch Support | JPA also provides some extra methods related to JPA such as delete records in batch and flushing data directly to a database. | It provides only CRUD functions like findOne, saves, etc. |
      | Pagination Support | JPA repository also extends the PagingAndSorting repository. It provides all the method for which are useful for implementing pagination. | Crud Repository doesn't provide methods for implementing pagination and sorting. |
      | Use Case | JpaRepository ties your repositories to the JPA persistence technology so it should be avoided | We should use CrudRepository or PagingAndSortingRepository depending on whether you need sorting and paging or not. |

### Spring Data - HIGH

[Back to top](#unit-spring)

* **What does `@Transactional` do?**
  * Keywords, concepts, or topics that should be in the response:
  * *@Transactional:* automatically handles transaction propagation, and isolation, commit, and rollback
  * best practice usage `@Transactional` should be used on your `@Service` beans since a transaction is a unit of work with its success or failure directly tied to the requirements of the application and not necessrarily to the model

* **What interfaces are available in Spring Data JPA?**
  * Keywords, concepts, or topics that should be in the response:
  * CrudRepository and PagingAndSortingRepository

* **What is the naming conventions for methods in Spring Data repositories?**
  * Keywords, concepts, or topics that should be in the response:
  * 2 parts sereprated by "By"
  * `List<User> findByName(String name)`
  * The first part — such as find — is the introducer, and the rest — such as ByName — is the criteria.
  * Spring Data JPA supports the introducers: find, read, query, count and get.

## Spring AOP

### Spring AOP - CRITICAL

[Back to top](#unit-spring)

* **What is "aspect-oriented programming"? Define an aspect.**
  * Keywords, concepts, or topics that should be in the response:
    * AOP breaks down program logic into parts (concerns). Allows for adaptability to change.
    * An *aspect* is a class that implements enterprise application concerns that cut across multiple classes, such as transaction management.

* **What is a cross-cutting concern? Give an example of a cross-cutting concern you could use AOP to address**
  * Keywords, concepts, or topics that should be in the response:
  * *Cross-Cutting Concern:* Same as an aspect: a concern which is applicable throughout the application. This affects the entire application.
  * Logging
  * Transaction management
  * Security
  * Caching
  * Error handling
  * Custom business rules
  * Performance monitoring

* **Define the following: Join point, Pointcut, Advice**
  * Keywords, concepts, or topics that should be in the response:
    * *Join point:* a specific point in the application such as method execution, exception handling, changing object variable values, etc. In Spring AOP a join point is always the execution of a method
    * *Pointcut:* an expression language of spring AOP which is basically used to match the target methods to apply the advice. It has two parts, one is the method signature comprising of method name and parameters. Other one is the pointcut expression which determines exactly which method we are applying the advice to
    * *Advice:* action taken by an aspect at a particular join point.

* **What are the different types of advice? What is special about the `@Around` advice? How is the ProceedingJoinPoint used?**
  * Keywords, concepts, or topics that should be in the response:
  * *Before advice:* Advice that executes before a join point, but which does not have the ability to prevent execution flow proceeding to the join point (unless it throws an exception).
  * *After returning advice:* Advice to be executed after a join point completes normally: for example, if a method returns without throwing an exception.
  * *After throwing advice:* Advice to be executed if a method exits by throwing an exception.
  * *After (finally) advice:* Advice to be executed regardless of the means by which a join point exits (normal or exceptional return).
  * *Around advice:* Advice that surrounds a join point such as a method invocation. This is the most powerful kind of advice. Around advice can perform custom behavior before and after the method invocation. It is also responsible for choosing whether to proceed to the join point or to shortcut the advised method execution by returning its own return value or throwing an exception

### Spring AOP - REGULAR

[Back to top](#unit-spring)

* **Explain the pointcut expression syntax**
  * Keywords, concepts, or topics that should be in the response:
  * Designator: a keyword telling Spring AOP what to match (ex: excecution, within, this, target)
  * Pattern: selects join points of the type determined by the pointcut designator
  * `execution( [scope] [ReturnType] [FullClassName].[MethodName] ([Arguments]) throws [ExceptionType])`
  * Possible follow-up questions:
    * **What will the following pointcut expressions return?**
      * `execution(public String getName())` 
        * This point cut specifies a public method (note this public access modifier is optional) named getName that returns String data
      * `execution(public * getName())`
        * This pointcut specifies any public method that returns any type of data, so long as the method is named getName.
      * `execution(* get*())`
        * the pointcut matches a method of any return type whose name begins with 'get'
      * `execution(* set*(*))`
        * This pointcut matches methods whose name begins with 'set' which take one argument of any type
      * `execution(void com.revature.*.set*(..))`
        * This pointcut matches any method who name begins with 'set' (which returns void) within any package from com.revature (such as com.revature.service, com.revature.dao, com.revature.examples, etc...), and can take any number of parameters.

* **What visibility / access modifier must Spring bean methods have to be proxied using Spring AOP?**
  * Keywords, concepts, or topics that should be in the response:
  * Only public methods of Spring beans will be proxied. The call to the public method must me made outside of the Spring bean.

### Spring Data - REGULAR

[Back to top](#unit-spring)

* **What is the `PlatformTransactionManager`?**
  * Keywords, concepts, or topics that should be in the response:
  * *PlatformTransactionManager:* the Spring transaction client API that provides the classic transaction client operations: begin, commit and rollback. In other words, this interface provides the essential methods for controlling transactions at runtime.

* **What is a `PersistenceContext`?**
  * Keywords, concepts, or topics that should be in the response:
  * The persistence context is the first-level cache where all the entities are fetched from the database or saved to the database
  * keeps track of any changes made into a managed entity. If anything changes during a transaction, then the entity is marked as dirty. When the transaction completes, these changes are flushed into persistent storage

* **What is the Template design pattern and what is the JDBC template?**
  * Keywords, concepts, or topics that should be in the response:
  * *Template Design Pattern:* a behavioral design pattern that allows you to defines a skeleton of an algorithm in a base class and let subclasses override the steps without changing the overall algorithm's structure
  * *JDBC Template:* simplifies the the use of JDBC and helps avoid common errors. It executes core JDBC workflow, leaving the app code to provide SQL and extract results. It extends the JdbcAccessor class and Implements the JdbcOperations interface.

* **What is transaction propagation?**
  * Keywords, concepts, or topics that should be in the response:
  * indicates if any component or service will or will not participate in a transaction and how will it behave if the calling component/service already has or does not have a transaction created already

## Spring Boot

### Spring Boot - CRITICAL

[Back to top](#unit-spring)

* **How does Boot's autoconfiguration work?**
  * Keywords, concepts, or topics that should be in the response:
  * To enable auto configuration in Spring Boot, you need to include `@EnableAutoConfiguration` or `@SpringBootApplication` on a class
  * `@EnableAutoConfiguration` then the class that the annotation is on must also be annotated with `@Configuration`
  * `@SpringBootApplication` is the combination of the `@SpringBootConfiguration`, `@EnableAutoConfiguration`, and `@ComponentScan` annotations

* **What are the benefits and features of using Spring boot?**
  * Keywords, concepts, or topics that should be in the response:
  * Spring Boot works well with several servlet containers
  * Bootstrapping saves memory space
  * Decreased boilerplate code
  * No XML configuration required
  * POM dependency management
  * Possible follow-up questions:
    * **What is the advantage of having an embedded Tomcat server?**
      * offers a way to package Java web applications that is consistent with a microservices-based approach to software development. It also makes it easier to distribute Java web applications through Docker containers and manage them through a container orchestration service, such as Kubernetes
      * Isolation: if one server fails, the application won't fail

* **What is the Spring Boot actuator? What information can it give you?**
  * Keywords, concepts, or topics that should be in the response:
  * *Spring Boot Actuator* is used to expose operational information about the running application — health, metrics, info, dump, env, etc. It uses HTTP endpoints or JMX beans to enable us to interact with it

* **What files would you use to configure Spring Boot applications?**
  * Keywords, concepts, or topics that should be in the response:
  * Application.properties or application.yaml

### Spring Boot - HIGH

[Back to top](#unit-spring)

* **How is Spring Boot different from legacy Spring applications? What does it mean that it is "opinionated"?**
  * Keywords, concepts, or topics that should be in the response:
  * Spring Boot is built on top of the conventional spring framework. It has all of the functionality of the legacy Spring applications but provides autoconfiguration capabilities.
  * *opinionated:* a strategy to eliminate boilerplate and configurations meant to improve unit testing, development, and integration test procedures. It decides the defaults to use for configuration and the packages to install based on the dependencies requirement.

* **What annotation would you use for Spring Boot apps? What does it do behind the scenes?**
  * Keywords, concepts, or topics that should be in the response:
  * `@EnableAutoConfiguration`: configures Spring, based on the jar dependencies that you have added
  * `@Required`: It applies to the bean setter method. It indicates that the annotated bean must be populated at configuration time with the required property, else it throws an exception `BeanInitilizationException`
  * `@Autowired`: It is used to autowire spring bean on setter methods, instance variable, and constructor
  * `@Configuration`: It is a class-level annotation. The class annotated with `@Configuration` used by Spring Containers as a source of bean definitions
  * `@ComponentScan`: It is used when we want to scan a package for beans
  * `@Bean`: It is a method-level annotation. It is an alternative of XML `<bean>` tag.

### Spring Boot - REGULAR

[Back to top](#unit-spring)

* **What is the significance of the Spring Boot starter POM?**
  * Starter POMs are a set of convenient dependency descriptors that you can include in your application. It allows the developer to not have to worry about defining dependency discriptors

* **What does "convention over configuration" mean?**
  * A design philosophy and technique that seeks to apply defaults that can be implied from the structure of the code instead of requiring explicit code.

* **What is the benefit of using Spring Boot profiles?**
  * It provides an efficient way to bundle properties according to functionality.

## Spring Security

[Back to top](#unit-spring)

* What is Spring Security? What features does it provide?
  * Security framework for Java applications.
  * Provides comprehensive security services for Java EE-based enterprise software applications.
  * Helps secure your applications against different types of attacks such as authentication, authorization, session management, and more.
  * Offers features like authentication, authorization, session management, CSRF protection, and more out-of-the-box.
  * Easily integrates with other Spring frameworks like Spring MVC, Spring Boot, and more.

* What is the difference between authentication and authorization?
  * **Authentication**:
    * Process of verifying the identity of a user or entity.
    * Answers the question: "Who are you?"
    * Examples include username/password, biometric scans, tokens, etc.
    * Validates the user's credentials to ensure they are who they claim to be.
  * **Authorization**:
    * Process of determining what actions or resources a user or entity is allowed to access.
    * Answers the question: "What are you allowed to do?"
    * Involves checking permissions and privileges against the authenticated user.
    * Determines whether the authenticated user has the necessary permissions to perform a specific action or access a particular resource.

* How can you securely store passwords in a database?
  * **Hashing**:
    * Use a strong cryptographic hash function like bcrypt, PBKDF2, or Argon2.
    * Hash the password before storing it in the database.
    * Salting: Add a unique random salt to each password before hashing to prevent rainbow table attacks.
  * **Avoid Plain Text**:
    * Never store passwords in plain text.
    * Ensure passwords are always hashed before storage.
  * **Key Stretching**:
    * Use algorithms that are intentionally slow to compute, making brute-force attacks more difficult.
  * **Constantly Updated Security**:
    * Keep abreast of latest security practices and update hashing algorithms accordingly.
  * **Defense in Depth**:
    * Implement additional layers of security such as two-factor authentication (2FA) to further protect user accounts.
  * **Secure Access Controls**:
    * Limit access to the database and ensure proper permissions are set for handling passwords.

* How does RBAC (Role-based access control) work?
  * **Roles**:
    * Define sets of permissions based on job functions or responsibilities.
    * Users are assigned to one or more roles.
  * **Permissions**:
    * Associated with each role.
    * Specify what actions or operations a role can perform.
  * **Access Control**:
    * Users gain access to resources based on their assigned roles.
    * Access is granted or denied based on the permissions associated with the user's role.
  * **Hierarchy**:
    * Roles can be organized in a hierarchical structure.
    * Inheritance of permissions: Higher-level roles inherit permissions from lower-level roles.
  * **Centralized Administration**:
    * Simplifies management by centralizing access control policies and permissions.
  * **Dynamic Access Control**:
    * Roles and permissions can be dynamically assigned based on user attributes or context.
  * **Example**:
    * In a system, an "Admin" role might have permissions to create, update, and delete users, while a "User" role might only have permissions to view data.

* What are some common configuration properties for Spring Security?
  * `spring.security.user.*`: Configure in-memory user details.
  * `spring.security.enabled`: Enable or disable Spring Security.
  * `spring.security.ignored`: Paths to ignore from security filters.
  * `spring.security.logout.*`: Customize logout behavior.
  * `spring.security.oauth2.*`: Configuration for OAuth2 authentication.
  * `spring.security.filter.order`: Set the order of the security filter chain.
  * `spring.security.session.*`: Session management configuration.
  * `spring.security.csrf.*`: CSRF protection configuration.
  * `spring.security.headers.*`: HTTP security headers configuration.
  * `spring.security.require-ssl`: Require SSL for all requests.
  * `spring.security.authentication.*`: Authentication manager configuration.

* What is a JWT? What are the different components of a token?
  * **JWT (JSON Web Token)**:
    * Compact, URL-safe means of representing claims to be transferred between two parties.
    * Often used for authentication and authorization in web applications.
  * **Components of a JWT**:
    * **Header**: Contains metadata about the type of token and the signing algorithm used.
    * **Payload**: Contains claims, which are statements about an entity (user) and additional data.
    * **Signature**: Used to verify that the token was not changed during transmission and was issued by a trusted party.
      * Created by combining the header, payload, and a secret key, then hashing the result.
  * Where should you store a JWT?
    * Cookies or local storage
  * How can you configure Spring Security to verify the tokens?
    * Use **JWT Authentication**:
      * Configure a **JWT filter** to intercept requests and validate JWT tokens.
      * Define a **custom authentication provider** to handle authentication using JWT tokens.
    * **JWT Decoder**:
      * Provide a **JWT decoder** to decode and verify the JWT tokens.
    * **Authentication Manager Configuration**:
      * Configure the authentication manager to use the custom authentication provider for JWT authentication.
    * **Security Configuration**:
      * Define security configurations to specify which endpoints require authentication and authorization.
    * **Token Validation**:
      * Ensure token validation includes checking the token's signature, expiration, and any additional claims.
    * **Error Handling**:
      * Implement error handling for invalid or expired tokens.
    * **Integration with Spring Boot**:
      * Leverage Spring Boot's auto-configuration to simplify JWT configuration.

* How is basic authentication different from token-based authentication?
  * **Basic Authentication**:
    * Sends credentials (username/password) with each request.
    * Uses HTTP headers (Authorization: Basic) to transmit credentials.
    * Stateless: Server does not store any session information.
    * Less secure: Vulnerable to eavesdropping if not used over HTTPS.
    * Simple implementation but less flexible.
  * **Token-based Authentication**:
    * Sends a token with each request instead of credentials.
    * Tokens are typically JSON Web Tokens (JWT) or similar formats.
    * Tokens contain encoded user information and are digitally signed.
    * Stateless or stateful: Tokens can be stored on the client-side (stateless) or server-side (stateful).
    * More secure: Tokens can be encrypted and have short lifetimes, reducing the risk of misuse.
    * More flexible: Can include additional information (claims) and support various authentication mechanisms like OAuth2.

* What do the `@Secured` and `@PreAuthorize` annotations do?
  * **`@Secured`**:
    * Annotation used to specify which roles or authorities are allowed to access a method or endpoint.
    * Applied at the method level.
    * Requires a list of role names or authority names as arguments.
    * Example: `@Secured({"ROLE_USER", "ROLE_ADMIN"})`
  * **`@PreAuthorize`**:
    * Annotation used for defining method-level security rules using Spring Expression Language (SpEL).
    * Provides more fine-grained control over method access based on conditions.
    * Allows using dynamic expressions to determine access.
    * Example: `@PreAuthorize("hasRole('ROLE_ADMIN') or hasRole('ROLE_MANAGER')")`

* How would you implement custom authentication with the `UserDetails` and `UserDetailsService`?
  1. **Create a Custom `UserDetails` Class**:
     * Implement the UserDetails interface to define custom user details.
     * Provide implementations for getUsername(), getPassword(), getAuthorities(), etc.
  
  2. **Implement `UserDetailsService`**:
     * Create a class implementing the UserDetailsService interface.
     * Override the loadUserByUsername() method to load user details by username from the data source (e.g., database).
     * Retrieve user details, including username, password, and authorities.
     * Create and return a UserDetails object populated with the retrieved user details.

  3. **Configure Authentication Provider**:
     * Define a custom authentication provider by extending AbstractUserDetailsAuthenticationProvider.
     * Override the additionalAuthenticationChecks() method to perform additional authentication checks if necessary.
     * Set the userDetailsService property to the custom UserDetailsService implementation.

  4. **Configure Spring Security**:
     * Configure Spring Security to use the custom authentication provider.
     * Specify the authentication manager bean with the custom authentication provider.
     * Configure security rules and endpoints as needed.

  5. **Authentication Flow**:
     * When a user attempts to authenticate, Spring Security invokes the loadUserByUsername() method of the UserDetailsService to retrieve user details.
     * The custom authentication provider then validates the user's credentials against the UserDetails object retrieved from the UserDetailsService.
     * If authentication is successful, the user is granted access; otherwise, authentication fails.
