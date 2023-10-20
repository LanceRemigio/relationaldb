# Intersect 


The `INTERSECT` operator compares the result set of two queries and returns the results they have in common.

The syntax use of this operator is the done in the following way:
```sql
SELECT select_list1
FROM  table1
INTERSECT
SELECT select_list2
FROM table2
```

In order to apply the `INTERSECT` operator, we need to have the following:
- The **number** and **order** of columns in all queries must be the same.
- The data types must be **comparable**.

Suppose we created two data tables `t1` and `t2` and inserted data into both tables: 
```sql
CREATE TABLE table1(
    v1 INT
);

INSERT INTO table1(v1)
VALUES(1),(2),(3);

CREATE TABLE table2(
    v2 INT
);
INSERT INTO table2(v2)
VALUES(2),(3),(4);
```

Following the syntax at the beginning of this section, we have
```sql
SELECT v1
FROM table1
INTERSECT
SELECT v2
FROM table2;
```
which returns the following data table:
````
v1
--
2 
3 
````
## SQLite INTERSECT example

Suppose we want to find the customers who have invoices using the `customers` and `invoices` tables from our sample database. We can do this by typing the following query:
```sql
SELECT CustomerId
FROM customers
INTERSECT
SELECT CustomerId
FROM invoices
ORDER BY CustomerId;
```
which returns the following data table:
````
CustomerId
----------
1         
2         
3         
4         
5         
6         
7         
8         
9         
````
