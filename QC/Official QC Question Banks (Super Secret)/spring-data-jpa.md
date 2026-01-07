## Unit

# Spring Data

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)
## Required Questions

* **What is `@Query` used for?**
  * Used to write the sql queries in the spring boot application in order to get the desired result from the database
  * Can only be used to annotate repository interface methods

* **What annotations or techniques allow writing more complex queries in Spring Data JPA?**
  * Use `@Query` for JPQL or native SQL.
  * Use method names for simple queries; fallback to native or JPQL for complex logic.

* **What is JPQL?**
  * Java Persistence Query Language
  * object-oriented query language which is used to perform database operations on persistent entities
  * Possible follow-up questions:
  * **What is the difference between JPQL and Native SQL?**
    * The main difference between SQL and JPQL is that SQL works with relational database tables, records and fields, whereas JPQL works with Java classes and objects. For example, a JPQL query can retrieve and return entity objects rather than just field values from database tables, as with SQL.

* **What is Spring ORM and Spring Data?**
  * *Spring ORM:* Object Relational Mapping. A technique or a Design Pattern used to access a relational database from an object-oriented language
  * The ORM **Hibernate** automatically handles SQL generation, table mapping, caching, and change tracking.
  * *Spring Data:* provides standard implementation for common DAO methods allowing for the removal of the DAO implementation and only requiring the definition of the DAO interface methods
  * Possible follow-up questions:
  * **What is the difference between `JPARepository` and `CrudRepository`?**

    * | Topic              | JPARepository                                                                                                                             | CrudRepository                                                                                                      |
      | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
      | Hierarchy          | JPA extend crudRepository and PagingAndSorting repository                                                                                 | Crud Repository is the base interface and it acts as a marker interface.                                            |
      | Batch Support      | JPA also provides some extra methods related to JPA such as delete records in batch and flushing data directly to a database.             | It provides only CRUD functions like findOne, saves, etc.                                                           |
      | Pagination Support | JPA repository also extends the PagingAndSorting repository. It provides all the method for which are useful for implementing pagination. | Crud Repository doesn't provide methods for implementing pagination and sorting.                                    |
      | Use Case           | JpaRepository ties your repositories to the JPA persistence technology so it should be avoided                                            | We should use CrudRepository or PagingAndSortingRepository depending on whether you need sorting and paging or not. |

* **What annotations can be used to prevent circular references during JSON serialization in Spring Data?**

  * Use `@JsonManagedReference` and `@JsonBackReference` to manage parent-child relationships.
  * Use `@JsonIdentityInfo` or `@JsonIdentityReference` to serialize only references.

* **What is the difference between eager and lazy loading in Spring Data JPA, and how do you resolve lazy load errors?**
  * Eager loading loads associated entities immediately; lazy loading loads them on access.
  * Lazy loading errors often occur outside of transaction scope (e.g., after session is closed).
  * Solutions include `@Transactional`, DTOs, or eager fetching where appropriate.

* **What is a database transaction, and how do you control transaction behavior in Spring?**
  * A transaction ensures atomicity, consistency, isolation, and durability (ACID).
  * Use `@Transactional` to control transaction scope.
  * Configure propagation and isolation levels via annotation attributes.

* **What is an Entity in Spring Data JPA, and how do you define one?**
  * An entity is a Java class annotated with `@Entity`, representing a table.
  * Fields are mapped to columns using `@Column`, `@Id`, and optional annotations like `@GeneratedValue`.

* **What are multiplicities in Spring Data JPA, and how do you implement them?**
  * One-to-one:

    ```java
    @OneToOne
    private Profile profile;
    ```

  * One-to-many:

    ```java
    @OneToMany(mappedBy = "user")
    private List<Post> posts;
    ```

  * Many-to-one:

    ```java
    @ManyToOne
    private User user;
    ```

  * Many-to-many:

    ```java
    @ManyToMany
    private Set<Role> roles;
    ```

* **What are derived query methods in Spring Data, and how do you use them for basic CRUD?**
  * Derived queries use method naming conventions like `findByName` or `deleteById`.
  * These allow basic CRUD without writing explicit queries.

## Preferred Questions
* **What does `@Transactional` do?**
  * *@Transactional:* automatically handles transaction propagation, and isolation, commit, and rollback
  * best practice usage `@Transactional` should be used on your `@Service` beans since a transaction is a unit of work with its success or failure directly tied to the requirements of the application and not necessrarily to the model

* **What interfaces are available in Spring Data JPA?**
  * CrudRepository and PagingAndSortingRepository

* **What is the naming conventions for methods in Spring Data repositories?**
  * 2 parts sereprated by "By"
  * `List<User> findByName(String name)`
  * The first part — such as find — is the introducer, and the rest — such as ByName — is the criteria.
  * Spring Data JPA supports the introducers: find, read, query, count and get.

* **What is the relationship between JPA, Spring Data JPA, and Hibernate?**
  * JPA is a Java specification for ORM.
  * Hibernate is an implementation of JPA.
  * Spring Data JPA builds on JPA and provides repository abstraction.

* **What are the different transaction propagation strategies in Spring?**
  * `REQUIRED`, `REQUIRES_NEW`, `NESTED`, `MANDATORY`, `NEVER`, `NOT_SUPPORTED`, and `SUPPORTS` define how methods should behave with existing transactions.

* **What are the different isolation levels in Spring transactions?**
  * `READ_UNCOMMITTED`, `READ_COMMITTED`, `REPEATABLE_READ`, and `SERIALIZABLE` control visibility of data changes across concurrent transactions.

## Stretch Questions

* **What validation annotations can be used in entity classes?**
  * Use JSR-303/JSR-380 annotations like `@NotNull`, `@Size`, `@Email`, and `@Pattern`.
  * Add `@Valid` in controller or service layer to trigger validation.

* **What is the Criteria API in Spring Data JPA, and how do you use it?**
  * The Criteria API is a programmatic way to build queries in a type-safe manner.
  * It uses `CriteriaBuilder`, `CriteriaQuery`, and predicates instead of string-based JPQL or SQL.
