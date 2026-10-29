# Relationships in PostgreSQL

A **relationship** means how two tables are connected to each other.

**Example:** In a school database, we can connect the `students` table with the `courses` table.

There are three common types of relationships.

## 1. One-to-One (1:1)

**Definition:** One row in the first table is connected to only one row in the second table.

**Example:** One person has one passport, and each passport belongs to one person.

```text
PERSON  ─────────  PASSPORT
  One                 One
```

## 2. One-to-Many (1:N)

**Definition:** One row in the first table can be connected to many rows in the second table.

**Example:** One customer can place many orders, but each order belongs to one customer.

```text
CUSTOMER  ───────<  ORDERS
   One                Many
```

## 3. Many-to-Many (M:N)

**Definition:** Many rows in the first table can be connected to many rows in the second table. We use a third table to connect them.

**Example:** One student can join many courses, and one course can have many students.

```text
STUDENTS  ─────  ENROLLMENTS  ─────  COURSES
  Many              Connects           Many
                    Both Tables
```
