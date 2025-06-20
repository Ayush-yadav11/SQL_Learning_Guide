## Stored Procedures 

A **stored procedure** in SQL is a saved collection of one or more SQL statements that can be executed as a single unit. Stored procedures are stored in the database and can be reused multiple times, making them ideal for automating repetitive tasks, encapsulating business logic, and improving performance and security[1](https://www.w3schools.com/sql/sql_stored_procedures.asp)[2](https://www.datacamp.com/tutorial/sql-stored-procedure)[3](https://hightouch.com/sql-dictionary/sql-stored-procedures)[4](https://www.tutorialspoint.com/sql/sql-stored-procedures.htm).

---

## Key Features

- **Reusability:** Write once, use many times—call the procedure whenever needed.
    
- **Modularity:** Encapsulate complex logic into manageable, named blocks.
    
- **Performance:** Procedures are often precompiled, reducing execution time.
    
- **Security:** Restrict direct table access; users can be granted permission to execute procedures without accessing underlying data directly[2](https://www.datacamp.com/tutorial/sql-stored-procedure)[3](https://hightouch.com/sql-dictionary/sql-stored-procedures).
    
- **Parameterization:** Accept input and output parameters to handle dynamic operations[1](https://www.w3schools.com/sql/sql_stored_procedures.asp)[5](https://www.shiksha.com/online-courses/articles/difference-between-procedure-and-function-in-sql-blogId-148707)[6](https://www.mssqltips.com/tutorial/sql-server-stored-procedure-with-parameters/)[2](https://www.datacamp.com/tutorial/sql-stored-procedure).
    

---

## Basic Syntax

The syntax varies slightly between database systems, but the general structure is:

**SQL Server:**

sql

`CREATE PROCEDURE procedure_name     @param1 datatype,    @param2 datatype AS BEGIN     -- SQL statements END;`

**MySQL:**

sql

`DELIMITER // CREATE PROCEDURE procedure_name (IN param1 datatype, IN param2 datatype) BEGIN     -- SQL statements END // DELIMITER ;`

**PostgreSQL:**

sql

`CREATE PROCEDURE procedure_name (param1 datatype, param2 datatype) LANGUAGE SQL AS $$     -- SQL statements $$;`

---

## Executing a Stored Procedure

- **SQL Server / Oracle:**  
    `EXEC procedure_name;`
    
- **MySQL / PostgreSQL:**  
    `CALL procedure_name();`  
    [7](https://www.programiz.com/sql/stored-procedures)
    

---

## Example: Simple Stored Procedure

**MySQL Example:**

sql

`DELIMITER // CREATE PROCEDURE SelectAllCustomers() BEGIN     SELECT * FROM Customers; END // DELIMITER ;`

To execute:  
`CALL SelectAllCustomers();`  
[1](https://www.w3schools.com/sql/sql_stored_procedures.asp)[7](https://www.programiz.com/sql/stored-procedures)[4](https://www.tutorialspoint.com/sql/sql-stored-procedures.htm)

---

## Example: Stored Procedure with Parameters

**SQL Server Example:**

sql

`CREATE PROCEDURE SelectCustomersByCity     @City nvarchar(30) AS BEGIN     SELECT * FROM Customers WHERE City = @City; END;`

To execute:  
`EXEC SelectCustomersByCity @City = 'London';`  
[1](https://www.w3schools.com/sql/sql_stored_procedures.asp)[6](https://www.mssqltips.com/tutorial/sql-server-stored-procedure-with-parameters/)[8](https://www.sqlshack.com/sql-server-stored-procedures-for-beginners/)

---

## Use Cases

- Automating routine database operations (e.g., updating records, generating reports)
    
- Enforcing business rules and data integrity
    
- Performing data validation or transformation
    
- Modularizing complex data processing logic
    
- Enhancing security by limiting direct access to tables[5](https://www.shiksha.com/online-courses/articles/difference-between-procedure-and-function-in-sql-blogId-148707)[2](https://www.datacamp.com/tutorial/sql-stored-procedure)[3](https://hightouch.com/sql-dictionary/sql-stored-procedures)
    

---

## Differences from Functions

- **Procedures** can perform multiple operations and may or may not return a value, while **functions** always return a single value.
    
- Procedures can have output parameters; functions cannot[5](https://www.shiksha.com/online-courses/articles/difference-between-procedure-and-function-in-sql-blogId-148707).
    
- Procedures are called with `EXEC` or `CALL`, while functions can be used in SQL expressions.
    

---

## Dropping a Procedure

To delete a stored procedure:

sql

`DROP PROCEDURE procedure_name;`

---

**In summary:**  
A stored procedure in SQL is a powerful tool for encapsulating and reusing logic, automating tasks, and improving performance and security in database applications[1](https://www.w3schools.com/sql/sql_stored_procedures.asp)[2](https://www.datacamp.com/tutorial/sql-stored-procedure)[3](https://hightouch.com/sql-dictionary/sql-stored-procedures)[4](https://www.tutorialspoint.com/sql/sql-stored-procedures.htm).

---

## 🔗 Navigation

**📚 [← Back to Main Guide](README.md)**

**Previous Topic:** [← Common Table Expressions (CTEs)](Common%20Table%20Expressions%20(CTEs)%20in%20MySQL.md) | **Next Topic:** [Temporary Tables →](Temporary%20Tables%20in%20SQL.md)

### 📖 Complete Learning Path:
1. [SQL Fundamentals](SQL.md)
2. [JOINS in SQL](JOINS%20in%20SQL.md)
3. [String Functions](Strings%20in%20SQL.md)
4. [Subqueries](Subqueries%20in%20SQL.md)
5. [CASE Statements](CASE%20Statement%20in%20SQL.md)
6. [UNION Operations](Unions%20in%20SQL.md)
7. [Window Functions](Window%20Functions%20in%20SQL.md)
8. [Common Table Expressions (CTEs)](Common%20Table%20Expressions%20(CTEs)%20in%20MySQL.md)
9. **Stored Procedures** ← *You are here*
10. [Temporary Tables](Temporary%20Tables%20in%20SQL.md)