## Unit

# Spring Testing

## Links
* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions
* **What is unit testing and why is it important in Spring applications?**
  * Unit testing is the process of testing individual units or components of a software application.
  * It ensures that each component functions correctly in isolation.
  * In Spring, it helps validate the behavior of services, controllers, and repositories without relying on the entire application context.

* **What is mocking, and how do you intercept method calls in Spring unit tests?**
  * Mocking is the practice of replacing real objects with simulated versions to isolate behavior.
  * In Spring, use libraries like Mockito to mock dependencies.
  * Use `when(...).thenReturn(...)` or `@Mock`, `@InjectMocks` annotations to control method behavior in tests.

* **What is the unit test structure (Arrange, Act, Assert)?**
  * Arrange: set up test data and mock dependencies.
  * Act: execute the method under test.
  * Assert: verify the result using assertions like `assertEquals`, `assertTrue`, etc.

* **How do you implement a test suite in Spring Boot?**
  * Use `@SpringBootTest` to load the full application context.
  * Use `@RunWith(SpringRunner.class)` or JUnit 5's `@ExtendWith(SpringExtension.class)`.
  * Organize related test classes into test suites using `@Suite` in JUnit.
  * Group test methods using nested classes or test naming conventions.

## Preferred Questions
* **How do you write unit tests for the presentation layer (controllers) in Spring?**
  * Use `@WebMvcTest(Controller.class)` for testing MVC controllers.
  * Mock the service layer using `@MockBean`.
  * Use `MockMvc` to simulate HTTP requests and assert results.

* **How do you test the data layer in Spring?**
  * Use `@DataJpaTest` to configure an in-memory database for repository testing.
  * Only repository beans are loaded; useful for validating JPQL/SQL queries.

* **How do you test the service layer in Spring?**
  * Use `@Mock` for dependencies and `@InjectMocks` for the service under test.
  * Test service logic in isolation from the data and controller layers.

* **How do you test for exceptions in Spring unit tests?**
  * Use `assertThrows(Exception.class, () -> { ... })` in JUnit 5.
  * Alternatively, use `ExpectedException` rule in JUnit 4.

## Stretch Questions
* **What is Test-Driven Development (TDD) and how is it applied in Spring?**
  * TDD is a software development practice where tests are written before writing the actual code.
  * In Spring, write a failing test, implement code to make it pass, then refactor.

* **How do you configure a test environment using properties and profiles in Spring Boot?**
  * Use `application-test.properties` or `application-test.yml` for test-specific configs.
  * Activate the profile using `@ActiveProfiles("test")` in test classes.
  * Helps isolate test settings like DB connection, ports, or logging levels.
