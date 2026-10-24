# Create a Database in PostgreSQL

This guide shows how to create a new database using the SQL Shell (`psql`).

## 1) Open SQL Shell (psql)

- Press the Windows key.
- Search for `SQL Shell (psql)`.
- Open the application.

## 2) Connect to PostgreSQL

When the terminal opens, you will be prompted for connection details.

Use the default values or the credentials you set during installation.

Example:

- Server: `localhost`
- Database: `postgres`
- Port: `5432`
- Username: `postgres`
- Password: `root` (if you used that during setup)

## 3) Create a new database

Run the following SQL command:

```sql
CREATE DATABASE test;
```

This creates a database named `test`.

## 4) List databases

To verify that the database was created, run:

```sql
SELECT datname FROM pg_database;
```

Or use:

```sql
\l
```

The output should include the new database `test`.

