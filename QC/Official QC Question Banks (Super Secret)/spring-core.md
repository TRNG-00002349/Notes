## Unit

# Spring Core

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions

* **What are Spring Projects and Spring Modules?**
    * *Spring Project:* Provide solutions to other issues faced by enterprise applications; Spring Boot, Spring Data, Spring Cloud, Spring HATEOAS
    * *Spring Module:* All Spring Modules share the same release version as the Spring Framework. They are part of the same project; Spring Core, Spring AOP, Spring Web MVC, Spring DAO, Spring ORM, Spring context, and Spring Web flow

* **What are the benefits of Spring?**
    * Core technologies: dependency injection, events, resources, validation, data binding, type conversion, SpEL, AOP.
    * Testing: mock objects, TestContext framework, Spring MVC Test, WebTestClient
    * Data Access: transactions, DAO support, JDBC, ORM, Marshalling XML

* **What is IOC and what does the IOC Container do?**
    * IoC: Inversion of control; Manages Dependency Injections; allows for loose coupling of objects
    * IoC Container: Creates the objects (beans), configures and assembles their dependencies, and manages their entire life cycle  
    * Possible follow-up questions:
    * **How does the IoC Container get the information about the beans?**
      * Configuration in the XML file or annotations

* **What is dependency injection and what are some of the benefits of using dependency injection?**
    * DI is when one object relies on another objects to run. Allows for objects that are dependent on the creation of another one to be loosely coupled instead of fully dependent

* **What types of dependency injection does Spring support, and when should you use constructor, setter, or field injection?**
    * **Setter Injection:**
        * Dependency is provided via a public setter method.
        * Configured in XML using `<property>` tag or via `@Autowired` on a setter method.
        * **Use when:** The dependency is optional or can be changed after object creation.
    * **Constructor Injection:**
        * Dependencies are passed through the constructor.
        * Configured in XML using `<constructor-arg>` tag or via `@Autowired` on the constructor (or just by using a single constructor).
        * **Use when:** Dependencies are required and should not change; promotes immutability and makes testing easier.
    * **Field Injection:**
        * Dependency is injected directly into the field using `@Autowired`.
        * **Use when:** You want quick prototyping or need brevity, but **not recommended** for production code due to poor testability and lack of clarity.
        * **Limitations:** Cannot be used on `final` fields; not ideal for unit testing.

* **What is bean wiring? What about autowiring?**
    * *Bean Wiring:* the process of combining beans with Spring container. You should tell the container what beans are needed and how the container should use dependency injection to tie them together
    * *Autowiring:* the `@Autowired` annotation is used to inject the dependency into a bean (equivalent to ref XML tag/attribute); The Spring container can auto wire on the basis of the following parameters: *byName, byType, constructor, and autodetect*.
    * Possible follow-up questions:
    * **What are the different ways that Spring can wire beans?**
      * XML: The configuration file contains the definitions of the beans. When the Spring-based software application starts up, the beans are called and based on the Dependency Injection (DI), the beans are wired. In the file, the element needs to be declared and the `<constructor-arg>` and `<property>` elements need to be used.
      * Through a Java Class: A Spring Configuration class needs to be created and the class `@Configuration` needs to be annotated. The `@Configuration` tells Spring that the beans that should be wired are configured within this class.

* **What is the concept of component scanning and how would you set it up?**
    * You add `@ComponentScan` with the `@Configuration` method in order to allow Spring to scan all sub-packages within it. The output of the main() will contain all scanned beans.

* **What is the Spring Bean lifecycle?**
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

* **What are lifecycle hooks in a Spring bean, and how do you implement them (especially `InitializingBean` and `DisposableBean`)?**
    * Lifecycle hooks let developers run logic **after a bean is initialized** and **before it is destroyed**.
    * These are typically used for resource setup (e.g. DB connections) and cleanup (e.g. closing files).
    * Spring supports three main ways to hook into the lifecycle:
      * **`InitializingBean`** interface – implement `afterPropertiesSet()` for post-injection logic.
      * **`DisposableBean`** interface – implement `destroy()` to clean up before shutdown.
      * **Annotations**:
        * `@PostConstruct` – run logic after dependencies are injected (preferred alternative to `InitializingBean`).
        * `@PreDestroy` – run logic before the bean is destroyed (preferred alternative to `DisposableBean`).
      * **XML configuration**:
        * Use `init-method` and `destroy-method` attributes to declare lifecycle methods declaratively.
    * These hooks are part of the broader **Spring Bean lifecycle**, which includes instantiation, dependency injection, and destruction phases.

* **What are the scopes of Spring beans? Which is default?**
    * singleton (Default): Returns a single bean instance per Spring IoC container.
    * prototype: Returns a new bean instance each time when requested.
    * request: Returns a single instance for every HTTP request call.
    * session: Returns a single instance for every HTTP session.
    * global session: global session scope is equal as session scope on portlet-based web applications.

## Preferred Questions

* **What are Sterotype annotations? List some stereotype annotations. What are the differences between these?**
    * *Sterotype annotations:* markers for any class that fulfills a role within an application. This helps remove, or at least greatly reduce, the Spring XML configuration required for these components
      * `@Component`: generic stereotype used to declare an objects as a bean
      * `@Service`: marks a class as a Service for an application
      * `@Repository`: marks a class to be used as a for use with storing data within a repository or database; provides benefits for objects that would otherwise be utilized as a Data Access Object (DAO)
      * `@Controller`:  marks a class as a Spring MVC Controller which allow the use of handler mapping annotations; autodetected through classpath scanning

* **What are some differences between BeanFactory and ApplicationContext? Which one eagerly instantiates your beans?**
    * *Bean Factory:* loads beans on demand (lazy), more lightweight (better in memory-constrained systems), only supports Singleton and Prototype bean scopes
    * *Application Context:* loads beans on startup (eager), preferred method in enterprise applications, can handle all bean scopes, can use annotation-based dependency injection

* **What is the Spring XML configuration and how to implement it**
    * Spring beans can be defined in an external XML file, usually `applicationContext.xml` or similar.
    * Beans are configured using the `<bean>` tag with attributes like `id`, `class`, and dependency injection via `<property>` or `<constructor-arg>`.
    * XML config supports features like component scanning (`<context:component-scan>`), lifecycle methods, and bean scopes.

* **What is the Spring Java Configuration class and how to implement it**
    * Java-based config uses classes annotated with `@Configuration` and methods annotated with `@Bean` to define beans.
    * Enables type safety, autocompletion, and better refactoring support in modern IDEs.
    * Supports full control of bean instantiation, dependencies, and lifecycle behavior.

* **What are Spring environments profiles and properties**
    * **Profiles** allow selective bean registration using `@Profile("dev")`, `@Profile("prod")`, etc., activated via `spring.profiles.active`.
    * Useful for environment-specific configurations (e.g., dev vs. prod DB).
    * **Properties** externalize configuration using `.properties` or `.yml` files.
    * Inject values using `@Value("${property.name}")` or `@ConfigurationProperties`.
    * Supports separation of config from code, easier deployment across environments.

## Stretch Questions

* **What does it mean to translate Spring bean definitions between configuration methods, and how is it done?**
    * Refers to converting bean definitions across XML, Java Configuration, and Annotation-based methods.
    * Spring beans can be defined using **XML**, **Java Configuration (`@Configuration` + `@Bean`)**, or **annotations (`@Component`, `@Service`, etc.)**.
    * You can use:
      * `<bean>` in XML
      * `@Bean` methods in `@Configuration` class
      * Annotated classes with `@Component` and component scanning
    * Example translation of a service bean:
      * **XML:**

        ```xml
        <bean id="myService" class="com.example.MyService"/>
        ```

      * **Java Config:**

        ```java
        @Bean
        public MyService myService() {
            return new MyService();
        }
        ```

      * **Annotation-based:**

        ```java
        @Component
        public class MyService { }
        ```

* **What are the benefits and limitations of Java configuration?**
    * *Benefits:*
      * **Over XML:** Compile-Time Feedback due to Type-checking, Refactoring Tools for Java without special support/plugins work out of the box with Java Config
      * **Over Annotations:** Separation of concerns, Technology agnostic, Ability to integrate Spring with external libraries, The more centralized location of bean list
    * *Limitations:*
      * Configuration class/class methods cannot be final, All Beans have to be listed (for big applications, it might be a challenge compared to Component Scanning)

* **What does the `@Configuration` and `@Bean` annotations do?**
    * `@Configuration`: indicates that the class has `@Bean` definition methods
    * `@Bean`: indicates that a method produces a bean to be managed by the Spring container

* **What is `@Value` used for?**
    * Used at the field or method/constructor parameter level
    * Assigns default values to variables and method arguments and is commonly used for injecting values into configuration variables

* **What is Spring Expression Language? What can you reference using SpEL? What is the difference between `$` and `#` in `@value` expressions?**
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
