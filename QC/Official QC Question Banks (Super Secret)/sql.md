## Unit

# SQL

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions

[Back to top](#unit)

* **What does the SQL acronym stand for? What are some SQL databases?**
  * Structured Query Language - allows us to interact with and manipulate relational databases like Oracle, Postgres, MySQL

* **How is data structured in a relational database?**
  * Tables
  * Rows
  * Columns
  * Primary keys / Foreign keys / relationships
  * Data is inserted as records, or rows, in a table. A database can have many tables that are related to each other. Each table has different columns, each with its own data type and possibly constraints.

* **Define the concept of `schema`**
  * Refers to the structure of the database - the columns of each table, their data types, and any constraints on them
  * **Follow-up: Can you have more than one schema in a database? (Yes)**

* **What is an ERD? How is it useful?**
  * Entity relationship diagram - used to model and show relationships between different tables in the database

* **What are the different multiplicity (cardinality) relationships? How would you create these relations?**
  * 1/1 - use a foreign key to relate to the primary key on another table; put UNIQUE constraint on the foreign key column
  * 1/many - foreign key on the many side of the relationship
  * many/many - use a 3rd table, called a junction/join table, to connect them. the junction table will have 2 foreign keys and will be the many side of both relations
  * **Follow-up: If want to model a university, what would be the relationship between 'student' table and 'professor' table? (Many to Many)**
  * **Follow-up: What kind of relationship would exist between Students and Classes? Students and Textbooks?**
    * Students/Classes: many-to-many
    * Students/Textbooks: one-to-many

* **What is normalization? What are the levels?**
  * The process of reducing redundancy in a database
  * 1NF: the key (PK must exist; columns must be atomic and granular)
  * 2NF: the whole key (1NF + every column relates to PK)
  * 3NF: nothing but the key (2NF + no transitive dependencies)
  * **Follow-up: Which normal form is it best practice to use? (3NF)**

* **What are the sublanguages of SQL? List some commands for each**
  * DDL - data definition language - CREATE, ALTER, MODIFY, DROP, TRUNCATE
  * DML - data manipulation language - SELECT, INSERT, UPDATE, DELETE
  * DCL - data control language - GRANT, REVOKE
  * DQL - data query language - SELECT
  * TCL - transaction control language - SAVEPOINT, ROLLBACK, COMMIT

* **What is the difference between scalar and aggregate functions? Give examples of each**
  * Scalar - operates on a single value, e.g. UPPER, LOWER, TRIM, CONCAT, DATE
  * Aggregate - operates on multiple values, e.g. MIN, MAX, AVG, SUM

* **How is `WHERE` different from `HAVING` in SQL?**
  * both are used to filter records
  * `HAVING` is used with aggregate functions to filter groups of records

* **What are the different types of keys? How are they made? What are they used for?**
  * Primary - Unique value that can identify a row in the table
  * Composite - A key made of more than a single column
  * Surrogate - Is a piece of data we add to a table, that isn’t a part of the data set
    * Added for our convenience
    * We use these most of the time, makes our life easy
  * Natural - Is a key that comes from the data itself
  * Candidate - Is any potential combination of columns that could server as a primary key

* **What are the 6 integrity constraints for enforcing database table relationships?**
  * PRIMARY KEY - Data in this column(s) is unique, not null, and uniquely identifies all records in the table
  * FOREIGN KEY - Any column(s) in a table referencing a PK in another table
    * Establishes relationship between 2 columns in the same table or between different tables
  * UNIQUE - No duplicate values
    * Null is not counted, you can still have multiple nulls
  * NOT NULL - Make sure a column does not contain null values
  * DEFAULT - Will default the column to some specified value of your choosing
  * CHECK - Adds an extra condition on inserted data (like x > 5)

* **What is the difference between `DELETE`, `DROP`, and `TRUNCATE` commands?**
  * `DROP` removes a table entirely
  * `DELETE` will remove specific rows (unless there is no `WHERE` clause)
  * `TRUNCATE` will empty a table of all data but leave the schema intact
  * `DROP` and `DELETE` can be rolled back; `TRUNCATE` cannot

* **Explain the concept of referential integrity**
  * Every foreign key in the database points to a valid, existing record
  * If this is broken, we have what is called an "orphan record"

* **What is the purpose of `CASCADE DELETE`?**
  * Maintaining referential integrity - if a row in the parent table is deleted, all rows in child table that reference the parent's primary key
  * Prevent orphaned records
  * Ensure data consistency

## Preferred Questions

[Back to top](#unit)

* **Explain what the ORDER BY and GROUP BY clauses do**
  * ORDER BY sorts the results set on a particular column (ascending or descending)
  * GROUP BY is used with an aggregate function to combine records together

* **What is the difference between joins and set operators?**
  * Joins combine tables horizontally
  * Set operators combine results sets vertically

* **Explain the difference between UNION, UNION ALL, and INTERSECT**
  * UNION - combines results sets, removes duplicates
  * UNION ALL - like UNION but allows duplicates
  * INTERSECT - returns the records that are in common between the two results sets

* **What are the types of joins? Explain the differences.**
  * INNER JOIN - only joins records that match based on join predicate
  * OUTER JOIN - joins all records in both tables, will have `null` as value if doesn't exist
  * LEFT JOIN - joins all records in left table, plus any records that match join predicate on right
  * RIGHT JOIN - joins all records in right table, plus any records that match join predicate on left
  * NATURAL JOIN - joins tables based on columns that have the same name in both tables
  * CROSS JOIN - cartesian product of records in both tables, i.e. each record in one table paired with each in another (results in M x N records)
  * SELF JOIN - joins a table with itself, FK points to PK of same table - e.g. employees table has reportsTo column for referencing manager in same table

* **What are the properties a transaction must follow?**
  * Atomicity - all or nothing (transaction must fully complete or rollback)
  * Consistency - data remains in a consistent state after the transaction
  * Isolation - transactions do not interfere with one another when running
  * Durability - data will persist even in case of catastrophic failure

* **What is a transaction within a relational database?**
  * A single unit of logic or work, sometimes made up of multiple operations
  * Independent of other transactions
  * You can set rollback points in which to rollback to if something fails
  * If anything fails, the whole transaction fails (all for one and one for all idea)
  * How do we write one? (Start with `BEGIN`, end with `COMMIT` and everything in between is the SQL you run)

    ```sql
    Begin;
    <Insert all the SQL in the transaction here >
    Commit;
    ```

* **Explain the different isolation levels. What read phenomena do each prevent?**
  * READ_UNCOMMITTED - fastest, allows dirty reads
  * READ_COMMITTED - prevents dirty reads, allows non-repeatable reads
  * REPEATABLE_READ - prevents non-repeatable reads, allows phantom reads
  * SERIALIZABLE - slowest, prevents phantom reads

## Stretch Questions

[Back to top](#unit)

* **What is the purpose of an index?**
  * Index increases performance of queries when done on the column with the index

* **What's the difference between a clustered and non-clustered index?**
  * Clustered - written to disk, only one allowed per table
  * Non-clustered - uses references in memory, multiple allowed

* **What is the purpose of a view?**
  * View is like a stored/cached query, useful for removing sensitive fields when giving access to a table
  * **How do you create a view?**
    * constructed from DQL queries and provide a window or "view" into the table
    * ` CREATE VIEW [viewname] AS [any DQL statement] `
  * **Benefit of a view?**
    * Views can be used to provide access to some portion of the data in a table but not all, which might be useful if the data is sensitive and needs to be kept private
    * used to abstract or hide complexity in the database - a view could be constructed with joins over multiple tables so that end users can query from denormalized tables easily
  * **What is a materialized view?**
    * Materialized views were introduced by Oracle and give a static snapshot of the data at a given point in time

* **What is a trigger? Give the syntax for creating a trigger.**
  * Trigger is a special type of stored procedure that runs when an event happens in the database

* **How would you setup a primary key that automatically increments with every INSERT statement?**
  * Postgres >10: use the IDENTITY keyword
  * Oracle 11g: use trigger and sequence together so that sequence increments on insert
  * Oracle 12c: IDENTITY keyword now exists

* **What's the difference between implicit and explicit cursors?**
  * Implicit cursor created automatically for you when you run a query
  * Cursor initially points to before the first record in a resultset
  * Explicit cursors must be created manually but give more control

* **What is an alias? How do we use them?**
  * SQL aliases are used to give a table, or a column in a table, a temporary name
  * An alias only exists for the duration of that query
  * Aliases are often used to make column names more readable
  * An alias is created with the `AS` keyword

    ```sql
    SELECT column_name AS alias_name FROM table_name;
    ```
