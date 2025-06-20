**Window functions** in SQL perform calculations across a set of rows related to the current row, known as a "window." Unlike aggregate functions (like `SUM`, `AVG`, etc.), which collapse rows into a single result per group, window functions retain each row and add calculated values alongside the original data[1](https://mode.com/sql-tutorial/sql-window-functions/)[2](https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet)[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/)[5](https://www.coginiti.co/tutorials/intermediate/sql-window-functions/)[6](https://hightouch.com/sql-dictionary/sql-window-functions).

---

## Key Features

- **Calculations Across Rows:** Window functions can compute running totals, moving averages, rankings, and more, all while keeping the original row structure intact[1](https://mode.com/sql-tutorial/sql-window-functions/)[2](https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet)[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/)[5](https://www.coginiti.co/tutorials/intermediate/sql-window-functions/)[6](https://hightouch.com/sql-dictionary/sql-window-functions).
- **No Grouping Required:** Unlike `GROUP BY`, window functions do not group rows into a single output row[1](https://mode.com/sql-tutorial/sql-window-functions/)[2](https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet)[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/).
- **Flexible Partitioning:** You can partition data into groups using `PARTITION BY`, and order rows within those groups using `ORDER BY`[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/)[5](https://www.coginiti.co/tutorials/intermediate/sql-window-functions/)[6](https://hightouch.com/sql-dictionary/sql-window-functions).

---

## Basic Syntax

```sql

SELECT   column1,  
window_function(column2) OVER ([PARTITION BY partition_column]
[ORDER BY order_column] [ROWS BETWEEN ...]  ) AS result_column 
FROM   table_name;
```
- `window_function`: Examples include `SUM`, `AVG`, `ROW_NUMBER`, `RANK`, `LAG`, `LEAD`, etc.
- `OVER`: Mandatory clause that defines the window.
- `PARTITION BY`: (Optional) Divides the data into partitions (like groups).
- `ORDER BY`: (Optional) Orders rows within each partition.
- `ROWS BETWEEN ...`: (Optional) Specifies the frame of rows for calculation[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/)[5](https://www.coginiti.co/tutorials/intermediate/sql-window-functions/)[6](https://hightouch.com/sql-dictionary/sql-window-functions).

---

## Common Window Functions

|Function|Description|Example Use Case|
|---|---|---|
|`ROW_NUMBER()`|Assigns a unique sequential number to each row|Row numbering|
|`RANK()`|Assigns a rank to each row, with gaps for ties|Competition ranking|
|`DENSE_RANK()`|Like `RANK()`, but no gaps for ties|Dense ranking|
|`SUM()`|Calculates running or partitioned totals|Running totals, subtotal by group|
|`AVG()`|Calculates running or partitioned averages|Moving averages|
|`LAG()`|Accesses data from a previous row|Compare current to previous value|
|`LEAD()`|Accesses data from a following row|Compare current to next value|
|`NTILE(n)`|Splits rows into `n` ranked buckets|Quartiles, deciles, etc.|
|`FIRST_VALUE()`|Gets the first value in the window frame|Find first sale per group|
|`LAST_VALUE()`|Gets the last value in the window frame|Find last sale per group|

---

## Example: Running Total

```sql

SELECT  order_date,revenue, SUM(revenue) OVER (ORDER BY order_date) AS running_total 
FROM   sales 
ORDER BY   order_date;
```
This calculates a cumulative sum (`running_total`) of revenue by order date, without collapsing the rows[1](https://mode.com/sql-tutorial/sql-window-functions/)[6](https://hightouch.com/sql-dictionary/sql-window-functions).

---

## Example: Row Ranking

```sql

SELECT   product_name,  price,  RANK() OVER (ORDER BY price DESC) AS price_rank FROM   products;
```
Ranks products by price from highest to lowest[2](https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet)[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/).

---

## When to Use Window Functions

- Calculating running totals, moving averages, or cumulative metrics[2](https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet)[6](https://hightouch.com/sql-dictionary/sql-window-functions)
- Ranking or numbering rows within partitions[2](https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet)[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/)[5](https://www.coginiti.co/tutorials/intermediate/sql-window-functions/)
- Comparing each row to previous or next rows (e.g., finding differences, trends)[5](https://www.coginiti.co/tutorials/intermediate/sql-window-functions/)[6](https://hightouch.com/sql-dictionary/sql-window-functions)
- Simplifying complex analytics that would otherwise require subqueries or self-joins[6](https://hightouch.com/sql-dictionary/sql-window-functions)

---

## Supported Databases

Window functions are available in all major SQL databases, including PostgreSQL, SQL Server, Oracle, MySQL, SQLite, and more[6](https://hightouch.com/sql-dictionary/sql-window-functions).

---

**In summary:**  
Window functions are essential for advanced analytics in SQL, enabling you to perform calculations over sets of rows while preserving the detail of each row in your result set[1](https://mode.com/sql-tutorial/sql-window-functions/)[2](https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet)[3](https://www.stratascratch.com/blog/the-ultimate-guide-to-sql-window-functions/)[5](https://www.coginiti.co/tutorials/intermediate/sql-window-functions/)[6](https://hightouch.com/sql-dictionary/sql-window-functions).

Next -- [[Common Table Expressions (CTEs) in MySQL]]