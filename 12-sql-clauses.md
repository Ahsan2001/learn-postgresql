# SQL Clauses in PostgreSQL

This lesson covers `WHERE`, `DISTINCT`, `ORDER BY`, `LIMIT`, and `LIKE` using the `employees` table from [Task 01](./11-task-01.md).

## 1. Definitions

- `WHERE` — Filters rows, returning only the rows that match a condition.
- `DISTINCT` — Removes duplicate rows from the query result. When used with selected columns, it returns each unique combination of those column values once.
- `ORDER BY` — Sorts the result by one or more columns. `ASC` sorts in ascending order (the default); `DESC` sorts in descending order.
- `LIMIT` — Sets the maximum number of rows returned.
- `LIKE` — Matches text against a pattern. `%` represents zero or more characters, and `_` represents exactly one character. `ILIKE` performs a case-insensitive match in PostgreSQL.

## 2. Examples using the Task 01 `employees` table

Task 01 creates this table:

```sql
CREATE TABLE employees (
    emp_id SERIAL PRIMARY KEY,
    fname VARCHAR(50) NOT NULL,
    lname VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    dept VARCHAR(50),
    salary DECIMAL(10, 2) DEFAULT 30000.00,
    hire_date DATE NOT NULL DEFAULT CURRENT_DATE
);
```

### `WHERE`: filter rows

For example, find employees in the Sales department:

```sql
SELECT fname, lname, dept
FROM employees
WHERE dept = 'Sales';
```

Only rows where `dept` is `Sales` are returned.

### `DISTINCT`: return unique values

For example, list each department once:

```sql
SELECT DISTINCT dept
FROM employees;
```

If several employees work in the same department, that department appears only once in the result. If `dept` is `NULL`, the result can include one `NULL` entry.

### `ORDER BY`: sort rows

For example, list employees from the highest salary to the lowest:

```sql
SELECT fname, lname, salary
FROM employees
ORDER BY salary DESC;
```

Use `ASC` for the opposite order. To sort by salary and then alphabetically by last name, use `ORDER BY salary DESC, lname ASC`.

### `LIMIT`: return only some rows

For example, show the five highest-paid employees:

```sql
SELECT fname, lname, salary
FROM employees
ORDER BY salary DESC
LIMIT 5;
```

Using `ORDER BY` with `LIMIT` makes it clear which five rows you want.

### `LIKE`: match text patterns

For example, find employees whose first name starts with `A`:

```sql
SELECT fname, lname
FROM employees
WHERE fname LIKE 'A%';
```

The pattern examples below use the `fname` column:

- Starts with `A`: `WHERE fname LIKE 'A%'`
- Ends with `A`: `WHERE fname LIKE '%A'`
- Contains `A`: `WHERE fname LIKE '%A%'`
- Has `A` as its second character: `WHERE fname LIKE '_A%'`
- Case-insensitive match for `john`: `WHERE fname ILIKE '%john%'`

`LIKE` is case-sensitive; use PostgreSQL's `ILIKE` when matching text without regard to letter case.

## Combining the clauses

These clauses can be used together. For example, find the first five employees whose first name starts with `A`, ordered by last name:

```sql
SELECT DISTINCT fname, lname
FROM employees
WHERE fname LIKE 'A%'
ORDER BY lname ASC
LIMIT 5;
```

The general order for this query is `SELECT`, `FROM`, `WHERE`, `ORDER BY`, then `LIMIT`. `DISTINCT` comes immediately after `SELECT`.
