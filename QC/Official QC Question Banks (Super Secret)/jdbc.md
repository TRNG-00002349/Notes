# Unit: JDBC

* [Concepts](#jdbc---concepts)
* [Practicals](#jdbc---practicals)

### IMPORTANCE: REQUIRED

## JDBC - CONCEPTS

[Back to top](#unit-jdbc)

* **What is JDBC?**
  * Java Database Connectivity: allows Java to connect to the DB
  * A Java API used to execute queries on various databases. Uses JDBC drivers to connect with the database

* **What is a Data Access Object (DAO) and why do we use them?**
  * Used for abstraction of accessing data to get information from the DB. Create them for classes in your application.

* **What are the interfaces and classes we use with JDBC?**
  * `Connection` (Interface)
  * `DriverManager` (Class)
  * `PreparedStatement` (Interface)
  * `Statement` (Interface)
  * `CallableStatement` (Interface)
  * `ResultSet` (Interface)
  * **Follow-up: What is the difference between `Statement` and `PreparedStatement`?**
    * `Statement` is used for executing *static* SQL statements
    * `PreparedStatement` is used for executing pre-compiled SQL statements

* **What is included in the Connection Interface?**
  *	`setAutoCommit()` -> turn to manual
  *	`commit()`
  *	`rollback()`
  *	`setSavepoint()`
  *	`preparedStatement` -> a kind of query
  *	`createStatement` -> a kind of query
  *	`prepareCall` -> a kind of query

* **What is the difference between the `.execute()` and `.executeUpdate()` methods in `PreparedStatement`?**
  * `.execute()` is used for any kind of SQL statement and returns a boolean
  * `.executeUpdate()` is used for DML statements and returns an int which is the number of rows affected

* **What is included in the `ResultSet` Interface?**
  *	What you get after executing a query
  *	First -> move it pointer to the first row of the results
  *	Next -> move to the next row of the results
    *	Next is designed to be the only one you need to call
    *	For a new result set next starts immediately before the first row
    *	The first time you call next you get the first row
  *	While on a row
    *	getInt(“column name”)
    *	getString(“column name”)
    *	Get specific values from a row

* **What is SQL Injection, and why is it considered a security risk in applications that interact with a database?**
  * SQL Injection is a security vulnerability that allows an attacker to interfere with the queries an application makes to its database. It occurs when user input is concatenated directly into SQL statements without proper validation or sanitization, potentially allowing attackers to manipulate the SQL query to execute arbitrary commands — such as extracting sensitive data, modifying or deleting records, or even executing administrative operations.
  * SQL Injection is risky because it bypasses standard authentication and authorization mechanisms, and may allow attackers to access data they shouldn’t (such as other users’ data), compromise the integrity of the database, or escalate to full system compromise, depending on database privileges.

* **Why should you use prepared statements for database interaction?**
  * A PreparedStatement helps mitigate SQL Injection because it separates SQL code from user input by using parameter placeholders (?). The SQL statement is precompiled and the parameters are safely bound to the placeholders, which prevents malicious input from being interpreted as part of the SQL code.
  * In addition to improving security, PreparedStatement can enhance performance because the SQL statement is precompiled by the database and can be reused with different parameter values efficiently — reducing the overhead of parsing and compiling SQL repeatedly, especially in batch operations or frequent queries.

* What are the steps to executing an SQL query using JDBC?
  1. Register the driver using `.forName()` (or let `DriverManager` detect and load automatically from classpath)
  2. Create the connection (`DriverManager.getConnection(url,username,password)`)
  3. Create a statement for executing the SQL query (`Statement st = conn.createStatement()`);
  4. Execute the SQL query (`ResultSet rs = st.executeQuery(String sql)`)
  5. Use `ResultSet` to get values returned (`rs.getInt(1)`, etc)
  6. Close the connection (`conn.close()`)


### IMPORTANCE: PREFERRED

* **What is the difference between Statement and PreparedStatement?**
  * PreparedStatements are pre-compiled by the JVM. The database doesn't have to compile the SQL each and every time it is executed.
  * PreparedStatement can be parameterized, which can make the SQL more readable. Furthermore, PreparedStatement will properly escape reserved characters to prevent SQL injection attacks.

* **What is a stored procedure and how would you call it in Java?**
  * A stored procedure is an executable block of code that is written in PL/SQL and stored in the Oracle database. A stored procedure is called from a Java class using a CallableStatement object. When the procedure is called, its name and any relevant parameters are sent over the JDBC connection to the DBMS, which executes the procedure and returns the results (if applicable) via the connection.

* **How to execute stored procedures using JDBC?**
  * Use the `CallableStatement` interface

* **Which interface is responsible for transaction management?** 
  * The `Connection` interface - can `commit`, `rollback`, etc

* **How do you use a ResultSet object to extract and manipulate data retrieved from a database query?**
  * A ResultSet contains the data produced by executing a query with Statement or PreparedStatement. You can iterate over the rows using while(resultSet.next()) and retrieve column values using getter methods like getInt(columnName) or getString(columnIndex).
  * ResultSet can also be used to manipulate data when it is updatable. You can modify the current row using updateXXX() methods and call updateRow() to persist changes, insert new rows with moveToInsertRow() + insertRow(), or delete rows with deleteRow().

* **What are the best practices to securely manage and hide JDBC database credentials in a Java application, and how can environment variables help?**
  * Instead of hardcoding database credentials (username, password) directly in the source code or configuration files, you can store them as environment variables on the operating system. In Java, you retrieve them at runtime using System.getenv(), e.g.,

  ```java
  String user = System.getenv("DB_USER");
  String password = System.getenv("DB_PASSWORD");
  ```
  This keeps sensitive credentials out of version control and minimizes exposure risk.
  * Or credentials can also be externalized using Java system properties (passed via -Dproperty=value at runtime), or secure configuration management tools like Spring’s application.properties + Vault integration, or AWS Secrets Manager, depending on the scale and sensitivity of the application. However, environment variables are a simple and widely supported solution for securely injecting credentials into any Java application.

### IMPORTANCE: STRETCH

* **What happens if you forget to close JDBC resources (Connection, Statement, ResultSet), and how can you ensure they are always closed properly?**
  * If JDBC resources are not closed, they may cause resource leaks, such as unclosed connections consuming database slots or unclosed ResultSet/Statement objects consuming memory and database cursors. Over time, this can exhaust available connections and degrade application or database performance.
  * The recommended way to ensure resources are always closed is by using try-with-resources which automatically closes any object implementing AutoCloseable. Example:

  ```java
  try (Connection conn = dataSource.getConnection();
      PreparedStatement ps = conn.prepareStatement(sql);
      ResultSet rs = ps.executeQuery()) {
    // use resources
  }
  // all resources automatically closed here
  ```

* **Explain the differences between auto-commit mode and manual transaction management in JDBC. Why would you disable auto-commit?**
  * In auto-commit mode (default), each individual SQL statement is executed and committed immediately after execution. No explicit transaction management is needed.
  * By disabling auto-commit (conn.setAutoCommit(false)), you control when a group of statements is committed or rolled back as a single transaction. This is useful when multiple statements should either all succeed or all fail together — such as transferring money between accounts. You explicitly call commit() or rollback() to finalize or discard the transaction.

### JDBC - Practicals

[Back to top](#unit-jdbc)

* What are the steps to executing an SQL query using JDBC?
  1. Register the driver using `.forName()` (or let `DriverManager` detect and load automatically from classpath)
  2. Create the connection (`DriverManager.getConnection(url,username,password)`)
  3. Create a statement for executing the SQL query (`Statement st = conn.createStatement()`);
  4. Execute the SQL query (`ResultSet rs = st.executeQuery(String sql)`)
  5. Use `ResultSet` to get values returned (`rs.getInt(1)`, etc)
  6. Close the connection (`conn.close()`)

  ```java
  import java.sql.Connection;
  import java.sql.DriverManager;
  import java.sql.ResultSet;
  import java.sql.SQLException;
  import java.sql.Statement;

  public class JDBCExample {
      // JDBC URL, username, and password of MySQL server
      private static final String JDBC_URL = "jdbc:mysql://localhost:3306/mydatabase";
      private static final String USERNAME = "username";
      private static final String PASSWORD = "password";

      public static void main(String[] args) {
          // Step 1: Establishing a Connection
          try (Connection connection = DriverManager.getConnection(JDBC_URL, USERNAME, PASSWORD)) {
              // Step 2: Create a Statement
              Statement statement = connection.createStatement();

              // Step 3: Execute a SQL SELECT query
              String query = "SELECT * FROM mytable";
              ResultSet resultSet = statement.executeQuery(query);

              // Step 4: Process the ResultSet
              while (resultSet.next()) {
                  // Example: Retrieving data from each row
                  int id = resultSet.getInt("id");
                  String name = resultSet.getString("name");
                  int age = resultSet.getInt("age");

                  // Do something with the data, like printing it
                  System.out.println("ID: " + id + ", Name: " + name + ", Age: " + age);
              }
          } catch (SQLException e) {
              e.printStackTrace();
          }
      }
  }

  ```