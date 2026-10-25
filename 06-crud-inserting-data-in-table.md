# Insert Data into a PostgreSQL Table

This section explains how to insert data into the `person` table in PostgreSQL.

## 1) Open pgAdmin 4 and connect to your database

- Open pgAdmin 4.
- Select your database.
- Click on the Query Tool button.

## 2) Insert data into the `person` table

Run the following SQL query in the Query Tool:

```sql
INSERT INTO person (id, name, city)
VALUES (101, 'Ahsan', 'Karachi');
```

You can also insert multiple rows at once:

```sql
INSERT INTO person (id, name, city)
VALUES
    (103, 'Khan', 'Islamabad'),
    (202, 'Hasan', 'Lahore');
```

If you want to insert values in the same order as the column list, you can also use:

```sql
INSERT INTO person
VALUES (101, 'Ahsan', 'Karachi');
```

## 3) Execute the query

- Click the Execute button in pgAdmin.
- The data will be inserted into the table.



