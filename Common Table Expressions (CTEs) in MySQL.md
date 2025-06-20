## Common Table Expressions
A **Common Table Expression (CTE)** in MySQL is a named temporary result set defined within the execution scope of a single SQL statement. CTEs are particularly useful for simplifying complex queries, improving readability, and enabling recursive operations such as traversing hierarchical data structures[1](https://dev.mysql.com/doc/refman/8.4/en/with.html)[5](https://www.scaler.com/topics/mysql-tutorial/cte-in-mysql/)[6](https://www.mysqltutorial.org/mysql-basics/mysql-cte/)[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).

---
## Syntax

The basic syntax for a CTE in MySQL is:


```sql

WITH cte_name [ (column1, column2, ...) ] AS (   SELECT ...  FROM ...  WHERE ... ) SELECT ... 
FROM cte_name 
WHERE ...;
```
- `cte_name`: The name you assign to the CTE.
- `(column1, column2, ...)`: Optional list of column names for the CTE.
- The CTE is referenced in the main query just like a regular table or view[1](https://dev.mysql.com/doc/refman/8.4/en/with.html)[5](https://www.scaler.com/topics/mysql-tutorial/cte-in-mysql/)[6](https://www.mysqltutorial.org/mysql-basics/mysql-cte/)[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).

**Multiple CTEs** can be defined by separating them with commas:

```sql

WITH   cte1 AS (SELECT ...),  
cte2 AS (SELECT ...) 
SELECT ... 
FROM cte1 
JOIN cte2 ON ...;
```
Each CTE can reference tables or CTEs defined before it in the list[1](https://dev.mysql.com/doc/refman/8.4/en/with.html)[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).

---

## Key Use Cases

- **Simplifying complex queries:** Break down large queries into logical building blocks, improving maintainability and readability[3](https://hightouch.com/sql-dictionary/sql-common-table-expression-cte)[5](https://www.scaler.com/topics/mysql-tutorial/cte-in-mysql/)[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).
- **Avoiding subquery repetition:** Reuse the same result set multiple times within a query without repeating the subquery[3](https://hightouch.com/sql-dictionary/sql-common-table-expression-cte)[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).
- **Recursive queries:** Traverse hierarchical data (e.g., organizational charts, file systems) using recursive CTEs[5](https://www.scaler.com/topics/mysql-tutorial/cte-in-mysql/).
- **Query organization:** Separate logical sections of a query for easier debugging and understanding[3](https://hightouch.com/sql-dictionary/sql-common-table-expression-cte).

---

## Recursive CTEs

Recursive CTEs allow a CTE to reference itself, making it possible to process hierarchical or tree-structured data. The syntax involves a base case and a recursive case, combined with `UNION ALL`:

```sql

WITH RECURSIVE cte_name AS (   
SELECT ... -- Base case  
FROM ...  
WHERE ...   
UNION ALL   
SELECT ... -- Recursive case  
FROM table  
JOIN cte_name ON ...  
WHERE ... ) 
SELECT * 
FROM cte_name;
```
- The recursion continues until the recursive SELECT returns no more rows[5](https://www.scaler.com/topics/mysql-tutorial/cte-in-mysql/).
    

---

## Example: Simple CTE

```sql

WITH high_salary_employees AS (   SELECT employee_id, salary  
									FROM employees  
									WHERE salary > 50000 ) 
SELECT * 
FROM high_salary_employees;
```

This query defines a CTE for employees with a salary over 50,000 and then selects from it[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).

---

## Example: Recursive CTE

Suppose you have an `employees` table with `employee_id`, `manager_id`, and `name` columns. To list all employees in a hierarchy:

```sql

WITH RECURSIVE employee_hierarchy AS 
(
SELECT employee_id, manager_id, name, 0 AS level  
FROM employees  
WHERE manager_id IS NULL   
UNION ALL   
SELECT e.employee_id, e.manager_id, e.name, eh.level + 1  
FROM employees e  JOIN employee_hierarchy eh ON e.manager_id = eh.employee_id 
) 
SELECT * 
FROM employee_hierarchy;
```
This will return all employees, showing their level in the hierarchy[5](https://www.scaler.com/topics/mysql-tutorial/cte-in-mysql/).

---

## Requirements & Notes

- **MySQL version:** CTEs are supported in MySQL 8.0 and later[6](https://www.mysqltutorial.org/mysql-basics/mysql-cte/).
- **Scope:** CTEs exist only for the duration of the statement in which they are defined.
- **Performance:** CTEs can make queries more readable and sometimes more efficient, but performance depends on the query structure and optimizer[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).

---

**In summary:**  
CTEs in MySQL are a powerful feature for writing cleaner, more maintainable, and more efficient SQL queries, especially when dealing with complex logic or hierarchical data[1](https://dev.mysql.com/doc/refman/8.4/en/with.html)[5](https://www.scaler.com/topics/mysql-tutorial/cte-in-mysql/)[7](https://www.bomberbot.com/mysql/how-to-use-mysql-common-table-expressions-with-example-queries/).

---

## 🔗 Navigation

**📚 [← Back to Main Guide](README.md)**

**Previous Topic:** [← Window Functions](Window%20Functions%20in%20SQL.md) | **Next Topic:** [Stored Procedures →](Stored%20Procedures%20in%20SQL.md)

### 📖 Complete Learning Path:
1. [SQL Fundamentals](SQL.md)
2. [JOINS in SQL](JOINS%20in%20SQL.md)
3. [String Functions](Strings%20in%20SQL.md)
4. [Subqueries](Subqueries%20in%20SQL.md)
5. [CASE Statements](CASE%20Statement%20in%20SQL.md)
6. [UNION Operations](Unions%20in%20SQL.md)
7. [Window Functions](Window%20Functions%20in%20SQL.md)
8. **Common Table Expressions (CTEs)** ← *You are here*
9. [Stored Procedures](Stored%20Procedures%20in%20SQL.md)
10. [Temporary Tables](Temporary%20Tables%20in%20SQL.md)