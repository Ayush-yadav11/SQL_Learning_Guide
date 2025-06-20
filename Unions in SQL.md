## Unions in SQL

The `UNION` operator in SQL is used to combine the result sets of two or more `SELECT` statements into a single result set. This is particularly useful when you want to retrieve data from multiple tables or queries and present them as one unified dataset.

---

## **Key Features of SQL UNION**

- **Combines Results:** Merges the output of multiple `SELECT` queries.
    
- **Removes Duplicates:** By default, `UNION` removes duplicate rows from the combined result set. If you wish to include duplicates, use `UNION ALL` instead[1](https://www.w3schools.com/sql/sql_union.asp)[2](https://www.programiz.com/sql/union)[5](https://docs.oracle.com/en/database/oracle/oracle-database/18/sqlrf/The-UNION-ALL-INTERSECT-MINUS-Operators.html)[7](https://hightouch.com/sql-dictionary/sql-union).
    
- **Column Requirements:** Each `SELECT` statement within the `UNION` must have:
    
    - The same number of columns.
    - Similar data types in corresponding columns.
    - The columns must be in the same order[1](https://www.w3schools.com/sql/sql_union.asp)[2](https://www.programiz.com/sql/union)[3](https://www.sqlshack.com/sql-union-overview-usage-and-examples/)[6](https://trainings.internshala.com/blog/sql-union/).

---

## **Syntax**

```sql
SELECT column1, column2, ... 
FROM table1 
UNION SELECT column1, column2, ... 
FROM table2
;
```
- To include duplicates, use `UNION ALL`:
```sql
SELECT column1, column2, ... 
FROM table1 
UNION ALL SELECT column1, column2, ... 
FROM table2
;
```
---

## **Examples**

**Basic Example:**

```sql
SELECT City 
FROM Customers 
UNION SELECT City 
FROM Suppliers 
ORDER BY City
;
```
This returns a list of distinct cities from both the Customers and Suppliers tables[1](https://www.w3schools.com/sql/sql_union.asp).

**With WHERE Clause:**
```sql
SELECT City, Country 
FROM Customers 
WHERE Country='Germany' 
UNION SELECT City, Country 
FROM Suppliers 
WHERE Country='Germany' 
ORDER BY City
;
```
This returns distinct German cities from both tables[1](https://www.w3schools.com/sql/sql_union.asp)[2](https://www.programiz.com/sql/union).

**Using UNION ALL:**

```sql
SELECT City 
FROM Customers 
UNION ALL 
SELECT City 
FROM Suppliers 
ORDER BY City
;
```
This returns all cities, including duplicates[1](https://www.w3schools.com/sql/sql_union.asp)[2](https://www.programiz.com/sql/union)[5](https://docs.oracle.com/en/database/oracle/oracle-database/18/sqlrf/The-UNION-ALL-INTERSECT-MINUS-Operators.html).

**Aliasing with UNION:**

```sql

SELECT 'Customer' AS Type, ContactName, City, Country 
FROM Customers 
UNION SELECT 'Supplier', ContactName, City, Country 
FROM Suppliers;
```
This query adds a column (`Type`) to indicate whether the person is a customer or supplier[1](https://www.w3schools.com/sql/sql_union.asp)[7](https://hightouch.com/sql-dictionary/sql-union).

---

## **Use Cases**

- **Merging Data:** Combine data from similar tables (e.g., employees and contractors) into a single report[7](https://hightouch.com/sql-dictionary/sql-union).
- **Reporting:** Create unified lists, such as all unique cities from multiple sources.
- **Data Integration:** Merge results from different databases or systems.

---

## **Best Practices & Notes**

- The column names in the result set are usually taken from the first `SELECT` statement[1](https://www.w3schools.com/sql/sql_union.asp).
- You can use `ORDER BY` at the end of the last `SELECT` statement to sort the final result[1](https://www.w3schools.com/sql/sql_union.asp)[3](https://www.sqlshack.com/sql-union-overview-usage-and-examples/).
- `UNION` is available in all major SQL databases (MySQL, PostgreSQL, Oracle, SQL Server, etc.)[7](https://hightouch.com/sql-dictionary/sql-union).

| Operator  | Removes Duplicates | Includes Duplicates | Use Case                          |
| --------- | ------------------ | ------------------- | --------------------------------- |
| UNION     | Yes                | No                  | Distinct combined results         |
| UNION ALL | No                 | Yes                 | All results, including duplicates |

Next -- [[Strings in SQL]]