# Read Data from a PostgreSQL Table

This section explains how to read data from the `person` table in PostgreSQL.

## 1) Open pgAdmin 4 and connect to your database

- Open pgAdmin 4.
- Select your database.
- Click on the Query Tool button.

## 2) Read data from the `person` table

Run the following SQL query in the Query Tool:

```sql
SELECT * FROM person;
```

This returns all rows and columns from the `person` table.

### Read a single column

```sql
SELECT name FROM person;
```

This returns only the `name` column.

### Read multiple columns

```sql
SELECT name, city FROM person;
```

This returns only the `name` and `city` columns.

## 3) Execute the query

- Click the Execute button in pgAdmin.
- The result will be displayed in a table format.

You can now view the stored records and filter the data as needed in future queries.
