# CASE Expressions in PostgreSQL

Use a `CASE` expression to return a value based on one or more conditions. It works like an if/then/else statement and can be used in a `SELECT` query.

The examples below use the `employees` table from [Task 01](./11-task-01.md).

## Searched CASE

A searched `CASE` checks each `WHEN` condition in order and returns the result for the first condition that is true. If none are true, it returns the value in `ELSE`. If `ELSE` is omitted, the result is `NULL`.

This query groups employees into salary categories:

```sql
SELECT fname, salary,
       CASE
           WHEN salary >= 50000 THEN 'High'
           WHEN salary >= 40000 AND salary < 50000 THEN 'Mid'
           ELSE 'Low'
       END AS sal_cat
FROM employees;
```

The result includes each employee's first name and salary, along with a calculated `sal_cat` value:

- `High` for salaries of 50,000 or more
- `Mid` for salaries from 40,000 up to, but not including, 50,000
- `Low` for salaries below 40,000

`sal_cat` is the output column alias. It does not add a column to the table or change stored data.

## Handle NULL values

In the query above, a `NULL` salary does not match either condition, so it is categorized as `Low` by `ELSE`. To label missing salaries separately, check for `NULL` explicitly:

```sql
SELECT fname, salary,
       CASE
           WHEN salary IS NULL THEN 'Unknown'
           WHEN salary >= 50000 THEN 'High'
           WHEN salary >= 40000 AND salary < 50000 THEN 'Mid'
           ELSE 'Low'
       END AS sal_cat
FROM employees;
```

## View the table in `psql`

In the PostgreSQL command-line tool (`psql`), use `\d` to show the table structure:

```text
\d employees
```

To display the table's rows, run this SQL query:

```sql
SELECT *
FROM employees;
```