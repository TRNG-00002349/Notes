# Unit: Java
# Core Java

## Modules

* [Java Orientation](#java-orientation)
* [Java Basics](#java-basics)
* [Methods](#methods)
* [Types](#types)
* [OOP](#oop)
* [Exceptions](#exceptions)
* [Collections](#exceptions)
* [Maven](#maven)
* [Testing](#junit)

### Other

These topics are not within the Core Java unit and not aligned with the exit criteria but may be used in more advanced competencies.

* [Gradle](#gradle)
* [Multithreading](#multithreading)
* [Reflections API](#reflections)
* [Logging](#logging)

### IMPORTANCE: Required

## Java Orientation

[Back to top](#unit:-java)

* What is Java? / Why Java?
  * A high-level OOP language with rich API libraries, widely used around the world, supported by Oracle. Write once run anywhere (WORA), static types, compiled language. Used extensively in enterprise applications.

* What is JRE / JDK / JVM?
  * JVM - Java virtual machine. Runs compiled Java code
  * JRE - Java runtime environment. Contains the standard Java libraries and packages. Also contains JVM.
  * JDK - Java developer kit. Has a compiler, debugger, etc. Contains JRE and JVM.

* How would you compile and execute a Java program?
  * Need a JDK, use `javac ProgramName.java` command, then `java ProgramName` to execute on JRE

## Java Basics

[Back to top](#unit:-java)

* What are the primitive data types in Java?
  * boolean, byte, short, int, long, float, double, char
  * **Follow-up: What are the default values for all data types in Java?**
    * Objects - `null`
    * int, short, byte, long, float, double - 0
    * boolean - `false`
    * char - '\u0000' (null character)

* What are annotations?
  * A type of syntactic metadata added to the code, read by the compiler - use `@` syntax

* What is a POJO? What is a bean?
  * POJO - plain old Java object. Any Java object that you create.
  * Bean - a POJO that has private data members, public getters/setters, and overrides `.hashcode()`, `.equals()`, and `.toString()` methods

* What data types are supported in switch statements?
  * `String`, `int`, `char`, `short`, `byte`, `enums`

* How to pass multiple values with a single parameter into a method?
  * Use varargs with elipses syntax (`public void myMethod(String... strings)`)

* What is an enhanced for loop and what is a `forEach` loop?
  * Enhanced for loop allows easier traversal of Collections (actually any arrays or `Iterable`s) - syntax: `for (Object o : collection) {...}`

* How can you force garbage collection in Java?
  * Garbage collection cannot be forced but only requested using `System.gc()`.

* What is the difference between `static` and `final` variables?
  * `static` variables are shared by all the instances of objects and it has only single copy.
  * A `final` variable is a constant and it cannot be changed. However, if the variable holds a reference to an object, the state of the object may still be changed and manipulated.

* What are the access modifiers in Java? Explain them.
  * `public`  - can be accessed from any package.
  * `private` - only members of the same class can access.
  * `protected` - can be accessed by classes inside the package and subclasses anywhere.
  * `default` - no access by classes or subclasses outside the package

* What are the non-access modifiers in Java?
  * `static`, `final`, `abstract`, `default`, `synchronized`, `transient`
  * obscure keywords: `volatile`, `native`, `strictfp`

## Methods

[Back to top](#unit:-java)

* What is the main method signature? How does the String array parameter get populated?
  * `public static void main(String[] args)` - the String array is populated by arguments passed into the command line when program is run

## Types

[Back to top](#unit:-java)

* What is a wrapper class?
  * Wrapper class is a wrapper around a primitive data type. It represents primitive data types in their corresponding class instances e.g. a boolean data type can be represented as a `Boolean` class instance. All of the primitive wrapper classes in Java are immutable i.e. once assigned a value to a wrapper class instance cannot be changed further.

* What is autoboxing / unboxing?
  * Auto-boxing is the automatic conversion of primitives to their wrapper classes by the compiler. Useful for adding primitives to collections

* Where are Strings stored?
  * In the String pool in the heap

* What is the difference between `String`, `StringBuilder`, and `StringBuffer`?
  * Strings are immutable.  Both `StringBuilder` and `StringBuffer` are mutable.  Furthermore, `StringBuffer` is sychronized while `StringBuilder` is not.
  * Follow-up question: Why are strings immutable in Java?
    * Identical String literals are collected in the "String pool" in an effort to conserve memory. Reference variables will then point to the same String object instance. Changing the object's state in the String pool will make changes to all references to that String object. Instead, when a change to a String is made, the JVM makes a new String object, and the reference variable points to the new String in the String pool.

* What are enumerations (enums)?
  * A special Java type that defines a collection of constants

* Explain stack vs heap?
  * Heap is where objects are stored in memory. Stack is where local variable references are kept - a new stack is created for each method invocation

## OOP

[Back to top](#unit:-java)

### OOP 

* What is an object / class?
  * Class is a blueprint for an object

* Describe the four pillars/principles of object oriented programming
  * Keywords, concepts, or topics that should be in the response:
    * Abstraction - abstract classes, interfaces
    * Inheritance - extends, implements
    * Encapsulation - access modifiers
    * Polymorphism - overloading, overriding
  * Possible follow-up questions

* What are the 4 pillars of OOP? Explain each one.
  * **Abstraction** - Hiding implementation details - use abstract classes and interfaces to achieve this.
  * **Polymorphism** - Subclasses of a class can define their own unique behaviors and yet share some of the same functionality of the parent class. An object can also be referenced by its supertype "parent" class, for example `ParentClass obj = new SubClass()`. Method overriding and overloading are also examples of polymorphism.
  * **Inheritance** - A class that is derived from another class is called a subclass (also a derived class, extended class, or child class). The class from which the subclass is derived is called a superclass (also a base class or a parent class).
  * **Encapsulation** can be described as a protective barrier that prevents the code and data being randomly accessed by other code defined outside the class. Access to the data and code is tightly controlled by an interface.
  * Follow-up questions
    * Can you explain [abstraction, e.g.] in more detail? How would you practically use that?

* What is the difference between method overloading and overriding?
  * Method overriding - In a subclass when one declares an identical method from the superclass, this method overrides the one in the superclass.
  * Method overloading - Within the same class when one declares more than method with the same name but different signature (parameters).

* Difference between extends and implements?
  * Extends is for classes, implements is for implementing interfaces

  * Ans: first line uses polymorphic declaration; we can swap out implementations of `List` at any time, so the code is more decoupled and uses abstraction properly

* What is the difference between an abstract class and an interface?
  * An abstract class can have both concrete and abstract methods whereas an interface must have only abstract methods if any (unless the default keyword is used). Interface methods are implicitly public and abstract, interface variables are implicitly public, static, and final, but these do not apply in abstract classes. Neither can be instantiated

* What are the implicit modifiers for interface variables / methods?
  * methods - `public abstract`; variables - `public static final`

* What is the root class from which every class extends?
  * The `Object` class
  * **Follow-up: What methods are available in the Object class?**
    * `.clone`, `.hashcode`, `.equals`, `.toString`

* What is the difference between `==` and `.equals()`?
  * `==` -  tests to see if two reference variables refer to the exact same instance of an object.
  * `.equals()` - tests to see if the two objects being compared to each other are equivalent, but they need not be the exact same object. This method should be overridden from the `Object` class. The default implementation falls back to `==` behavior.

* If two objects are equal, do they have the same hashcode? If not equal?
  * If two objects have the same hashcode then they are NOT necessarily equal. But if objects are equal, then they MUST have same hashcode.

* What is the first line of constructor?
  * The compiler will insert `super()` as the first line - it cannot be used anywhere else in constructor except for the first line
  * `super()` calls the parent constructor

* Can you overload / override a main method? static method? a private method? a default method? a protected method?
  * Main method - overload, cannot override b/c is static method.
  * Static method - overload, cannot override b/c belongs to class (not inherited).
  * Private method - overload, cannot override b/c doesn't get inherited.
  * Default method - both.
  * Protected method - both (override if inherited).

* If 2 interfaces have default methods and you implement both, what happens?
  * The code will NOT compile unless you override the method. However, the code WILL compile if one interface is implemented further up in the class hierarchy than the other - in this case, the closest method implementation in the hierarchy will be called

* If 2 interfaces have same variable names and you implement both, what happens?
  * The code will compile unless you make a reference to the variable (this is an ambiguous reference). You must explicitly define the variable by using the interface name: `int a = INTERFACENAME.a;`

## Exceptions

[Back to top](#unit:-java)

### Exceptions 

* What is base class of all exceptions? What interface do they all implement?
  * The base class is `Exception`, which implements the `Throwable` interface

* What is the difference between checked and unchecked exceptions?
  * Checked means the compiler will check that you have either handled or declared it. Unchecked exceptions do not need to be handled, but they can be. Unchecked exceptions extend from `RuntimeException`
  * **Follow-up: List some checked and unchecked exceptions**
    * Checked - `IOException`, `ClassNotFoundException`, `InterruptedException`
    * Unchecked - `ArithmeticException`, `ClassCastException`, `IndexOutOfBoundsException`, `NullPointerException`

* What are the different ways of handling checked exceptions?
  * Use `try/catch` block; or use the `throws` declaration on the method signature to "duck" it and have it propagate up the call stack

* What is try-with-resources? What interface must the resource implement to use this feature?
  * Try-with-resources allows for automatically closing resources in a try/catch block using `try(resource) {...}` syntax. Must implement the `AutoCloseable` interface

* How would you create a custom exception?
  * Extend `Exception` or `RuntimeException` classes or subclasses

## Collections

[Back to top](#unit:-java)

### Collections 

* What are collections in Java?
  * A general data structure that contains Objects. Also the name of the API
  * **Follow-up: What are the interfaces in the Collections API?**
    * Iterable, Collection, List, Queue, Set, Map, SortedSet, SortedMap, Deque
  * **Follow-up: Which collections are iterable?**
    * Everything except `Map`s; they have to be iterated by keys or by values or by using an `Iterator`

* What is the difference between a `Set` and a `List`?
  * `Set` does not allow duplicates (its members are unique)

* What is the difference between a `Array` and an `ArrayList` (or any `List`)?
  * An array is static and its size cannot be changed, but an ArrayList can grow/shrink

* How would you iterate over a `Map`?
  * Cannot use for loop (or enhanced for loop) directly
  * Iterate over each entry in the map `Map.Entry<K,V>` using `.entrySet()`
  * Iterate over the collection of values with `.values()`
  * Iterate over the keyset with `.keySet()`

* What are generics? What is the diamond operator (`<>`)?
  * A way of specifying a type within a data structure - they enforce type safety. `<>` operator lets you infer generic types from the LHS of assignment operation

* What is the difference between `ArrayList` and `LinkedList`?
  * `ArrayList` is backed by an array; grows by 50% when capacity reached; more efficient for reading instead of inserting/deleting
  * `LinkedList` is a doubly linked list of nodes; each node has reference to previous and next; more efficient for inserting/deleting

## JUnit

[Back to top](#unit:-java)

### JUnit 

* What is JUnit?
  * A Java unit testing framework for testing code - use it for TDD

* What is TDD?
  * Test-driven development - write unit tests before application code, then write code to make tests pass. Repeat this process until functionality is complete.

* What are the annotations in JUnit? List them in the order of execution
  * BeforeClass, AfterClass, Before, After, Test, Ignore

* Give an example of a test case?
  * Adding two numbers, check that the method returns the sum

* What does "code coverage" as a metric mean?
  * How much of the code has been tested with unit tests
  * Could be measured by lines of code tested, or how many of branches of control flow have been tested

### IMPORTANCE: PREFERRED

### Exceptions 

* `throw` vs `throws` vs `Throwable`?
  * `Throwable` - the root interface of exceptions, allow a class to be "thrown"
  * `throws` - keyword in method signature after params that declare which exception the method might throw
  * `throw` - the keyword that will actually "throw" an exception in code

* Do you need a catch block? Can have more than 1? Order of them?
  * Catch block is not necessary - try/finally will compile. You can have more than one catch block, but the order must be from most narrow exception to most broad/general.

* Multi-catch block - can you catch more than one exception in a single catch block?
  * Yes, use the `|` operator

### Collections 

* What is the difference between `TreeSet` and `HashSet`?
  * `HashSet` is much faster (constant time versus log time for most operations) but offers no ordering guarantees.

* How does a Queue work?
  * First in, first out

* `LinkedList` implements which two interfaces?
  * `List` and `Queue`

* What is the difference between HashTable and HashMap?
  * `HashTable` is synchronized whereas `HashMap` is not.
  * `HashMap` permits `null` values and the `null` key.
  * Follow-up question: Why does `HashTable` not take `null` key?
    * The hash table hashes the keys given as input, and the `null` value cannot be hashed

* Are Maps in the Collections API?
  * Yes, but they do not implement `Collection` or `Iterable` interfaces

### JUnit 

* When writing a unit test, what is the order of the following: "Act", "Assert", "Arrange". Explain these terms
  * Order: Arrange, Act, Assert
  * Arrange: Setup the test by initializing objects, preparing inputs, and configuring the environment.
  * Act: Execute the specific behavior or action that you want to test.
  * Assert: Verify that the outcome of the action matches the expected result or state

* List some assertion types
  * `AssertTrue` / `AssertFalse`
  * `AssertGreaterThan` / `AssertLessThan`
  * `AssertEquals` / `AssertNotEqual`

* What is mockito used for?
  * Mocking library for creating test stubs and mocks
  * Both are fake objects used for testing when classes have dependencies
  * Stubs are simple implementations, usually hard-coded responses
  * Mocks are more sophisticated, are dynamic and can be configured to return specific values with specific arguments
  * Mocks usually have built-in verification methods

## Maven

[Back to top](#unit:-java)

* What is Maven?
  * A build automation and dependency management tool for Java applications

* What is the POM and what is the pom.xml?
  * POM stands for project object model and is the model used by Maven to understand project attributes and dependencies. The pom.xml is the xml document which lists those attributes and dependencies

* What do these commands do?

  ```bash
  mvn compile
  mvn test
  mvn package
  ```

* Where / when does Maven retrieve dependencies from? Where are they stored locally?
  * Maven first looks to see if the dependency is in the local repo under `.m2` directory. If not, it will download the necessary .jar file(s) from the remote central Maven repository into the `.m2` directory

* What is the default Maven build lifecycle?
  * process resources - copy and process the resources into destination directory
  * compile - compile the source code
  * process-test-resources - same for test directory
  * test-compile - compile the test code
  * test - run the test code
  * package - combine compiled source code into a .jar or .war file
  * install - install package to local repo
  * deploy - copy package and install in remote repo

### Maven 

* What are the project coordinates for a dependency?
  * `artifact-id`, `group-id`, and `version`

## Gradle

[Back to top](#unit:-java)

* **What is Gradle and how does it work as a build tool?**
  * Gradle is an open-source build automation tool that is designed to automate the process of building, testing, and deploying software projects. It uses a Groovy-based domain-specific language (DSL) or Kotlin for scripting, allowing developers to describe their build process declaratively. Gradle follows a task-based approach where tasks represent individual build steps, and dependencies between tasks are automatically managed, ensuring that tasks are executed in the correct order. Gradle uses a build script (usually named `build.gradle`) to define the project structure, dependencies, and tasks required to build the project.

* **What are some common Gradle commands and their purposes?**
  * `gradle build`: Compiles and assembles the project, running all tasks necessary for building the project.
  * `gradle clean`: Deletes the build directory and any generated files, allowing for a clean build from scratch.
  * `gradle test`: Executes the tests for the project.
  * `gradle run`: Runs the project, typically used for running applications.
  * `gradle tasks`: Lists all available tasks in the project.
  * `gradle dependencies`: Displays the dependencies of the project.

* **What is the purpose of the Gradle configuration file (`build.gradle`)?**
  * The `build.gradle` file serves as the configuration file for Gradle projects. It defines the project structure, dependencies, plugins, and tasks required for building the project. In the `build.gradle` file, developers can specify various settings and configurations using Gradle's DSL (Domain Specific Language) or Kotlin. This includes specifying project metadata, declaring dependencies, configuring tasks, applying plugins, and defining custom build logic. The `build.gradle` file is where developers customize the build process to suit the specific requirements of their project.

* **How does Gradle handle project dependencies?**
  * Gradle manages project dependencies using a declarative approach, where dependencies are declared in the `build.gradle` file. Dependencies can be specified for different scopes, such as compile-time dependencies, test dependencies, and runtime dependencies. Gradle retrieves dependencies from repositories such as Maven Central, JCenter, or custom repositories specified in the `build.gradle` file. Gradle automatically resolves transitive dependencies, meaning it includes dependencies required by other dependencies. Dependency management in Gradle helps ensure that the project has access to the necessary libraries and components required for building and running the application.

## Design Patterns

[Back to top](#unit:-java)

* What are Singleton / Factory design patterns?
  * Singleton - allows for creation of only 1 object. Method for retrieving object returns reference to the same object in memory. Implement via private constructor
  * Factory - abstracts away instantiation logic, usually used in conjunction with singleton pattern

## Other 

[Back to top](#unit:-java)

### Multithreading

* What is multi-threading?
  * Handling multiple threads / paths of execution in your program.

* In what ways can you create a thread?
  * By extending the `Thread` Class or by implementing the `Runnable` Interface. You must call `Thread`'s `.start()` method to start it as a new thread of execution.

* What is the lifecycle of a thread?
  * When created, in NEW state.
  * When `.start()` is called, it goes to RUNNABLE state.
  * When `.run()` is called, goes to RUNNING state.
  * If `.sleep()` or `.wait()` is called, will go to WAITING.
  * If dependent on another thread to release a lock, it will go to BLOCKED state.
  * When finished executing, will be in TERMINATED state and cannot be restarted.

* What is deadlock?
  * When two or more threads are waiting on locks held by the others, such that no thread can execute

* What is `synchronized` keyword?
  * Only allowing one thread access to the method or variable at a time - enforces thread-safety

* What is an `Executor` and `ExecutorService`?
  * `Executor` is an interface with the `execute` method that provides an abstraction for launching new tasks
  * `ExecutorService` is a subinterface that adds methods to handle the lifecycle of the task and service itself. It has a `submit` method that accepts `Runnable`s and `Callable`s and returns a `Future`

* What is thread pooling? Why is it a good idea to use a thread pool? How?
  * Instead of creating new threads every time you need one, store them in a central location and reuse them.
  * Reduces the overhead of creating new threads
  * Tasks are added to a queue and processed when a thread becomes available
  * `Executors.newFixedThreadPool(n)` will create a thread pool with a fixed `n` number of threads and return an `ExecutorService` for it

* Explain the fork/join framework
  * A specific implementation of `ExecutorService` for tasks that we can split up and perform recursively
  * Usually we'll use `RecursiveTask` (returns a result) or `RecursiveAction` (does not return anything)

### Logging

* What is an advantage to using a logging library?
  * Allows you to set logging thresholds

* What is log4j?
  * Logging library for Java

* What are the logging levels of log4j?
  * TRACE, DEBUG, INFO, WARN, ERROR, FATAL

* Why was the `default` keyword introduced for interfaces?
  * So that developers could update their interfaces without breaking legacy code that depends on that interface. The `default` keyword allows for implementation of an interface method

### Serialization

* How do you serialize / deserialize an object in Java?
  * Step 1: An object is marked serializable by implementing the `java.io.Serializable` interface, which signifies to the underlying API that the object can be flattened into bytes and subsequently inflated in the future.
  * Step 2: The next step is to actually persist the object. That is done with the `java.io.ObjectOutputStream` class. That class is a filter stream--it is wrapped around a lower-level byte stream (called a node stream) to handle the serialization protocol for us. Node streams can be used to write to file systems or even across sockets. That means we could easily transfer a flattened object across a network wire and have it be rebuilt on the other side!
  * To restore the object back, you use `ObjectInputStream.readObject()` method call. The method call reads in the raw bytes that we previously persisted and creates a live object that is an exact replica of the original. Because `readObject()` can read any serializable object, a cast to the correct type is required. With that in mind, the class file must be accessible from the system in which the restoration occurs. In other words, the object's class file and methods are not saved; only the object's state is saved.

* What is a Marker interface?
  * A marker interface is an interface which has no methods at all. Example: `Serializable`, `Remote`, `Cloneable`. Generally, they are used to give additional information about the behavior of a class.

* What are transient variables?
  * Transient variables are those variables which cannot be serialized.

* Difference between FileReader and BufferedReader?
  * `FileReader` is just a `Reader` which reads a file, so it reads characters and uses the platform-default encoding.
  * `BufferedReader` reads text from a character-input stream, buffering characters so as to provide for the efficient reading of characters, arrays, and lines (e.g. can read one line at a time).
  * So you can wrap a `BufferedReader` around a `FileReader`

### Reflections

* What is Reflection API?
  * The first component of the Reflection API is the mechanism used to fetch information about a class. This mechanism is built into the class named Class. The special class Class is the universal type for the meta information that describes objects within the Java system. Class loaders in the Java system return objects of type Class. Up until now the three most interesting methods in this class were:
  * `.forName()`, which would load a class of a given name, using the current class loader
  * `.getName()`, which would return the name of the class as a String object,which was useful for identifying object references by their class name
  * `.newInstance()`, which would invoke the null constructor on the class (if it exists) and return you an object instance of that class of object
  * To these three useful methods the Reflection API adds some additional methods to class Class. These are as follows:
  * `getConstructor`, `getConstructors`, `getDeclaredConstructor`
  * `getMethod`, `getMethods`, `getDeclaredMethods`
  * `getField`, `getFields`, `getDeclaredFields`
  * `getSuperclass`
  * `getInterfaces`
  * `getDeclaredClasses`

### IMPORTANCE: STRETCH

* How would you make an immutable object?
  * Declare the class as `final` so it can't be extended.
  * Make all fields `private` so that direct access is not allowed.
  * Don't provide setter methods for variables.
  * Make all mutable fields final so that it's value can be assigned only once.
  * Initialize all the fields via a constructor performing deep copy.
  * Perform cloning of objects in the getter methods to return a copy rather than returning the actual object reference.

* What is static block?
  * Used for static initialization. Executed only once - upon creation of first object of class or access to static method of class

* What are 3 usages of `super` keyword?
  * to refer to immediate parent class instance variable.
  * `super()` is used to invoke immediate parent class constructor (also can pass params)
  * to invoke immediate parent class method.

* Is Java pass-by-value or pass-by-reference?
  * Java is strictly pass by value. Even when object references are passed as arguments, it is the value of the reference that is passed

* What is the difference between `final`, `.finalize()`, and `finally`?
  * `final`: final keyword can be used for class, method and variables. A final class cannot be subclassed and it prevents other programmers from subclassing a secure class to invoke insecure methods. A final method can't be overridden. A final variable can't change from its initialized value.
  * `finalize()`: finalize method is used just before an object is destroyed and called just prior to garbage collection.
  * `finally`: finally, a key word used in exception handling, creates a block of code that will be executed after a `try/catch` block has completed and before the code following the `try/catch` block. The `finally` block will execute whether or not an exception is thrown. For example, if a method opens a file upon exit, then you will not want the code that closes the file to be bypassed by the exception-handling mechanism. This finally keyword is designed to address this contingency.

* How to make numbers in your code more readable?
  * Use the `_` for numeric literals - must be placed between numbers

* What are functional interfaces?
  * Functional interfaces only have one method, and can be used in conjuntion with lambdas

* What are lambdas?
  * Like anonymous functions, they allow implementation of functional interfaces directly without creating a class
  * Allow methods to be stored in variables

* What is the Streams API used for? What is the difference between intermediate and terminal operations? Can you provide examples?
