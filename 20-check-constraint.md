# CHECK Constraints in PostgreSQL

A `CHECK` constraint requires each non-`NULL` value in a row to satisfy a condition. PostgreSQL rejects an `INSERT` or `UPDATE` that violates the condition. Use `NOT NULL` as well if a value must be provided, because a `CHECK` alone allows `NULL`.

## Add a column with constraints

Start with a `person` table:

```sql
CREATE TABLE person (
    id INTEGER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    name VARCHAR(50)
);
```

Add a phone column and constraints. The `CHECK` requires at least 10 characters, and `UNIQUE` prevents two rows from having the same non-`NULL` phone value.

```sql
ALTER TABLE person
ADD COLUMN phone VARCHAR(15),
ADD CONSTRAINT person_phone_length_check CHECK (LENGTH(phone) >= 10),
ADD CONSTRAINT person_phone_unique UNIQUE (phone);
```

`VARCHAR(15)` also limits the value to 15 characters. This check validates the length; it does not ensure that the value contains only digits.

## Insert and validate data

Use quotes when inserting phone numbers because they are text. This also preserves leading zeroes.

```sql
INSERT INTO person (name, phone)
VALUES ('Ahsan', '0123456789');
```

The following insert fails because the phone value has fewer than 10 characters:

```sql
INSERT INTO person (name, phone)
VALUES ('Sam', '123');
```

PostgreSQL reports a check-constraint violation. If you run statements interactively in `psql`, the error does not remove previously committed rows.

## Name and remove a constraint

Naming a constraint makes it easier to identify in error messages and when altering the table. The constraint above is named `person_phone_length_check`. Remove it with:

```sql
ALTER TABLE person
DROP CONSTRAINT person_phone_length_check;
```

Dropping the constraint removes the length rule; it does not remove the `phone` column or the separate unique constraint.

## View the table in `psql`

In the PostgreSQL command-line tool (`psql`), use `\d` to show the table's columns, data types, and constraints:

```text
\d person
```

Use a SQL query to show the rows stored in the table:

```sql
SELECT *
FROM person;
```

To list tables in the current schema in `psql`, use:

```text
\dt
```
