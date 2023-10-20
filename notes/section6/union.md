# Union

The `union` operator is used to combine result sets of two or more queries into a single result set.

## Basics

The basic syntax of the `UNION` operator goes something like this:
```sql
query_1 
UNION [ALL]
query_2 
UNION [ALL]
query_3
...;
```
Both the `UNION` and `UNION ALL` operators combine the rows from two or more queries into a single result set. The `UNION` also removes any duplicate rows while the `UNION ALL` does not.  

Because of this, it is often faster to use the `UNION` operator.

The following are rules to using these operators:
    - The number of columns in all queries must be the same.
    - The corresponding columns of each result set must contain compatible data types.
    - The column names of the first query determine the column names of the combined result set.
    - The `GROUP BY` and `HAVING` clauses are applied to each individual query, not the final result set.
    - The `ORDER BY` clause is applied to the combine result set, not within the individual result set.

### Key Differences between UNION and JOIN

- The `JOIN` clause combines *columns* from multiple related tables.
- The `UNION` cobines *rows* from multiple related tables.

### Example

Suppose we made a query that created the following two tables:

```sql
CREATE TABLE t1(
    v1 INT
);
 
INSERT INTO t1(v1)
VALUES(1),(2),(3);
 
CREATE TABLE t2(
    v2 INT
);
INSERT INTO t2(v2)
VALUES(2),(3),(4);
```
and suppose we unioned the result sets from both queries into one resulting set using the following:

```sql
SELECT v1
  FROM t1
UNION
SELECT v2
  FROM t2;
```

which generates the following output
````
v1
--
1 
2 
3 
4 
````
where the first table `t1` contained values `1,2,3` and the second table `t2` contained values `2,3,4`. Keep in mind, these values are associated with a distinct row and are combined together in the resulting set. Observe that the name of the column of the resulting set is also the same name as the column in `t1`.


## Examples From Sample Database

The query below uses the `UNION` operator to combine names of employees and customers into a single list:
```sql
SELECT FirstName, LastName, 'Employee' AS Type
FROM employees
UNION
SELECT FirstName, LastName, 'Customer'
FROM customers;
```

which returns the following output:
````
FirstName  LastName      Type    
---------  ------------  --------
Aaron      Mitchell      Customer
Alexandre  Rocha         Customer
Andrew     Adams         Employee
Astrid     Gruber        Customer
Bjørn      Hansen        Customer
Camille    Bernard       Customer
Daan       Peeters       Customer
Dan        Miller        Customer
````

The next query adds on to the previous one by ordering the resulting set in terms of the columns `FirstName` and `Lastname`.
```sql
SELECT FirstName, LastName, 'Employee' AS Type
FROM employees
UNION
SELECT FirstName, LastName, 'Customer'
FROM customers
ORDER BY FirstName, LastName;
```
which return the following output:
````
FirstName  LastName      Type    
---------  ------------  --------
Aaron      Mitchell      Customer
Alexandre  Rocha         Customer
Andrew     Adams         Employee
Astrid     Gruber        Customer
Bjørn      Hansen        Customer
Camille    Bernard       Customer
Daan       Peeters       Customer
Dan        Miller        Customer
Diego      Gutiérrez     Customer
Dominique  Lefebvre      Customer
Eduardo    Martins       Customer
Edward     Francis       Customer

````



