## Temporary Tables
**Temporary tables** (temp tables) are special tables used to store data temporarily during the lifespan of a session or transaction. They are useful for holding intermediate results, simplifying complex queries, and improving performance by breaking down large operations into manageable steps[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[5](https://milvus.io/ai-quick-reference/how-do-you-create-a-temporary-table-in-sql)[7](https://www.databasestar.com/sql-temp-table/).

---

## How to Create a Temporary Table

**In MySQL and PostgreSQL:**  
Use the `CREATE TEMPORARY TABLE` statement:

sql

`CREATE TEMPORARY TABLE temp_table_name (   column1 datatype,  column2 datatype,  ... );`

- Example:
    
    sql
    
    `CREATE TEMPORARY TABLE temp_users (   id INT,  name VARCHAR(50) );`
    
- The table exists only within the current session and is automatically dropped when the session ends[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[5](https://milvus.io/ai-quick-reference/how-do-you-create-a-temporary-table-in-sql)[10](https://dev.mysql.com/doc/refman/8.4/en/create-temporary-table.html).
    

**In SQL Server:**  
Use the `#` prefix for local temp tables and `##` for global temp tables:

- **Local Temporary Table:**
    
    sql
    
    `CREATE TABLE #temp_table_name (   column1 datatype,  column2 datatype,  ... );`
    
    - Only visible in the current session; dropped automatically when the session ends[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[6](https://www.dbvis.com/thetable/sql-server-temp-table-mechanism-complete-guide/)[7](https://www.databasestar.com/sql-temp-table/)[8](https://www.c-sharpcorner.com/article/sql-temporary-tables-syntax-types-and-usage/).
        
- **Global Temporary Table:**
    
    sql
    
    `CREATE TABLE ##temp_table_name (   column1 datatype,  column2 datatype,  ... );`
    
    - Visible to all sessions; dropped when all sessions referencing it are closed[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[6](https://www.dbvis.com/thetable/sql-server-temp-table-mechanism-complete-guide/)[7](https://www.databasestar.com/sql-temp-table/)[8](https://www.c-sharpcorner.com/article/sql-temporary-tables-syntax-types-and-usage/).
        

---

## Inserting and Using Data

You can insert, update, select, and delete data in temp tables just like regular tables:

sql

`INSERT INTO #temp_table_name (column1, column2) VALUES (value1, value2); SELECT * FROM #temp_table_name;`

Or, create and populate in one step (SQL Server):

sql

`SELECT column1, column2 INTO #temp_table_name FROM original_table WHERE condition;`

---

## When to Use Temporary Tables

- Storing intermediate results for complex queries or reporting[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[5](https://milvus.io/ai-quick-reference/how-do-you-create-a-temporary-table-in-sql)[6](https://www.dbvis.com/thetable/sql-server-temp-table-mechanism-complete-guide/).
    
- Reusing filtered or transformed data multiple times in a session.
    
- Improving performance by avoiding repeated computations.
    
- Simplifying multi-step data processing, especially in stored procedures.
    

---

## Key Points

- **Scope:** Temp tables are session-specific (local) or global (all sessions, SQL Server only)[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[6](https://www.dbvis.com/thetable/sql-server-temp-table-mechanism-complete-guide/)[7](https://www.databasestar.com/sql-temp-table/).
    
- **Lifetime:** Automatically dropped at the end of the session or can be manually dropped with `DROP TABLE`[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[6](https://www.dbvis.com/thetable/sql-server-temp-table-mechanism-complete-guide/).
    
- **Visibility:** Not listed in regular table listings; only accessible within their scope[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[5](https://milvus.io/ai-quick-reference/how-do-you-create-a-temporary-table-in-sql).
    
- **Storage:** In SQL Server, temp tables are stored in the `tempdb` system database[6](https://www.dbvis.com/thetable/sql-server-temp-table-mechanism-complete-guide/)[8](https://www.c-sharpcorner.com/article/sql-temporary-tables-syntax-types-and-usage/).
    

---

## Example: Temporary Table in MySQL

sql

`CREATE TEMPORARY TABLE recent_orders AS SELECT order_id, customer_id, total FROM orders WHERE order_date >= '2025-06-01';`

---

## Example: Temporary Table in SQL Server

sql

`CREATE TABLE #temp_customers (   id INT,  cust_name VARCHAR(100) ); INSERT INTO #temp_customers (id, cust_name) SELECT id, cust_name FROM customers WHERE active = 1; SELECT * FROM #temp_customers;`

---

**In summary:**  
Temporary tables are powerful tools for managing intermediate data in SQL, providing flexibility and efficiency for complex data processing tasks. Their syntax and behavior vary slightly between database systems, but the core concept remains the same: they exist only for the duration of your session or until explicitly dropped[1](https://www.tutorialspoint.com/sql/sql-temporary-tables.htm)[5](https://milvus.io/ai-quick-reference/how-do-you-create-a-temporary-table-in-sql)[7](https://www.databasestar.com/sql-temp-table/).