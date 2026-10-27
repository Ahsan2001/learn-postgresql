# Rename a Column in a PostgreSQL Table

Use the `ALTER TABLE` command with `RENAME COLUMN` to change a column's name. Renaming a column does not change the data stored in it.

The examples below use the `employees` table from [Task 01](./11-task-01.md).

## Rename a column

Use this syntax:

```sql
ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name;
```

For example, rename `fname` to `first_name`:

```sql
ALTER TABLE employees
RENAME COLUMN fname TO first_name;
```

The column's existing values are preserved. Update queries and application code that refer to the old column name to use the new name.

## Verify the column name

In the PostgreSQL command-line tool (`psql`), use `\d` to display the table structure:

```sql
\d employees
```