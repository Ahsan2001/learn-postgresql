# Add or Remove a Column in PostgreSQL

Use the `ALTER TABLE` command to change the structure of an existing table without recreating it.

The examples below use the `employees` table from [Task 01](./11-task-01.md).

## Add a column

Use `ADD COLUMN` to add a column to a table. Existing rows will have `NULL` in the new column unless you specify a default value.

```sql
ALTER TABLE employees
ADD COLUMN phone VARCHAR(20);
```

To add a column with a default value:

```sql
ALTER TABLE employees
ADD COLUMN employment_status VARCHAR(20) DEFAULT 'active';
```

You can add more than one column in a single statement:

```sql
ALTER TABLE employees
ADD COLUMN phone VARCHAR(20),
ADD COLUMN city VARCHAR(100);
```

## Remove a column

Use `DROP COLUMN` to remove a column and its data from a table. This action deletes the values stored in that column.

```sql
ALTER TABLE employees
DROP COLUMN phone;
```

To avoid an error if the column does not exist, use `IF EXISTS`:

```sql
ALTER TABLE employees
DROP COLUMN IF EXISTS phone;
```

## Verify the table structure

In the PostgreSQL command-line tool (`psql`), use `\d` to display a table's columns and data types:

```sql
\d employees
```

> **Caution:** Dropping a column permanently removes its data. Make sure the column is no longer needed before running `DROP COLUMN`.