# SQL Lesson 15: Deleting Rows
## Basics
The `DELETE` statement deletes rows by specifying the table and the rows to delete based on some condition specified in the `WHERE` clause.

If a `WHERE` constraint is not specified then the `DELETE` statement will delete all the rows in the table.

A query with the `DELETE` statement looks something like:

```sql
DELETE FROM mytable
WHERE some_condition;
```

Treat the `DELETE` statement just like the `UPDATE` statement; that is, run a `SELECT` statement first to confirm you the right rows and then run the `DELETE` statement.



## Exercise

1. This database is getting too big, lets remove all movies that were released **before** 2005. 
```sql
DELETE FROM Movies
WHERE Year < 2005
```

2. Andrew Stanton has also left the studio, so please remove all movies directed by him.

```sql
DELETE FROM Movies
WHERE Director = 'Andrew Stanton'
```
