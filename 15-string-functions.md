# PostgreSQL String Functions

String functions help you work with text values such as names, emails, and descriptions. They are useful for formatting, cleaning, searching, and combining data.

The examples below use the `employees` table from [Task 01](./11-task-01.md).

## CONCAT

Combines two or more strings into one value.

```sql
SELECT first_name, last_name,
       CONCAT(first_name, ' ', last_name) AS full_name
FROM employees;
```

## CONCAT_WS

Similar to `CONCAT`, but inserts a separator between values.

```sql
SELECT first_name, last_name,
       CONCAT_WS(' ', first_name, last_name) AS full_name
FROM employees;
```

## SUBSTR

Returns part of a string starting from a given position.

```sql
SELECT first_name,
       SUBSTR(first_name, 1, 3) AS first_3_chars
FROM employees;
```

## LEFT and RIGHT

Returns characters from the start or end of a string.

```sql
SELECT first_name,
       LEFT(first_name, 3) AS left_3,
       RIGHT(first_name, 3) AS right_3
FROM employees;
```

## LENGTH

Returns the number of characters in a string.

```sql
SELECT first_name,
       LENGTH(first_name) AS name_length
FROM employees;
```

## UPPER and LOWER

Convert text to uppercase or lowercase.

```sql
SELECT first_name,
       UPPER(first_name) AS upper_name,
       LOWER(last_name) AS lower_last_name
FROM employees;
```

## TRIM, LTRIM, and RTRIM

Remove spaces or characters from the beginning/end of a string.

```sql
SELECT '  PostgreSQL   ' AS raw_value,
       TRIM('  PostgreSQL   ') AS trimmed_value,
       LTRIM('  PostgreSQL') AS left_trimmed,
       RTRIM('PostgreSQL  ') AS right_trimmed;
```

You can also remove specific characters:

```sql
SELECT TRIM(BOTH '$' FROM '$100.00$') AS cleaned_value;
```

## REPLACE

Replaces all occurrences of a substring with another substring.

```sql
SELECT email,
       REPLACE(email, '@', ' at ') AS modified_email
FROM employees;
```

## POSITION

Finds the position of a substring inside a string.

```sql
SELECT email,
       POSITION('@' IN email) AS at_sign_position
FROM employees;
```

## REVERSE

Returns a string with its characters in reverse order.

```sql
SELECT first_name,
       REVERSE(first_name) AS reversed_name
FROM employees;
```

## STRING_AGG

Combines multiple values into a single string. This is especially useful after grouping data.

```sql
SELECT dept,
       STRING_AGG(first_name, ', ') AS employee_names
FROM employees
GROUP BY dept;
```

You can also control the order inside the aggregation:

```sql
SELECT dept,
       STRING_AGG(first_name, ', ' ORDER BY first_name) AS employee_names
FROM employees
GROUP BY dept;
```

## Example: clean and format employee names

```sql
SELECT first_name,
       last_name,
       UPPER(TRIM(first_name)) AS clean_first_name,
       CONCAT_WS(' ', UPPER(first_name), last_name) AS formatted_name
FROM employees;
```

## Summary

Common PostgreSQL string functions include:

- `CONCAT` and `CONCAT_WS` to join text
- `SUBSTR`, `LEFT`, and `RIGHT` to extract text
- `LENGTH` to measure text length
- `UPPER` and `LOWER` to change letter case
- `TRIM`, `LTRIM`, and `RTRIM` to clean text
- `REPLACE` to swap text values
- `POSITION` to find text locations
- `REVERSE` to reverse a string
- `STRING_AGG` to combine text from multiple rows

These functions are very helpful when working with names, email addresses, reports, and user-generated text.
