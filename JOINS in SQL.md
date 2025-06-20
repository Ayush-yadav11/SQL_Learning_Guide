SQL joins are used to combine rows from two or more tables based on a related column between them, allowing retrieval of related data spread across multiple tables in a database[1](https://www.w3schools.com/sql/sql_join.asp)[6](https://www.pingcap.com/article/mastering-sql-joins-guide-examples/). The main types of SQL joins are:

**1. INNER JOIN**

- Returns only the rows where there is a match in both tables based on the join condition.
    
- It excludes rows that do not have matching values in both tables.
    
- Example syntax:
```sql
SELECT columns 
FROM table1 INNER 
JOIN table2 ON table1.column = table2.column
;
```
- Use case: When you want records that exist in both tables only[2](https://www.datacamp.com/cheat-sheet/sql-joins-cheat-sheet)[4](https://www.w3schools.com/sql/sql_ref_join.asp)[5](https://en.wikipedia.org/wiki/Join_\(SQL\))[6](https://www.pingcap.com/article/mastering-sql-joins-guide-examples/).


**2. LEFT JOIN (LEFT OUTER JOIN)**

- Returns all rows from the left table and the matched rows from the right table.
    
- If there is no match, NULL values are returned for columns from the right table.
    
- Example syntax:
```sql
 SELECT columns 
 FROM table1 LEFT 
 JOIN table2 ON table1.column = table2.column
 ;
```
- Use case: When you want all records from the left table regardless of matches in the right table[2](https://www.datacamp.com/cheat-sheet/sql-joins-cheat-sheet)[4](https://www.w3schools.com/sql/sql_ref_join.asp)[6](https://www.pingcap.com/article/mastering-sql-joins-guide-examples/).
**3. RIGHT JOIN (RIGHT OUTER JOIN)**

- Returns all rows from the right table and matched rows from the left table.
    
- If no match is found, NULLs are returned for columns from the left table.
- Example syntax:
```sql
 SELECT columns 
 FROM table1 RIGHT 
 JOIN table2 ON table1.column = table2.column
 ;
```
- It is essentially the mirror of LEFT JOIN with the right table as the base[6](https://www.pingcap.com/article/mastering-sql-joins-guide-examples/)7.
    

**4. FULL JOIN (FULL OUTER JOIN)**

- Combines the results of both LEFT and RIGHT JOINs.
    
- Returns all rows when there is a match in either left or right table.
- Example syntax:
```sql
 SELECT columns 
 FROM table1 FULL 
 JOIN table2 ON table1.column = table2.column
 ;
```
- Rows without a match in the other table will have NULLs for that table’s columns[5](https://en.wikipedia.org/wiki/Join_\(SQL\))[6](https://www.pingcap.com/article/mastering-sql-joins-guide-examples/).
    

**5. CROSS JOIN**

- Produces the Cartesian product of the two tables, returning all possible combinations of rows.
    
- It does not require a join condition[5](https://en.wikipedia.org/wiki/Join_\(SQL\))[6](https://www.pingcap.com/article/mastering-sql-joins-guide-examples/).
    

**Other types:**

- **SELF JOIN:** A table is joined with itself to compare rows within the same table[2](https://www.datacamp.com/cheat-sheet/sql-joins-cheat-sheet).
    

**How joins work:**

- Joins are performed based on a join condition, typically involving a foreign key in one table and a primary key in another.
    
- The join condition uses logical operators like `=` to match rows.
    
- SQL implementations optimize join operations beyond the naive Cartesian product approach for efficiency[3](https://learn.microsoft.com/en-us/sql/relational-databases/performance/joins?view=sql-server-ver17)[5](https://en.wikipedia.org/wiki/Join_\(SQL\)).
```csv
Join Type,Description,Result
INNER JOIN,Rows with matching values in both tables,Only matching rows from both tables
LEFT JOIN,All rows from left table + matched rows from right, NULL for right if no match
RIGHT JOIN,All rows from right table + matched rows from left, NULL for left if no match
FULL JOIN,All rows with match in either table or All rows from both tables, NULLs where no match
CROSS JOIN,Cartesian product of rows,Every combination of rows from both tables
SELF JOIN,Table joined with itself,Compare rows within the same table
```

Next-- [[Unions in SQL]]