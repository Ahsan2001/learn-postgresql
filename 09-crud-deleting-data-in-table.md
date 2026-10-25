# Delete Data from a PostgreSQL Table

This section explains how to delete records from the `person` table in PostgreSQL.

## 1) Open pgAdmin 4 and connect to your database

- Open pgAdmin 4.
- Select your database.
- Click on the Query Tool button.

## 2) Delete data from the `person` table

Run the following SQL query in the Query Tool:

```sql
DELETE FROM person
WHERE id = 101;
```

This deletes the row where the `id` is `101`.

## 3) Execute the query

- Click the Execute button in pgAdmin.
- The selected row will be removed from the table.

## 4) Verify the changes

To check the remaining records, run:

```sql
SELECT * FROM person;
```

This displays the current contents of the `person` table after deletion.
