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

This query retrieves rows where the email ends with "gmail.com".
```
SELECT GmailUser
FROM data 
WHERE email LIKE '%gmail.com';
```

This query retrieves rows where the name is four characters long, starts with "J," and ends with "n" (e.g., "John", "Jean").
```
SELECT gender
FROM data 
WHERE name LIKE 'J__n';
```
