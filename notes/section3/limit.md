# Limit

- LIMIT
- 


## The LIMIT clause
The `LIMIT` clause contrains the number of rows returned by a query.

For example, we can contrain the amount of rows in our 1 million plus rows database by adding the the `LIMIT` clause to the `SELECT` statement to return 10 rows.

Observe the following syntax below:
````sql
SELECT 
    column_list
FROM    
    table
LIMIT row_count;

````
where the `row_count` specifies the number of rows you want to return. We can use our example database to return the first 10 rows of our `tracks` table.
````sql
SELECT
    trackID, 
    name
FROM
    tracks
LIMIT 10;
````

Say we want to get the first 10 rows starting from the 11th row in the `tracks` table. We can use the following statement:
````sql
SELECT
	trackId,
	name
FROM
	tracks
LIMIT 10 OFFSET 10;
````
## SQLITE LIMIT and ORDERY BY clause

Using the `LIMIT` clause with the `ORDER BY` clause is a good way to get the number of rows you want in a specified order. Note that the `ORDER BY` clause always comes before the`LIMIT` clause. This makes sense because SQLite has to filter the rows the user wants in order to start limiting the amount of rows depending on the situation. The syntax of our query should look like the following statement:
````sql
SELECT
   column_list
FROM
   table
ORDER BY column_1
LIMIT row_count;
````
Suppose we want to grab the top 10 biggest tracks by size so we use the following query:
````sql
SELECT
	trackid,
	name,
	bytes
FROM
	tracks
ORDER BY
	bytes DESC 
LIMIT 10;
````
The `DESC` statement indicates that we want to return the rows from greatest to least.

What if we want the 5 shortest tracks? We would need to sort the tracks via the milliseconds column using the `ORDER BY` clause and get the first 5 rows using the `LIMIT` clause.

````sql
SELECT
	trackid,
	name,
	milliseconds
FROM
	tracks
ORDER BY
	milliseconds ASC
LIMIT 5;
````
## Getting the nth highest and the lowest value

- To get the nth highest value rows, we need to use the `ORDER BY` statement in descending order.
- The nth lowest value rows can be gathered by using the `ORDER BY` clause but in ascending order.
- We can use the `LIMIT OFFSET` statement to the nth highest or nth lowest row.

The following statement returns the second-longest track in the `tracks` table.

````sql
SELECT
	trackid,
	name,
	milliseconds
FROM
	tracks
ORDER BY
	milliseconds DESC
LIMIT 1 OFFSET 1;
````
If we want the third-longest track, then we would need to have the following query:
````sql
SELECT
	trackid,
	name,
	milliseconds
FROM
	tracks
ORDER BY
	milliseconds DESC 
LIMIT 1 OFFSET 2;
````

