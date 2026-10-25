# Task 01: Create an Employees Table

Create an `employees` table using the SQL below. It stores each employee's name, email address, department, salary, and hire date.

## SQL

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

## Line-by-line explanation

- `CREATE TABLE employees (` — Starts creating a table named `employees`.
- `emp_id SERIAL PRIMARY KEY,` — Creates an automatically numbered ID that uniquely identifies each employee.
- `fname VARCHAR(50) NOT NULL,` — Stores a first name of up to 50 characters; a value is required.
- `lname VARCHAR(50) NOT NULL,` — Stores a last name of up to 50 characters; a value is required.
- `email VARCHAR(100) NOT NULL UNIQUE,` — Stores a required email address of up to 100 characters; duplicate addresses are not allowed.
- `dept VARCHAR(50),` — Stores a department name of up to 50 characters; this value is optional.
- `salary DECIMAL(10, 2) DEFAULT 30000.00,` — Stores a salary with up to 10 digits total and 2 decimal places; defaults to `30000.00`.
- `hire_date DATE NOT NULL DEFAULT CURRENT_DATE` — Stores a required hire date; uses today's date if none is provided.
- `);` — Closes the column list and runs the table definition.