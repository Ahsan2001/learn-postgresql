# Data Types and Constraints in PostgreSQL

## Data types

A data type determines what kind of value a table column can store. Common PostgreSQL types include:

- `INT` — whole numbers
- `VARCHAR(n)` — text up to `n` characters; use `TEXT` for longer or unrestricted text
- `BOOLEAN` — `TRUE` or `FALSE`
- `DATE` — calendar dates
- `DECIMAL(p, s)` — exact numbers that can include digits after the decimal point, such as prices. `p` is the total number of digits, and `s` is the number of digits after the decimal point. For example, `DECIMAL(8, 2)` can store values like `12345.67`.

## Constraints

Constraints are rules that help keep table data valid. Common constraints include:

- `NOT NULL` — requires a value
- `UNIQUE` — prevents duplicate values
- `PRIMARY KEY` — uniquely identifies each row
- `CHECK` — requires values to meet a condition
- `DEFAULT` — supplies a value when none is provided

## Example

```sql
CREATE TABLE person (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(255) UNIQUE,
    age INTEGER CHECK (age >= 0),
    balance DECIMAL(8, 2),
    active BOOLEAN DEFAULT TRUE
);
```

Each column has a data type that describes the kind of value it stores. The constraints set rules: `PRIMARY KEY` identifies each row, `NOT NULL` requires a name, `UNIQUE` prevents duplicate email addresses, `CHECK` requires a non-negative age, and `DEFAULT` sets `active` to `TRUE` when no value is provided.
