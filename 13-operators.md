# PostgreSQL Operators

## Logical Operators

### AND

Returns rows only when both conditions are true.

```sql
SELECT fname, lname, dept, salary
FROM employees
WHERE dept = 'Sales' AND salary > 50000;
```

### OR

Returns rows when at least one condition is true.

```sql
SELECT fname, lname, dept
FROM employees
WHERE dept = 'Sales' OR dept = 'Marketing';
```

### NOT

Returns rows for which the condition is false.

```sql
SELECT fname, lname, dept
FROM employees
WHERE NOT dept = 'Sales';
```

## Relational Operators

### Equal to (`=`)

Matches values that are equal to the specified value.

```sql
SELECT fname, lname, dept
FROM employees
WHERE dept = 'Sales';
```

### Not equal to (`<>`)

Matches values that are different from the specified value.

```sql
SELECT fname, lname, dept
FROM employees
WHERE dept <> 'Sales';
```

### Not equal to (`!=`)

Matches values that are different from the specified value.

```sql
SELECT fname, lname, dept
FROM employees
WHERE dept != 'Sales';
```

### Greater than (`>`)

Matches values greater than the specified value.

```sql
SELECT fname, lname, salary
FROM employees
WHERE salary > 50000;
```

### Less than (`<`)

Matches values less than the specified value.

```sql
SELECT fname, lname, salary
FROM employees
WHERE salary < 50000;
```

### Greater than or equal to (`>=`)

Matches values greater than or equal to the specified value.

```sql
SELECT fname, lname, salary
FROM employees
WHERE salary >= 50000;
```

### Less than or equal to (`<=`)

Matches values less than or equal to the specified value.

```sql
SELECT fname, lname, salary
FROM employees
WHERE salary <= 50000;
```

## IN

Matches a value against any value in the specified list.

```sql
SELECT fname, lname, dept
FROM employees
WHERE dept IN ('Sales', 'Marketing', 'IT');
```

## NOT IN

Matches values that are not in the specified list.

```sql
SELECT fname, lname, dept
FROM employees
WHERE dept NOT IN ('Sales', 'Marketing', 'IT');
```

## BETWEEN

Matches values within the specified inclusive range.

```sql
SELECT fname, lname, salary
FROM employees
WHERE salary BETWEEN 40000 AND 60000;
```