# PostgreSQL GROUP BY

`GROUP BY` combines rows that have the same value in one or more columns so aggregate functions can calculate a result for each group.

The examples below use the `employees` table from [Task 01](./11-task-01.md).

## Count employees in each department

```sql
SELECT dept, COUNT(*) AS employee_count
FROM employees
GROUP BY dept;
```

This returns one row for each department and the number of employees in it. Rows where `dept` is `NULL` are counted as their own group.

## Calculate the average salary in each department

```sql
SELECT dept, AVG(salary) AS average_salary
FROM employees
GROUP BY dept;
```

## Group by more than one column

Group by both department and hire date to get a separate count for each department and date combination:

```sql
SELECT dept, hire_date, COUNT(*) AS employee_count
FROM employees
GROUP BY dept, hire_date
ORDER BY dept, hire_date;
```

When using `GROUP BY`, each selected column must either be included in the grouping or be used in an aggregate function such as `COUNT`, `SUM`, `AVG`, `MIN`, or `MAX`.