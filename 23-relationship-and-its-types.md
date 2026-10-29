# Relationships in SQL

A relationship in SQL connects tables through keys—typically a primary key in one table and a foreign key in another—to represent how their rows are associated.

## Types of relationships

### One-to-one (1:1)

Each row in one table is related to at most one row in the other table, and vice versa.

```text
PERSON                 PASSPORT
person.id (PK)  1 ─── 1  passport.person_id (FK)
```

### One-to-many (1:N)

One row in the first table can be related to many rows in the second table; each row in the second table relates to one row in the first.

```text
CUSTOMER                ORDER
customer.id (PK) 1 ───<  order.customer_id (FK)
                   one     many
```

### Many-to-many (M:N)

Many rows in either table can relate to many rows in the other, represented by a junction table containing foreign keys to both tables.

```text
STUDENT             ENROLLMENT              COURSE
student.id (PK) 1 ───< student_id (FK)
                              course_id (FK) >─── 1 course.id (PK)
                  many       many
```