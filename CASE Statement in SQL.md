## CASE Statement
The `CASE` statement in SQL is a versatile conditional expression that allows you to perform logic similar to if-then-else statements in programming languages. It evaluates conditions and returns a result when the first condition is met. If no conditions are true, it can return a default value specified by the `ELSE` clause; otherwise, it returns NULL if `ELSE` is omitted[1](https://www.w3schools.com/sql/sql_case.asp)[2](https://mode.com/sql-tutorial/sql-case/)[3](https://www.programiz.com/sql/case)[5](https://webreference.com/sql/references/case/)[6](https://hightouch.com/sql-dictionary/sql-case).

---
**Basic Syntax:**

```sql
CASE     
WHEN condition1 THEN result1    
WHEN condition2 THEN result2      
[ELSE result_default] END
``` 
- `condition1`, `condition2`, ...: Expressions that are evaluated in order.
- `result1`, `result2`, ...: Values returned when the corresponding condition is true.
- `ELSE result_default`: (Optional) Value returned if none of the conditions are met[1](https://www.w3schools.com/sql/sql_case.asp)[3](https://www.programiz.com/sql/case)[5](https://webreference.com/sql/references/case/)[6](https://hightouch.com/sql-dictionary/sql-case)

---
## Example Usage

**1. Categorizing Data in a SELECT Statement:**

```sql

SELECT product_name, price,   
CASE    
WHEN price > 100 THEN 'expensive'    
WHEN price > 50 THEN 'moderate'    
ELSE 'cheap'  END AS price_category FROM products;
```
This query creates a new column (`price_category`) that labels products as 'expensive', 'moderate', or 'cheap' based on their price[5](https://webreference.com/sql/references/case/)[6](https://hightouch.com/sql-dictionary/sql-case).

**2. Adding Conditional Columns:**

```sql

SELECT OrderID, Quantity,   
CASE    
WHEN Quantity > 30 THEN 'The quantity is greater than 30'    
WHEN Quantity = 30 THEN 'The quantity is 30'   
ELSE 'The quantity is under 30'  
END AS QuantityText FROM OrderDetails;
```
This example adds a descriptive text column based on the value of `Quantity`[1](https://www.w3schools.com/sql/sql_case.asp).

**3. Using CASE in ORDER BY:**

```sql

SELECT CustomerName, City, Country 
FROM Customers 
ORDER BY   
CASE    
WHEN City IS NULL THEN Country    
ELSE City  
END;
```
This orders customers by city, but if the city is NULL, it orders by country instead[1](https://www.w3schools.com/sql/sql_case.asp).

---
## Key Points

- The `CASE` statement can be used in `SELECT`, `UPDATE`, `DELETE`, and `SET` statements, as well as in clauses like `WHERE`, `ORDER BY`, and `HAVING`[4](https://careerfoundry.com/en/blog/data-analytics/case-statements-in-sql/)[6](https://hightouch.com/sql-dictionary/sql-case)[9](https://learn.microsoft.com/en-us/sql/t-sql/language-elements/case-transact-sql?view=sql-server-ver17).
- The `ELSE` clause is optional but recommended for clarity and to handle all possible cases[5](https://webreference.com/sql/references/case/)[6](https://hightouch.com/sql-dictionary/sql-case)
- The `CASE` statement always ends with the `END` keyword[1](https://www.w3schools.com/sql/sql_case.asp)[3](https://www.programiz.com/sql/case)[4](https://careerfoundry.com/en/blog/data-analytics/case-statements-in-sql/)[5](https://webreference.com/sql/references/case/).
- There are two types of CASE expressions:
    - **Simple CASE:** Compares an expression to a set of values.
    - **Searched CASE:** Evaluates a set of Boolean expressions[4](https://careerfoundry.com/en/blog/data-analytics/case-statements-in-sql/).

---
## Typical Use Cases

- **Data Transformation:** Categorizing or labeling data based on conditions.
- **Custom Calculations:** Calculating values conditionally.
- **Dynamic Sorting:** Customizing sort order.
- **Data Cleaning:** Standardizing or replacing values[6](https://hightouch.com/sql-dictionary/sql-case). 

---

## 🔗 Navigation

**📚 [← Back to Main Guide](README.md)**

**Previous Topic:** [← Subqueries](Subqueries%20in%20SQL.md) | **Next Topic:** [UNION Operations →](Unions%20in%20SQL.md)

### 📖 Complete Learning Path:
1. [SQL Fundamentals](SQL.md)
2. [JOINS in SQL](JOINS%20in%20SQL.md)
3. [String Functions](Strings%20in%20SQL.md)
4. [Subqueries](Subqueries%20in%20SQL.md)
5. **CASE Statements** ← *You are here*
6. [UNION Operations](Unions%20in%20SQL.md)
7. [Window Functions](Window%20Functions%20in%20SQL.md)
8. [Common Table Expressions (CTEs)](Common%20Table%20Expressions%20(CTEs)%20in%20MySQL.md)
9. [Stored Procedures](Stored%20Procedures%20in%20SQL.md)
10. [Temporary Tables](Temporary%20Tables%20in%20SQL.md)