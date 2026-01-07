## Unit

# Spring Boot

## Links
* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions
* **How does Boot's autoconfiguration work?**
  * To enable auto configuration in Spring Boot, you need to include `@EnableAutoConfiguration` or `@SpringBootApplication` on a class
  * `@EnableAutoConfiguration` then the class that the annotation is on must also be annotated with `@Configuration`
  * `@SpringBootApplication` is the combination of the `@SpringBootConfiguration`, `@EnableAutoConfiguration`, and `@ComponentScan` annotations

* **What are the benefits and features of using Spring boot?**
  * Spring Boot works well with several servlet containers
  * Bootstrapping saves memory space
  * Decreased boilerplate code
  * No XML configuration required
  * POM dependency management
  * Possible follow-up questions:
  * **What is the advantage of having an embedded Tomcat server?**
    * offers a way to package Java web applications that is consistent with a microservices-based approach to software development. It also makes it easier to distribute Java web applications through Docker containers and manage them through a container orchestration service, such as Kubernetes
    * Isolation: if one server fails, the application won't fail

* **What files would you use to configure Spring Boot applications?**
  * `Application.properties` or `application.yaml`

* **What is Spring Initializr and how do you use it to create a Spring Boot app?**
  * Spring Initializr is a web-based tool at start.spring.io
  * It allows developers to generate a pre-configured Spring Boot application by choosing dependencies, packaging type, Java version, etc.
  * Outputs a downloadable ZIP that includes a full project structure

* **What are common Spring Boot Starters and what do they include?**
  * `spring-boot-starter-web`: Includes Tomcat, Spring MVC, Jackson for RESTful APIs
  * `spring-boot-starter-data-jpa`: Includes Spring Data JPA, Hibernate, and a database driver

* **How is Spring Boot different from legacy Spring applications? What does it mean that it is "opinionated"?**
  * Spring Boot is built on top of the conventional spring framework. It has all of the functionality of the legacy Spring applications but provides autoconfiguration capabilities.
  * *opinionated:* a strategy to eliminate boilerplate and configurations meant to improve unit testing, development, and integration test procedures. It decides the defaults to use for configuration and the packages to install based on the dependencies requirement.

## Stretch Questions
* **What is the Spring Boot actuator? What information can it give you?**
  * *Spring Boot Actuator* is used to expose operational information about the running application — health, metrics, info, dump, env, etc. It uses HTTP endpoints or JMX beans to enable us to interact with it

* **How do you use DevTools in a Spring project?**
  * Add `spring-boot-devtools` as a dependency
  * Enables automatic restarts, live reload, and configurations for development only

* **How do you use Lombok in a Spring project?**
  * Add Lombok to the dependencies (either via Maven or Gradle)
  * Use annotations like `@Getter`, `@Setter`, `@AllArgsConstructor`, `@NoArgsConstructor`, `@Builder` to reduce boilerplate code
  * Requires Lombok plugin in the IDE for proper annotation processing

* **What is the significance of the Spring Boot starter POM?**
  * Starter POMs are a set of convenient dependency descriptors that you can include in your application. It allows the developer to not have to worry about defining dependency discriptors

* **What does "convention over configuration" mean?**
  * A design philosophy and technique that seeks to apply defaults that can be implied from the structure of the code instead of requiring explicit code.

* **What is the benefit of using Spring Boot profiles?**
  * It provides an efficient way to bundle properties according to functionality.

* **What annotation would you use for Spring Boot apps? What does it do behind the scenes?**
  * `@EnableAutoConfiguration`: configures Spring, based on the jar dependencies that you have added
  * `@Required`: It applies to the bean setter method. It indicates that the annotated bean must be populated at configuration time with the required property, else it throws an exception `BeanInitilizationException`
  * `@Autowired`: It is used to autowire spring bean on setter methods, instance variable, and constructor
  * `@Configuration`: It is a class-level annotation. The class annotated with `@Configuration` used by Spring Containers as a source of bean definitions
  * `@ComponentScan`: It is used when we want to scan a package for beans
  * `@Bean`: It is a method-level annotation. It is an alternative of XML `<bean>` tag.
