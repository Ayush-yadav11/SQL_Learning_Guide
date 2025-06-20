MySQL provides a comprehensive set of string functions to manipulate, search, and analyze character string data. These functions are essential for formatting, cleaning, and extracting information from text fields in your database.

---
## **Commonly Used String Functions**

|Function|Description|Example Usage|
|---|---|---|
|CONCAT()|Concatenates two or more strings.|`CONCAT('Hello', ' ', 'World')` → 'Hello World'|
|CONCAT_WS()|Concatenates strings with a separator.|`CONCAT_WS('-', '2025', '06', '11')` → '2025-06-11'|
|LENGTH()|Returns the length of a string in bytes.|`LENGTH('abc')` → 3|
|CHAR_LENGTH()|Returns the length of a string in characters.|`CHAR_LENGTH('abc')` → 3|
|LOWER() / LCASE()|Converts a string to lowercase.|`LOWER('ABC')` → 'abc'|
|UPPER() / UCASE()|Converts a string to uppercase.|`UPPER('abc')` → 'ABC'|
|SUBSTRING()|Extracts a substring from a string.|`SUBSTRING('abcdef', 2, 3)` → 'bcd'|
|LEFT()|Returns the leftmost characters from a string.|`LEFT('abcdef', 3)` → 'abc'|
|RIGHT()|Returns the rightmost characters from a string.|`RIGHT('abcdef', 2)` → 'ef'|
|TRIM()|Removes leading and trailing spaces.|`TRIM(' abc ')` → 'abc'|
|LTRIM()|Removes leading spaces.|`LTRIM(' abc')` → 'abc'|
|RTRIM()|Removes trailing spaces.|`RTRIM('abc ')` → 'abc'|
|REPLACE()|Replaces occurrences of a substring with another substring.|`REPLACE('abcabc', 'a', 'x')` → 'xbcxbc'|
|REPEAT()|Repeats a string a specified number of times.|`REPEAT('ab', 3)` → 'ababab'|
|REVERSE()|Reverses the characters in a string.|`REVERSE('abc')` → 'cba'|
|INSTR()|Returns the position of the first occurrence of a substring.|`INSTR('database', 'base')` → 5|
|LOCATE()|Returns the position of a substring within a string.|`LOCATE('a', 'banana')` → 2|
|POSITION()|Synonym for LOCATE().|`POSITION('a' IN 'banana')` → 2|
|SUBSTRING_INDEX()|Returns a substring from a string before a specified number of occurrences of a delimiter.|`SUBSTRING_INDEX('a,b,c', ',', 2)` → 'a,b'|
|INSERT()|Inserts a substring at a specified position.|`INSERT('abcdef', 2, 3, 'xyz')` → 'axyzef'|
|ASCII()|Returns the ASCII value of the leftmost character.|`ASCII('A')` → 65|
|CHAR()|Returns the character for each integer ASCII code passed.|`CHAR(65)` → 'A'|
|FORMAT()|Formats a number as a string with a specified number of decimal places and locale.|`FORMAT(12345.6789, 2)` → '12,345.68'|
|SPACE()|Returns a string consisting of a specified number of spaces.|`SPACE(5)` → ' '|
|SOUNDEX()|Returns a soundex string (phonetic representation).|`SOUNDEX('Hello')`|
|BIT_LENGTH()|Returns the length of a string in bits.|`BIT_LENGTH('abc')` → 24|
|QUOTE()|Escapes the argument for use in an SQL statement.|`QUOTE("O'Reilly")` → `'O\'Reilly'`|

---

## **Examples**

- **Concatenate Strings:**
    ```sql
    SELECT CONCAT('My', 'SQL'); -- Output: 'MySQL'
    ```
- **Extract Substring:**
```sql
    SELECT SUBSTRING('Database', 2, 4); -- Output: 'atab'
    ```
- **Replace Substring:**
    ```sql
    SELECT REPLACE('2025-06-11', '-', '/'); -- Output: '2025/06/11'
    ```
- **Get String Length:**
    ```sql
    SELECT LENGTH('abc'); -- Output: 3 SELECT CHAR_LENGTH('abc'); -- Output: 3
    ```

---

## **Notes**

- Many functions are multibyte safe, meaning they work correctly with Unicode and other multibyte character sets[1](https://dev.mysql.com/doc/en/string-functions.html).
- Some functions like `LENGTH()` count bytes, while `CHAR_LENGTH()` counts characters—important for multibyte strings[2](https://www.tutorialspoint.com/mysql/mysql-string-functions.htm)[6](https://www.mysqltutorial.org/mysql-string-functions/).
- Functions like `TRIM()`, `LTRIM()`, and `RTRIM()` are useful for cleaning up data by removing unwanted spaces[1](https://dev.mysql.com/doc/en/string-functions.html)[6](https://www.mysqltutorial.org/mysql-string-functions/).
- Pattern matching can use `LIKE`, `INSTR()`, `LOCATE()`, and regular expressions for more advanced searches[3](https://phoenixnap.com/kb/mysql-string-function)[6](https://www.mysqltutorial.org/mysql-string-functions/).


## **What are the differences between LEFT(), RIGHT(), and SUBSTRING()**
## Key Differences

- **LEFT()**:
    - Returns the leftmost N characters from a string.
    - Syntax: `LEFT(string, number_of_characters)`
    - Useful when you always want the beginning of the string[5](https://database.guide/left-vs-substring-in-sql-server-whats-the-difference/)[7](https://learn.microsoft.com/en-us/archive/technet-wiki/17948.t-sql-right-left-substring-and-charindex-functions)[9](https://www.ibm.com/docs/SSGU8G_14.1.0/com.ibm.sqls.doc/ids_sqs_0258.htm).
- **RIGHT()**:
    - Returns the rightmost N characters from a string.
    - Syntax: `RIGHT(string, number_of_characters)`
    - Useful when you always want the end of the string[7](https://learn.microsoft.com/en-us/archive/technet-wiki/17948.t-sql-right-left-substring-and-charindex-functions)[9](https://www.ibm.com/docs/SSGU8G_14.1.0/com.ibm.sqls.doc/ids_sqs_0258.htm).
- **SUBSTRING()**:
    - Returns a substring starting at any position for a specified length.
    - Syntax: `SUBSTRING(string, start_position, length)`
    - The first character position is 1.
    - More flexible, as it can extract from anywhere in the string—not just the start or end[5](https://database.guide/left-vs-substring-in-sql-server-whats-the-difference/)[7](https://learn.microsoft.com/en-us/archive/technet-wiki/17948.t-sql-right-left-substring-and-charindex-functions)[6](https://www.sqlshack.com/sql-substring-function-and-its-performance-tips/).
        

---

## Example

Suppose you have the string 'HELLO WORLD':

- `LEFT('HELLO WORLD', 3)` returns `'HEL'` (first 3 characters)
- `RIGHT('HELLO WORLD', 3)` returns `'RLD'` (last 3 characters)
- `SUBSTRING('HELLO WORLD', 4, 5)` returns `'LO WO'` (5 characters starting from position 4)[7](https://learn.microsoft.com/en-us/archive/technet-wiki/17948.t-sql-right-left-substring-and-charindex-functions).

---

## Summary

- Use **LEFT()** for the start, **RIGHT()** for the end, and **SUBSTRING()** for any position within the string.
- **SUBSTRING()** is the most flexible, as it can mimic LEFT() and RIGHT() (with the right parameters), but LEFT() and RIGHT() are more concise and readable for their specific purposes[5](https://database.guide/left-vs-substring-in-sql-server-whats-the-difference/)[6](https://www.sqlshack.com/sql-substring-function-and-its-performance-tips/)[7](https://learn.microsoft.com/en-us/archive/technet-wiki/17948.t-sql-right-left-substring-and-charindex-functions).

Next --[[CASE Statement in SQL]]