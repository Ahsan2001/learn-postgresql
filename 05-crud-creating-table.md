# CRUD in PostgreSQL

This section demonstrates how to create a table called `person` in PostgreSQL.

## 1) Open pgAdmin 4 and connect to your database

- Open pgAdmin 4.
- Select your database.
- Click on the Query Tool button.

## 2) Create the `person` table

Run the following SQL query in the Query Tool:

```sql
CREATE TABLE person (
    id INT,
    name VARCHAR(100),
    city VARCHAR(100)
);
```

## 3) Execute the query and verify the table

- Click the Execute button.
- Check whether the `person` table appears in the database tree or object list.

## 4) Connect to the database using the SQL shell

Open the SQL shell and connect to the database where the table was created:

```sql
\c persondb
```

## 5) View table information

To inspect the table structure, run:

```sql
\d person
```

This command displays information about the `person` table, including its columns and data types.