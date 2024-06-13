---
tags:
  - code
  - code_snippet
  - SQL/widecard
keywords: 
topics: 
language: SQL
date of note: 2024-04-19
---

## Code Snippet Summary

>[!important]
>Use **wildcard** to match strings and query based on text pattern


## Code

>[!info]  **SQL Wildcard Characters**
>- A **wildcard character** is used to *substitute* one or more *characters* in a string.
>- Wildcard characters are used with the [`LIKE`](https://www.w3schools.com/sql/sql_like.asp) operator. The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column.


>[!example]
> Return all customers that starts with the letter 'a':
> ```sql
> SELECT * FROM Customers  
> WHERE CustomerName LIKE 'a%';
> ```
> 

>[!example]
>Return all customers that ends with the pattern 'es':
> ```sql
> SELECT * FROM Customers  
> WHERE CustomerName LIKE '%es';
> ```


## Wildcard Characters

| Symbol | Description                                                    |
| ------ | -------------------------------------------------------------- |
| %      | Represents *zero or more* characters                           |
| _      | Represents a *single character*                                |
| []     | Represents any *single character* within *the brackets* *      |
| ^      | Represents any character *not* *in the brackets* *             |
| -      | Represents any single character *within the specified range* * |
| {}     | Represents any *escaped character* **                          |

\* Not supported in PostgreSQL and MySQL databases.
\** Supported **only in Oracle databases**.

### Match any single character with `_` 

>[!example]
>Return all customers with a `City` starting with any character, followed by "ondon":
> ```sql
> SELECT * FROM Customers  
> WHERE City LIKE '_ondon';
> ```


> [!example]
> Return all customers with a `City` starting with "L", followed by any 3 characters, ending with "on":
> ```sql
> SELECT * FROM Customers  
> WHERE City LIKE 'L___on';
> ```
> 

### Match any given characters within `[]` 

>[!example]
>Return all customers starting with either "b", "s", or "p":
> ```sql
>SELECT * FROM Customers  
>WHERE CustomerName LIKE '[bsp]%';
> ```

### Match a range of characters within `[]` 

>[!example]
>Return all customers starting with "a", "b", "c", "d", "e" or "f":
> ```sql
>SELECT * FROM Customers  
>WHERE CustomerName LIKE '[a-f]%';
> ```









-----------
##  Recommended Notes

- [SQL Wildcards](https://www.w3schools.com/sql/sql_wildcards.asp)