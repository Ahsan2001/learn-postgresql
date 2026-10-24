# Change Database in PostgreSQL

This guide explains how to switch from one PostgreSQL database to another.

## 1) View available databases

Before changing databases, list the available databases:

```sql
SELECT datname FROM pg_database;
```

Or:

```sql
\l
```

## 2) Connect to a different database

Use the following command to switch to the `test` database:

```sql
\c test
```

This connects the current session to the `test` database.

Once connected, you can run queries and create tables in that database.
