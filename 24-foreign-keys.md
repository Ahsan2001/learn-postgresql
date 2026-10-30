# Foreign Keys in PostgreSQL

A **foreign key** is a column (or group of columns) that points to a primary key in another table, connecting the rows and preventing references to rows that do not exist.

## Customers and orders example

One customer can have many orders, and each order belongs to one customer. This is a **one-to-many relationship**:

```text
CUSTOMERS                         ORDERS
cust_id (PK)  1 ───────────────<  cust_id (FK)
              one                 many
```

Create the `customers` table first because `orders` will reference it:

```sql
CREATE TABLE customers (
    cust_id SERIAL PRIMARY KEY,
    cust_name VARCHAR(100) NOT NULL
);
```

Add a foreign key on `orders.cust_id` that references `customers.cust_id`:

```sql
CREATE TABLE orders (
    ord_id SERIAL PRIMARY KEY,
    ord_date DATE DEFAULT CURRENT_DATE,
    price NUMERIC NOT NULL,
    cust_id INTEGER NOT NULL,
    FOREIGN KEY (cust_id)
    REFERENCES customers (cust_id)
);
```

`customers.cust_id` is the primary key, and `orders.cust_id` is the foreign key. The foreign key ensures an order can only refer to a customer that exists. `NOT NULL` also requires every order to have a customer.
