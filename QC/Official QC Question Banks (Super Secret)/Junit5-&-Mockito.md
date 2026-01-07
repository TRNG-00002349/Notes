## Unit

# Junit5 & Mockito

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions

[Back to top](#unit)

* **What is the purpose and what are the benefits of Unit Testing?**
  * Keywords, concepts, or topics that should be in the response:
    * Testing individual components in isolation
    * Early detection of defects
    * Supports Test Driven Development (TDD)
    * Improves code quality and maintainability
    * Identifies common developer errors (e.g., logic flaws, wrong variables)
  * Possible follow-up questions
    * **How does Test Driven Development (TDD) relate to Unit Testing?**
      * Keywords, concepts, or topics that should be in the response:
        * Tests written before code
        * Guides development process
        * Encourages modular, testable code
        * Enhances collaboration between testers and developers
* **What is Regression Testing and why is it important in software development?**
  * Keywords, concepts, or topics that should be in the response:
    * Ensures new code doesn’t break existing functionality
    * Uses previously written unit tests
    * Validates that all requirements are still met
    * Detects defects introduced by recent changes
  * Possible follow-up questions
    * **How do Unit Tests support Regression Testing?**
      * Keywords, concepts, or topics that should be in the response:
        * Reuse of existing test cases
        * Quick validation of system integrity
        * Automated detection of regressions
        * Confidence in code changes
* **What is Retesting and how does it differ from Regression Testing?**
  * Keywords, concepts, or topics that should be in the response:
    * Re-running failed tests after defect fixes
    * Confirms that specific bugs have been resolved
    * Smaller in scope than Regression testing
    * Focused on validating fixes, not preventing new issues
* **What types of defects are typically discovered through Unit Testing?**
  * Keywords, concepts, or topics that should be in the response:
    * Flow control issues
    * Improper logic
    * Use of incorrect variables
    * Malformed environment variables
    * Misconfigured properties
* **How do you define a test case in JUnit 5?**
  * Keywords, concepts, or topics that should be in the response:
    * Use of `@Test` annotation
    * Method-level annotation
    * Belongs to `org.junit.jupiter.api` package
    * Recognized as a test case by the JUnit framework
* **What is the structure of a basic JUnit 5 test class?**
  * Keywords, concepts, or topics that should be in the response:
    * Class with one or more methods annotated with `@Test`
    * Import from `org.junit.jupiter.api.Test`
    * Test methods are `void` and take no parameters
    * Can include setup and teardown methods
* **What is Mockito and how is it used in unit testing?**
  * Keywords, concepts, or topics that should be in the response:
    * Java testing framework
    * Supports mocking and stubbing
    * Used when code structure complicates direct unit testing
    * Enables isolation of components during testing
* **How do you create and inject mock objects using Mockito?**
  * Keywords, concepts, or topics that should be in the response:
    * `Mockito.mock()` for manual creation
    * `@Mock` and `@InjectMocks` annotations
    * `MockitoAnnotations.openMocks(this)` for initialization
    * Constructor, setter, or field injection
* **What is a Spy in Mockito and how does it differ from a Mock?**
  * Keywords, concepts, or topics that should be in the response:
    * Spy wraps a real object
    * Allows partial mocking
    * Can call real methods and stub others
    * Useful for verifying behavior while preserving logic
  * Possible follow-up questions
    * **When would you choose to use a Spy instead of a Mock?**
      * Keywords, concepts, or topics that should be in the response:
        * Need to test real behavior with some overrides
        * Want to preserve original method logic
        * Useful in legacy or complex systems
* **How do you test for exceptions in JUnit 5?**
  * Keywords, concepts, or topics that should be in the response:
    * Use of `assertThrows()` method
    * Part of `org.junit.jupiter.api.Assertions`
    * Lambda expression to encapsulate code
    * Test fails if exception is not thrown
* **What are setup and teardown methods in JUnit 5 and how are they used?**
  * Keywords, concepts, or topics that should be in the response:
    * Lifecycle annotations from `org.junit.jupiter.api`
    * `@BeforeEach` and `@AfterEach` for per-test setup and cleanup
    * `@BeforeAll` and `@AfterAll` for one-time setup and teardown
    * Used to manage test resources and environment
  * Possible follow-up questions
    * **When should you use `@BeforeAll` and `@AfterAll` instead of `@BeforeEach` and `@AfterEach`?**
      * Keywords, concepts, or topics that should be in the response:
        * For expensive or shared setup tasks
        * Run once before/after all tests
        * Ideal for initializing shared resources
        * Requires static methods or `@TestInstance(Lifecycle.PER_CLASS)`
    * **What are the method requirements for lifecycle annotations in JUnit 5?**
    * Keywords, concepts, or topics that should be in the response:
        * `@BeforeAll` and `@AfterAll` must be static unless using `@TestInstance(Lifecycle.PER_CLASS)`
        * `@BeforeEach` and `@AfterEach` have no special requirements
        * All methods must be `void` and take no parameters
* **How does JUnit 5 handle lifecycle method inheritance?**
  * Keywords, concepts, or topics that should be in the response:
    * Lifecycle methods can be inherited from parent classes
    * Parent methods run before child methods by default
    * Can be overridden in child classes
    * Supports reusable test setup logic
* **What is method stubbing in Mockito and how is it used?**
  * Keywords, concepts, or topics that should be in the response:
    * Uses `when(...).thenReturn(...)` pattern
    * Defines behavior of mock methods
    * Prevents actual method execution
    * Returns predefined values for specific arguments
  * Possible follow-up questions
    * **Why is it important to match arguments exactly when stubbing methods in Mockito?**
      * Keywords, concepts, or topics that should be in the response:
        * Argument values determine stub behavior
        * Mismatched arguments return default values
        * Ensures test reliability and accuracy
        * Helps simulate realistic scenarios
* **What makes a stubbed method effective in a unit test?**
  * Keywords, concepts, or topics that should be in the response:
    * Returns values that reflect expected behavior
    * Supports isolation of the unit under test
    * Avoids reliance on actual implementation
    * Enhances test clarity and focus
  * Possible follow-up questions
    * **What are the risks of using unrealistic return values in stubs?**
      * Keywords, concepts, or topics that should be in the response:
        * Misrepresents application behavior
        * Leads to misleading test results
        * Reduces test validity
        * May hide real defects
* **What are parameterized tests in JUnit 5 and why are they useful?**
  * Keywords, concepts, or topics that should be in the response:
    * Run the same test logic with different inputs
    * Supports data-driven testing
    * Reduces code duplication
    * Provided by `junit-jupiter-params` module
* **How can you customize the names of parameterized test runs in JUnit 5?**
  * Keywords, concepts, or topics that should be in the response:
    * Use `name` attribute in the test annotation
    * Placeholders like `{index}`, `{0}`, `{arguments}`
    * Improves test readability and reporting
    * Helps identify failing cases easily
  * Possible follow-up questions
    * **What are some common placeholders used in test names?**
      * Keywords, concepts, or topics that should be in the response:
        * `{index}` for invocation number
        * `{0}`, `{1}` for argument values
        * `{arguments}` for all arguments
* **What are the different data sources supported by parameterized tests in JUnit 5?**
  * Keywords, concepts, or topics that should be in the response:
    * `@ValueSource` for simple values
    * `@CsvSource` for inline CSV data
    * `@CsvFileSource` for external CSV files
    * `@EnumSource`, `@MethodSource`, `@ArgumentsSource` for advanced use cases
  * Possible follow-up questions
    * **When would you use `@CsvFileSource` instead of `@CsvSource`?**
      * Keywords, concepts, or topics that should be in the response:
        * When test data is large or external
        * Keeps test code clean
        * Supports skipping headers
* **How do you verify method calls using Mockito?**
  * Keywords, concepts, or topics that should be in the response:
    * Use of `Mockito.verify()`
    * Confirms method was called with specific arguments
    * Validates number of invocations
    * Ensures correct execution path
  * Possible follow-up questions
    * **Why is verifying method calls important in unit testing?**
      * Keywords, concepts, or topics that should be in the response:
        * Confirms internal behavior, not just output
        * Validates that required checks or logic were executed
        * Helps detect missing or incorrect interactions
        * Supports thorough test coverage
* **What are some common verification modes in Mockito?**
  * Keywords, concepts, or topics that should be in the response:
    * `times(n)` for exact number of calls
    * `atLeast(n)` for minimum number of calls
    * `atMost(n)` for maximum number of calls
    * Used to assert expected interaction frequency

## Preferred Questions

[Back to top](#unit)

* **What is a test suite in JUnit 5 and how is it created?**
  * Keywords, concepts, or topics that should be in the response:
    * Use of `@Suite` annotation
    * Part of `org.junit.platform.suite.api` package
    * Groups multiple test classes
    * Uses `@SelectClasses` or `@SelectPackages` to specify included tests
  * Possible follow-up questions
    * **What are the benefits of using test suites in JUnit 5?**
    * Keywords, concepts, or topics that should be in the response:
        * Logical grouping of related tests
        * Targeted execution of specific test sets
        * Simplifies continuous integration workflows
        * Easier integration with build tools like Maven or Gradle
* **How do you ignore or disable tests in JUnit 5?**
  * Keywords, concepts, or topics that should be in the response:
    * Use of `@Disabled` annotation
    * Can be applied to individual test methods or entire classes
    * Prevents test execution
    * Optional reason can be provided
  * Possible follow-up questions
    * **Why might you disable a test instead of deleting it?**
      * Keywords, concepts, or topics that should be in the response:
        * Test is temporarily irrelevant or flaky
        * Code under test is being refactored
        * Waiting on external dependencies or bug fixes
        * Preserves test for future reactivation
* **What is the syntax for stubbing an exception with Mockito?**
  * Keywords, concepts, or topics that should be in the response:
    * `Mockito.when(...).thenThrow(...)`
    * Provide the mock method and exception instance
    * Example: `thenThrow(new RuntimeException("message"))`
    * Similar structure to `thenReturn()`
* **How does Mockito support Test Driven Development (TDD)?**
  * Keywords, concepts, or topics that should be in the response:
    * Enables isolation of units under test
    * Allows creation of mock dependencies before implementation
    * Supports writing tests first
    * Encourages design focused on testability

## Stretch Questions

[Back to top](#unit)

* **How does automated testing support long-term code maintenance?**
  * Keywords, concepts, or topics that should be in the response:
    * Detects regressions early
    * Provides safety net for refactoring
    * Documents expected behavior
    * Reduces manual testing effort over time
  * Possible follow-up questions
    * **Why is having a reliable test suite important for evolving codebases?**
      * Keywords, concepts, or topics that should be in the response:
        * Ensures changes don’t break existing functionality
        * Builds developer confidence
        * Encourages continuous improvement
        * Supports agile and iterative development