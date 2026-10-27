# Rename a Table in PostgreSQL

Use the `ALTER TABLE` command with `RENAME TO` to change a table's name. Renaming a table keeps its existing columns and data.

## Rename a table

Use this syntax:

```sql
ALTER TABLE old_table_name
RENAME TO new_table_name;
```

For example, rename the `employees` table to `staff`:

```sql
ALTER TABLE employees
RENAME TO staff;
```

After renaming, refer to the table by its new name in queries:

```sql
SELECT *
FROM staff;
```

In the PostgreSQL command-line tool (`psql`), you can check the table name with `\dt`.