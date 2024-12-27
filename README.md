# Basic SQL Statement

Sql is the thing for database purpose. These are the basic syntax:
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

This query retrieves the company name and its location for rows where the industry column has the value "Media."
```
SELECT company, location
FROM data
WHERE industry = "Media";
```
