## Subqueries
A **subquery** (also called a nested query or inner query) is a SQL query placed inside another query such as within a SELECT, INSERT, UPDATE, or DELETE statement. The outer query, which contains the subquery, is called the outer query or main query. Subqueries are always enclosed in parentheses and are executed first, with their results used by the outer query[1](https://hightouch.com/sql-dictionary/sql-subqueries)[2](https://www.programiz.com/sql/subquery)[5](https://dev.to/abhay_yt_52a8e72b213be229/understanding-sql-subqueries-a-complete-guide-with-examples-3jff)[6](https://www.w3resource.com/sql/subqueries/understanding-sql-subqueries.php)[7](https://www.tutorialspoint.com/sql/sql-sub-queries.htm)[8](https://www.dbvis.com/thetable/the-complete-guide-to-sql-subqueries/).

---
## Where Can Subqueries Be Used?

Subqueries can be placed in various parts of a SQL statement:

- **WHERE clause:** To filter rows based on the result of another query.
- **FROM clause:** To use the result of a subquery as a temporary table or derived table.
- **SELECT clause:** To compute values for each row.
- **HAVING clause:** To filter groups after aggregation[6](https://www.w3resource.com/sql/subqueries/understanding-sql-subqueries.php)[8](https://www.dbvis.com/thetable/the-complete-guide-to-sql-subqueries/).

---

## Basic Syntax


```sql

SELECT column1, column2 
FROM table 
WHERE column OPERATOR (SELECT column 
						FROM another_table 
						WHERE condition);
```
- The subquery is executed first.
- Its result is used by the outer query[1](https://hightouch.com/sql-dictionary/sql-subqueries)[2](https://www.programiz.com/sql/subquery)[6](https://www.w3resource.com/sql/subqueries/understanding-sql-subqueries.php)[7](https://www.tutorialspoint.com/sql/sql-sub-queries.htm).

---

## Types of Subqueries

|Type|Description|Example Syntax|
|---|---|---|
|**Single-row**|Returns a single value (row) and is used with operators like =, <, >|`WHERE column = (SELECT MAX(column) FROM table)`|
|**Multi-row**|Returns multiple values and is used with operators like IN, ANY, ALL|`WHERE column IN (SELECT column FROM table WHERE ...)`|
|**Correlated**|References columns from the outer query and is evaluated once for each row of the outer query|`WHERE column > (SELECT AVG(column) FROM table WHERE outer_table.id = inner_table.id)`|

- **Scalar subquery:** Returns a single value and can be used in SELECT or WHERE clauses[5](https://dev.to/abhay_yt_52a8e72b213be229/understanding-sql-subqueries-a-complete-guide-with-examples-3jff)[9](https://blog.stackademic.com/sql-subqueries-with-code-examples-ec4a7bfba8e2?gi=d45de8545a46).
    
- **Correlated subquery:** References columns from the outer query and is executed repeatedly, once for each row of the outer query[5](https://dev.to/abhay_yt_52a8e72b213be229/understanding-sql-subqueries-a-complete-guide-with-examples-3jff)[9](https://blog.stackademic.com/sql-subqueries-with-code-examples-ec4a7bfba8e2?gi=d45de8545a46).
    

---

## Example Usages

**1. Subquery in WHERE Clause**


```sql

SELECT first_name 
FROM Customers 
WHERE age = (SELECT MAX(age) 
				FROM Customers)
;
```
Finds the first name(s) of the customer(s) with the highest age[2](https://www.programiz.com/sql/subquery)[5](https://dev.to/abhay_yt_52a8e72b213be229/understanding-sql-subqueries-a-complete-guide-with-examples-3jff).

**2. Subquery in FROM Clause**

```sql
SELECT sub.* 
FROM (SELECT * 
		FROM Orders 
		WHERE status = 'Pending') sub 
WHERE sub.amount > 1000
;```

Uses a subquery as a derived table to further filter results[3](https://mode.com/sql-tutorial/sql-sub-queries/).

**3. Correlated Subquery**

```sql

SELECT Name 
FROM Employees e 
WHERE Salary > (SELECT AVG(Salary) 
				FROM Employees 
				WHERE DepartmentID = e.DepartmentID)
;
```
Finds employees earning more than the average salary in their department[5](https://dev.to/abhay_yt_52a8e72b213be229/understanding-sql-subqueries-a-complete-guide-with-examples-3jff)[9](https://blog.stackademic.com/sql-subqueries-with-code-examples-ec4a7bfba8e2?gi=d45de8545a46).

---

## Key Points and Rules

- Subqueries must be enclosed in parentheses[1](https://hightouch.com/sql-dictionary/sql-subqueries)[7](https://www.tutorialspoint.com/sql/sql-sub-queries.htm).
- They can be nested within other subqueries.
- Subqueries can return a single value, a single row, a single column, or a table (set of rows and columns)[7](https://www.tutorialspoint.com/sql/sql-sub-queries.htm).
- The inner query must be able to run independently.
- Subqueries can be used with operators such as =, <, >, IN, ANY, ALL, EXISTS, and NOT EXISTS[1](https://hightouch.com/sql-dictionary/sql-subqueries)[8](https://www.dbvis.com/thetable/the-complete-guide-to-sql-subqueries/).
- In SQL Server, subqueries can be nested up to 32 levels (practically, much less is common)[4](https://learn.microsoft.com/en-us/sql/relational-databases/performance/subqueries?view=sql-server-ver17).

---

## Summary Table

| Placement     | Purpose                           | Example                                                   |
| ------------- | --------------------------------- | --------------------------------------------------------- |
| WHERE clause  | Filter based on subquery result   | `WHERE id IN (SELECT id FROM ...)`                        |
| FROM clause   | Use subquery as a temporary table | `FROM (SELECT ... ) AS sub`                               |
| SELECT clause | Compute value for each row        | `SELECT (SELECT MAX(salary) FROM salaries) AS max_salary` |
| HAVING clause | Filter groups after aggregation   | `HAVING SUM(sales) > (SELECT AVG(sales) FROM ...)`        |
---

## 🔗 Navigation

**📚 [← Back to Main Guide](README.md)**

**Previous Topic:** [← String Functions](Strings%20in%20SQL.md) | **Next Topic:** [CASE Statements →](CASE%20Statement%20in%20SQL.md)

### 📖 Complete Learning Path:
1. [SQL Fundamentals](SQL.md)
2. [JOINS in SQL](JOINS%20in%20SQL.md)
3. [String Functions](Strings%20in%20SQL.md)
4. **Subqueries** ← *You are here*
5. [CASE Statements](CASE%20Statement%20in%20SQL.md)
6. [UNION Operations](Unions%20in%20SQL.md)
7. [Window Functions](Window%20Functions%20in%20SQL.md)
8. [Common Table Expressions (CTEs)](Common%20Table%20Expressions%20(CTEs)%20in%20MySQL.md)
9. [Stored Procedures](Stored%20Procedures%20in%20SQL.md)
10. [Temporary Tables](Temporary%20Tables%20in%20SQL.md)