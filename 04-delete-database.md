# Delete a Database in PostgreSQL

This guide explains how to delete an existing PostgreSQL database.

## 1) View available databases

Before deleting a database, check the list of existing databases:

```sql
SELECT datname FROM pg_database;
```

Or:

```sql
\l
```

## 2) Disconnect the database in pgAdmin

If the database is open in pgAdmin 4, disconnect it before deleting it.

This prevents errors caused by deleting an active database.

## 3) Delete the database

Run the following SQL command:

```sql
drop database test;
```

This permanently deletes the `test` database.

## 4) Refresh pgAdmin

Go back to pgAdmin 4 and press `F5` to refresh the database list.

The deleted database should no longer appear in the list.

Note: Be careful when deleting a database because the data inside it will be removed permanently.
