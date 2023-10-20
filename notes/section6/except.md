# Except 

## Basics

The `EXCEPT` operator compares the result sets of two queries and returns the distinct rows from the left query that are not outputs of the right query.

The following shows the basic syntax needed in order to use the `EXCEPT` operator correctly.

```sql
SELECT select_list1
FROM table1
EXCEPT
SELECT select_list2
FROM table2
```
Returns distinct rows of `table1` that are not found in `table2`. The quert above must adhere to the following rules:
    - The number of columns of both tables found in both queries  must be the same.
    - The order of the columns and their types must be comparable.

Say, for demonstration that we wanted to create two tables `t1` and `t2` and insert some data into both tables:
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
We can use the `EXCEPT` operator to compare and filter out the result sets of the two queries:
```sql
SELECT v1
FROM t1
EXCEPT 
SELECT v2
FROM t2;
```

which should just return the row `1`.


## Examples

We will use the `artists` and `albums` tables from our sample database for demonstration.

Suppose we wanted to find the artist ids of artists who do not have any albums under the `albums` table:
```sql
SELECT ArtistId
FROM artists
EXCEPT 
SELECT ArtistId
FROM albums;
```
We have the following output:

````

ArtistId
--------
25      
26      
28      
29      
30      
31      
32      
33      
34      
35      
````


