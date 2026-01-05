# Database Normalization Lesson

## What is Database Normalization?

Database normalization is an opinionated approach to organizing data in a database. It provides specific rules and conventions for structuring tables to reduce redundancy and improve data integrity. Like other opinionated practices in software development, normalization prescribes how you should do things rather than leaving design completely open-ended.

Importantly, these rules aren't enforced by database technology itself—you can absolutely create poorly normalized databases that work. Normalization is a set of best practices you choose to follow. The process involves breaking down tables into smaller, related tables and defining relationships between them, with the goal of eliminating duplicate data and ensuring each piece of information is stored in only one place. Normalization follows a series of rules called "normal forms," each building on the previous one.

## First Normal Form (1NF)

A table is in 1NF when every row is uniquely identifiable, typically through a primary key—though this requirement is actually enforced by database technology itself and is included in 1NF mainly for completeness. Additionally, all columns must contain only atomic (indivisible) values with no repeating groups or arrays. For example, instead of storing "John Smith" in a single Name column, you'd separate it into FirstName and LastName columns.

## Second Normal Form (2NF)

A table is in 2NF when it's in 1NF and all non-key columns depend on the entire primary key, not just part of it. This mainly applies to composite primary keys. For instance, if OrderID and ProductID form a composite key, columns describing only the product should move to a separate Products table since they depend only on ProductID.

## Third Normal Form (3NF)

A table is in 3NF when it's in 2NF and no non-key column depends on another non-key column. If column A depends on the primary key and column B depends on column A, then B is transitively dependent on the primary key and violates 3NF. For example, storing both CustomerZipCode and CustomerCity in a table creates a transitive dependency since City depends on ZipCode rather than directly on the primary key. To normalize to 3NF, you need to eliminate these transitive dependencies.

## Higher Normal Forms

While 1NF through 3NF cover most practical database design scenarios, there are additional normal forms that address increasingly niche problems:

**Boyce-Codd Normal Form (BCNF)** - Addresses edge cases that 3NF misses, specifically when a non-key column determines part of a candidate key. Still taught in database courses and occasionally relevant in practice.

**Fourth Normal Form (4NF)** - Eliminates multi-valued dependencies, which occur when you have two independent many-to-many relationships in the same table. Rarely encountered in typical applications.

**Fifth Normal Form (5NF)** - Deals with join dependencies and is largely of academic interest. Problems requiring 5NF are extremely uncommon in real-world databases.

**Sixth Normal Form (6NF)** - Requires extreme decomposition, mainly used in specialized temporal databases and data warehouses with columnar storage. Essentially impractical for standard OLTP systems.

Beyond these, theoretical constructs like Domain-Key Normal Form (DKNF) exist but have no practical application—there's no algorithm to achieve them or even test for them.

_**Note on Terminology:** Throughout these definitions, references to "primary key" formally extend to all candidate keys. When we say non-key attributes must depend on the primary key, we mean they must depend on every candidate key—not just the one chosen as primary. This distinction matters most in 2NF and 3NF when dealing with tables that have multiple possible keys._

## Common Problems with Poor Normalization

When databases aren't properly normalized, several types of anomalies can occur:

**Update Anomalies** - If customer address information is duplicated across multiple order records, updating a customer's address requires changing it in many places. Miss one, and you have inconsistent data. With proper normalization, the address exists in one place and updates happen once.

**Insertion Anomalies** - Suppose you store course information only when students enroll. You can't add a new course to the database until at least one student registers for it. Normalization separates course data from enrollment data, allowing courses to exist independently.

**Deletion Anomalies** - If you store instructor information only in a course table, deleting the last course an instructor teaches removes all record of that instructor from the database. Proper normalization preserves instructor data even when they're not currently teaching.

**Wasted Storage** - Redundant data consumes unnecessary disk space. Storing complete customer details with every order rather than once in a customers table multiplies storage requirements. Normalized databases use less storage but may require joins to reconstruct data.

## When to Denormalize

While normalization provides important benefits for data integrity and consistency, there are practical scenarios where you might intentionally violate normalization rules:

**Performance optimization** - In read-heavy applications, constantly joining normalized tables can be slow. Storing redundant information (like a customer's name in an orders table even though it exists in the customers table) can significantly speed up queries.

**Reporting and analytics** - Data warehouses often use denormalized schemas because aggregating data across many normalized tables is too slow for analytics queries. Star and snowflake schemas intentionally denormalize for query performance.

**Caching calculated values** - Storing aggregates like total order count per customer, even though it's derivable from the orders table, avoids expensive calculations on every query.

The tradeoff is always between data integrity and consistency (normalization's strength) versus performance and query simplicity (denormalization's advantage).