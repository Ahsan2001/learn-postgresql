# JOINs in PostgreSQL

A **JOIN** combines related rows from two or more tables using a matching column, such as `customers.cust_id` and `orders.cust_id`.

## Types of JOINs

- **INNER JOIN:** Returns rows with matching values in both tables.
- **LEFT JOIN:** Returns every row from the left table and matching rows from the right table; unmatched right-side columns are `NULL`.
- **RIGHT JOIN:** Returns every row from the right table and matching rows from the left table; unmatched left-side columns are `NULL`.
- **FULL OUTER JOIN:** Returns all rows from both tables, matching them where possible; unmatched columns are `NULL`.
- **CROSS JOIN:** Returns every possible combination of rows from both tables.

## Practical examples with `customers` and `orders`

These queries use the tables created in [Foreign Keys](./24-foreign-keys.md). Open pgAdmin 4, select the same database, and click **Query Tool**. Run a query by clicking **Execute**; its rows appear in the **Data Output** panel.

### INNER JOIN

List orders together with the matching customer name:

```sql
SELECT customers.cust_id, customers.cust_name, orders.ord_id, orders.ord_date, orders.price
FROM customers
INNER JOIN orders ON customers.cust_id = orders.cust_id;
```

### LEFT JOIN

List every customer, including customers who have not placed an order:

```sql
SELECT customers.cust_id, customers.cust_name, orders.ord_id, orders.ord_date, orders.price
FROM customers
LEFT JOIN orders ON customers.cust_id = orders.cust_id;
```

### RIGHT JOIN

List every order and its matching customer:

```sql
SELECT customers.cust_id, customers.cust_name, orders.ord_id, orders.ord_date, orders.price
FROM customers
RIGHT JOIN orders ON customers.cust_id = orders.cust_id;
```

### FULL OUTER JOIN

List all customers and all orders, including rows that have no match in the other table:

```sql
SELECT customers.cust_id, customers.cust_name, orders.ord_id, orders.ord_date, orders.price
FROM customers
FULL OUTER JOIN orders ON customers.cust_id = orders.cust_id;
```

### CROSS JOIN

Combine every customer with every order. The result contains one row for each possible customer-and-order combination:

```sql
SELECT customers.cust_id, customers.cust_name, orders.ord_id, orders.ord_date, orders.price
FROM customers
CROSS JOIN orders;
```

## Run and list results in `psql`

Connect to the database that contains the tables (replace `your_database` with its name):

```text
\c your_database
```

Run any of the `SELECT` queries above in `psql` to list its results. To list the table structure, use:

```text
\d customers
\d orders
```