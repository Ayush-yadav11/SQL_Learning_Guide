SQL (Structured Query Language) is the standard language for managing and manipulating relational databases. Below are essential notes covering SQL fundamentals, best practices, and key concepts relevant for students and professionals.

---
## **1. What is SQL?**

- SQL is used to create, modify, manage, and query data in relational databases.
- Common SQL operations include: creating tables, inserting data, updating records, deleting records, and retrieving data.
---
## **2. Database Design Principles**

- **Minimize Redundancy:** Avoid storing the same information in multiple places to reduce errors and inconsistencies[1](https://support.microsoft.com/en-us/office/database-design-basics-eb2159cf-1e30-401a-8084-bd4f9c9ca1f5)[5](https://www.guvi.in/blog/database-design-principles-and-best-practices/).
- **Integrity:** Use primary keys for unique identification (entity integrity) and foreign keys to maintain relationships (referential integrity)[5](https://www.guvi.in/blog/database-design-principles-and-best-practices/).
- **Normalization:** Organize data into tables to reduce redundancy and dependency. Most databases are normalized to the third normal form (3NF)[5](https://www.guvi.in/blog/database-design-principles-and-best-practices/)[8](https://www.reddit.com/r/Database/comments/rrwmtv/are_there_any_good_rules_of_thumb_dos_and_donts/).
- **Scalability & Performance:** Plan for growth and optimize for query performance using indexing, partitioning, and efficient data types[5](https://www.guvi.in/blog/database-design-principles-and-best-practices/).
- **Security:** Implement access controls, encryption, and regular backups to protect data[5](https://www.guvi.in/blog/database-design-principles-and-best-practices/)[6](https://www.integrate.io/blog/complete-guide-to-database-schema-design-guide/).
---
## **3. SQL Syntax and Key Clauses**

- **SELECT:** Retrieves data from one or more tables.
- **WHERE:** Filters records based on specified conditions.
- **ORDER BY:** Sorts the result set by one or more columns.
- **GROUP BY:** Groups rows that have the same values in specified columns for aggregate functions.
- **HAVING:** Filters groups created by GROUP BY, often used with aggregate functions.
- **LIMIT:** Restricts the number of rows returned (MySQL, PostgreSQL).
- **DISTINCT:** Returns unique values, removing duplicates.
- **Aliasing (AS):** Assigns temporary names to columns or tables for readability.
---
## SELECT

- Retrieves data from a database table.
- Syntax:
```sql  
SELECT column1, column2
FROM table_name;
```
- To select all columns:
```sql    
SELECT * 
FROM table_name;
```  
---
## WHERE

- Filters records based on specified conditions.
    
- Syntax:
    
```sql   
	SELECT column1 
	FROM table_name 
	WHERE condition;
```
- Example:
    ```sql
    SELECT * 
    FROM Customers 
    WHERE Country = 'USA';
    ```
---
## ORDER BY

- Sorts the result set by one or more columns.
    
- Syntax:
 ```sql
    SELECT column1 
    FROM table_name 
    ORDER BY column1 [ASC|DESC];
    ```
- Example:
```sql
    SELECT * 
    FROM Customers 
    ORDER BY CustomerName ASC;
    ```
---
## GROUP BY

- Groups rows sharing a property so aggregate functions can be applied.
    
- Syntax:
    ```sql
    SELECT column, AGG_FUNC(column2) 
    FROM table_name 
    GROUP BY column;
    ```
- Example:
    ```sql
	SELECT Country, COUNT(*) 
	FROM Customers 
	GROUP BY Country;
    ```
---
## LIMIT

- Restricts the number of rows returned (MySQL, PostgreSQL).
    
- Syntax:
    ```sql
    SELECT column1 
    FROM table_name 
    LIMIT number;
    ```
- Example:
    ```sql
    SELECT * 
    FROM Customers 
    LIMIT 10;
    ```
---
## DISTINCT

- Returns only unique (distinct) values.
    
- Syntax:
    ```sql
    SELECT DISTINCT column1 
    FROM table_name;
    ```
- Example:
    
    ```sql
    SELECT DISTINCT Country 
    FROM Customers;
    ```
---
## Aliasing (AS)

- Assigns a temporary name (alias) to a column or table for readability.
    
- Syntax:
    
    ```sql
    SELECT column1 AS alias_name 
    FROM table_name;
    ```
- Example:
    
    ```sql
    SELECT CustomerName AS Name 
    FROM Customers;
    ```
---
## HAVING

- Filters groups created by GROUP BY, often used with aggregate functions.
    
- Syntax:
    
    ```sql
    SELECT column, AGG_FUNC(column2) 
    FROM table_name 
    GROUP BY column 
    HAVING condition;
    ```
- Example:
    
    ```sql
    SELECT Country,COUNT(*) 
     FROM Customers 
     GROUP BY Country 
     HAVING COUNT(*) > 5;
    ```

---

## Example Query Using All Clauses

```sql
SELECT Country AS Nation, 
COUNT(*) AS NumCustomers 
FROM Customers 
WHERE City IS NOT NULL 
GROUP BY Country 
HAVING COUNT(*) > 5 
ORDER BY NumCustomers DESC LIMIT 10;
```
This query:
- Selects countries and counts customers,
- Filters out rows where City is NULL,
- Groups by country,
- Only includes groups with more than 5 customers,
- Sorts by the number of customers descending,
- Returns the top 10 results,
- Uses aliases for readability.
Each clause has a specific order in SQL:  
`SELECT` → `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `ORDER BY` → `LIMIT`[8](https://dev.mysql.com/doc/en/select.html).
These features are fundamental for querying and analyzing data in SQL databases.
## **Best Practices for SQL and Schema Design**

- **Keep It Simple:** Use straightforward, descriptive names for tables and columns[2](https://www.lucidchart.com/blog/database-design-best-practices)[4](https://www.sisense.com/blog/better-sql-schema/)[6](https://www.integrate.io/blog/complete-guide-to-database-schema-design-guide/).
- **Consistent Naming Conventions:** Stick to a naming convention throughout your schema (e.g., lowercase with underscores)[4](https://www.sisense.com/blog/better-sql-schema/)[8](https://www.reddit.com/r/Database/comments/rrwmtv/are_there_any_good_rules_of_thumb_dos_and_donts/).
- **Use Appropriate Data Types:** Select the smallest and most suitable data type for each column to optimize storage and performance[5](https://www.guvi.in/blog/database-design-principles-and-best-practices/).
- **Indexing:** Create indexes on columns that are frequently searched or used in joins, but avoid over-indexing to prevent slow write operations[3](https://vertabelo.com/blog/best-practices-for-database-design/)[5](https://www.guvi.in/blog/database-design-principles-and-best-practices/).
- **Documentation:** Maintain up-to-date documentation for your schema and queries for future reference[3](https://vertabelo.com/blog/best-practices-for-database-design/)[6](https://www.integrate.io/blog/complete-guide-to-database-schema-design-guide/).
- **Avoid Over-Normalization:** Normalize to reduce redundancy, but don't split data into too many tables unnecessarily, as this can complicate queries[4](https://www.sisense.com/blog/better-sql-schema/).

---

## 🔗 Navigation

**📚 [← Back to Main Guide](README.md)**

**Next Topic:** [JOINS in SQL →](JOINS%20in%20SQL.md)

### 📖 Complete Learning Path:
1. **SQL Fundamentals** ← *You are here*
2. [JOINS in SQL](JOINS%20in%20SQL.md)
3. [String Functions](Strings%20in%20SQL.md)
4. [Subqueries](Subqueries%20in%20SQL.md)
5. [CASE Statements](CASE%20Statement%20in%20SQL.md)
6. [UNION Operations](Unions%20in%20SQL.md)
7. [Window Functions](Window%20Functions%20in%20SQL.md)
8. [Common Table Expressions (CTEs)](Common%20Table%20Expressions%20(CTEs)%20in%20MySQL.md)
9. [Stored Procedures](Stored%20Procedures%20in%20SQL.md)
10. [Temporary Tables](Temporary%20Tables%20in%20SQL.md)