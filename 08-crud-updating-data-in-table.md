# Update Data in a PostgreSQL Table

This section explains how to update existing records in the `person` table in PostgreSQL.

## 1) Open pgAdmin 4 and connect to your database

- Open pgAdmin 4.
- Select your database.
- Click on the Query Tool button.

## 2) Update data in the `person` table

Run the following SQL query in the Query Tool:

```sql
UPDATE person
SET city = 'London'
WHERE id = 101;
```

You can also update a record using another column, such as `name`:

```sql
UPDATE person
SET city = 'Pindi'
WHERE name = 'Ahsan';
```

## 3) Execute the query

- Click the Execute button in pgAdmin.
- The selected rows will be updated.

## 4) Verify the changes

To check the updated values, run:

```sql
SELECT * FROM person;
```

This displays the table with the updated records.
