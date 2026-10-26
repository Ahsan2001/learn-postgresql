# PostgreSQL Aggregate Functions

The examples below use the `employees` table from [Task 01](./11-task-01-create-bank-employee.md).

## COUNT

Counts the number of rows or non-`NULL` values.

```sql
SELECT COUNT(*) AS employee_count
FROM employees;
```

```sql
SELECT COUNT(dept) AS employees_with_department
FROM employees;
```

## SUM

Calculates the total of numeric values.

```sql
SELECT SUM(salary) AS total_salary
FROM employees;
```

## AVG

Calculates the average of numeric values.

```sql
SELECT AVG(salary) AS average_salary
FROM employees;
```

## MIN

Returns the smallest value in a column.

```sql
SELECT MIN(salary) AS lowest_salary
FROM employees;
```

## MAX

Returns the largest value in a column.

```sql
SELECT MAX(salary) AS highest_salary
FROM employees;
```