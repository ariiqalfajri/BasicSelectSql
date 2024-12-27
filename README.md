# Basic SQL Statement
This projects source is from [AlexTheAnalyst](https://github.com/AlexTheAnalyst/MySQL-YouTube-Series/)'s GitHub and [Hackerrank](https://www.hackerrank.com/domains/sql)'s website.

SQL (Structured Query Language) is a standardized programming language designed for managing and manipulating relational databases. These are the basic syntax:
### Select Statement

The `SELECT` statement is used to interact with columns and determine which ones to include in your output. To select all columns from a table, use `*` after the `SELECT` statement. For selecting specific columns, list their names separated by commas `,` or specify a single column name after the `SELECT` statement if you want to select only that column. Additionally, the `FROM` statement is included to specify the table from which the data will be retrieved. Here are the example:

For all columns
```
SELECT *
FROM data;
```
For some columns
```
SELECT company, location
FROM data;
```
For single column

```
SELECT country
FROM data;
```

*Additional* `DISTINCT` select, this will remove duplicate column. Even if there are multiple rows with the same value in the column, DISTINCT will include each value only once in the result.
```
SELECT DISTINCT CITY
FROM data;
```

*Additional* select, this will give 2 column output 
```
SELECT salary, salary * 12
FROM data;
```

### Order by
The `ORDER BY` clause will sort the result in either `ASC`(ascending) or `DESC`(descending) order. It will sort by ascending in default.
For example, this query retrieves the list of countries with highest to lowest taxes:
```
SELECT country
FROM data
ORDER BY taxes DESC;
```
### Group by
The `GROUP BY` clause groups together rows that have the same values in the specified column or columns. Its is going to allow us to group rows that have the same data and run aggregate functions on them.

You have to have the same columns you're grouping on in the `GROUP BY` clause,
```
SELECT location
FROM data
GROUP BY location;
```
This query groups the data by the location column, and since no aggregate function is used, it only returns the distinct location values.
However, if you want to select other columns alongside location, you must use aggregate functions (like `AVG`, `SUM`, `COUNT`, etc.) on those columns, because SQL needs to know how to handle the rows that are grouped together. For example,
```
SELECT location, avg(total_laid_off)
FROM parks_and_recreation.layoffs
GROUP BY location;
```
This query will return the average number of total layoffs for each location. The `AVG`(total_laid_off) is an aggregate function that calculates the average value for each group (grouped by location).

### Where Clause
The `WHERE` clause is used to filter rows of data. It retrieves only the records that meet a specified condition. `WHERE` clause also supports various operators for different conditions, such as `>`, `<`, `>=`, `<=`, `=`, and `!=`. Here are the example:

This query will output only the rows where the value in the country column is "Indonesia".
```
SELECT *
FROM data
WHERE country = "Indonesia";
```

This query retrieves the company name and its location for rows where the industry column has the value "Media".
```
SELECT company, location
FROM data
WHERE industry = "Media";
```

Additionally, you can include logical operators like `AND` or `OR` to combine multiple conditions in the `WHERE` clause:
- `AND`: Ensures all conditions must be true.
- `OR`: Ensures at least one of the conditions must be true.

This query **only** retrieves the company name and its location for rows where the industry column has the value "Media" **and** the country value is "Indonesia" (e.g., news company)
```
SELECT company, location 
FROM data 
WHERE industry = "Media" AND country = "Indonesia";
```

This query retrieves the company name and its location for rows where the industry column is "Media" **or** the country column is "Indonesia" (e.g., companies located in Indonesia but not in the media industry, as well as media companies that are not based in Indonesia).
```
SELECT company, location 
FROM data 
WHERE industry = "Media" OR country = "Indonesia";
```

### Like Clause
The `LIKE` clause in Sql is used to search for a specified pattern within a column. There are some wildcards in `LIKE`:
- `%`: Represents zero, one, or multiple characters.
- `_`: Represents a single character.

This query retrieves rows where "name" appears anywhere in the name (e.g., "TechJohn", "FinhTech").
```
SELECT company
FROM data 
WHERE name LIKE '%Tech%'';
```

This query retrieves rows where the email ends with ".com".
```
SELECT GmailUser
FROM data 
WHERE email LIKE '%.com';
```

This query retrieves rows where the name is four characters long, starts with "J," and ends with "n" (e.g., "John", "Jean").
```
SELECT gender
FROM data 
WHERE name LIKE 'J__n';
```

### Having Clause
Similar to the `WHERE` clause, the `HAVING` clause also filters rows, but it is specifically used to filter grouped data based on *aggregate* values. This is the example:
```
SELECT gender, AVG(age)
FROM data 
GROUP BY gender
HAVING AVG(age) > 40
```
In this query, we are calculating the average age grouped by gender. Since we are filtering based on the aggregated average age (AVG(age) > 40), we must use the `HAVING` clause instead of `WHERE`, as `HAVING` is specifically designed for conditions on aggregated data.

### Limit Clause
The `LIMIT` clause will limit the output to specific rows. For example, in the following query, the `LIMIT 2` ensures that only the first two rows of the result are returned:
```
SELECT *
FROM data 
LIMIT 2;
```
This query will retrieve all columns (*) from the data table, but it will only return 2 rows, regardless of how many rows are actually in the table. You can also use `LIMIT` with `ORDER BY` to control which rows are returned, such as selecting the top N results based on some ordering criteria.

### Aliasing
Aliasing or `AS` will change the name of the column (for the most part) to whatever we want.
This is the basic example:
```
SELECT salary * 12 as annual_salary
FROM data ;
```

We can also use `AS` to shorten table name:
```
SELECT d.name, d.salary
FROM data AS d;
```

We could even use it in `ORDER BY` clauses, this will print the name and annual salary column:
```
SELECT name, salary * 12 AS annual_salary
FROM data
ORDER BY annual_salary;
```

--------------------------------------------

**SUMMARY**
| Statement/Clauses | Purposes |
| ------ | ------ |
| Select `SELECT`| Show specific column(s) from a table |
| Order by `ORDER BY` |Sort rows in ascending `ASC` or descending `DESC` order |
| Group by `GROUP BY` | Group rows that have the same values in specified columns, often used with aggregate functions |
| Where `WHERE` | Filter rows based on specified conditions |
| Like `LIKE` | Search for patterns in a column using wildcard characters  |
| Having `HAVING` |Filter rows based on aggregate conditions|
| Limit `LIMIT` |Restrict the number of rows returned in the result set|
| Aliases `AS` | Rename columns or tables for clarity in the query|
