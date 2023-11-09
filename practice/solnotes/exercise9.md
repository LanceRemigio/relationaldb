# SQL Lesson 9: Queries with Expressions
## Basics
- We can leverage the complex logic that comes with expressions to create more sophisticated querying data from a table.

An example of a query using expressions mentioned above is the following:
````python
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data 
WHERE ABS(particle_position) * 10.0 > 500;
````

This finds all the rows in the `particle_speed` column from the `physics_data` table and divides them in half and labels this new data as `half_particle_speed` if and only if the absolute value of the particle position mutiplied by 10.0 is greater than 500. 


- Although very helpful in selecting particular data, the use of expressions can also make the query harder to read.
- It is recommended that expressions be used in the `SELECT` part of the query along with an *alias* using the `AS` keyword; that is, we should have
````python
SELECT col_expression AS expr_description, ...
FROM mytable;

````
## Exercise

You are going to have to use expressions to transform the `BoxOffice` data into something easier to understand for the task below.

1. List all movies and their combined sales in **millions** of dollars.


```sql
SELECT 
    Title,
    (Domestic_sales + International_sales) / 1000000 AS Combined_sales,
FROM 
    Movies
INNER JOIN Boxoffice
ON Boxoffice.Movie_id = Movies.Id 
```





2. List all the movies and their ratings **in percent**.

```sql
SELECT 
    Title, 
    Rating * 10 AS Percent_ratings
FROM 
    Movies
INNER JOIN Boxoffice
    ON Movies.Id = Boxoffice.Movie_id
```





3. List all movies that were released on even number years. 

```sql
SELECT 
    Title, 
    Year
FROM 
    Movies
INNER JOIN BoxOffice
    ON Movies.Id = Boxoffice.Movie_id
WHERE Year % 2 = 0 
    ```



