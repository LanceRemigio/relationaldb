# SQL Lesson 12: Order of execution of a Query

## Basics
Now let us focus on creating a complete query given all the knowledge we have gathered so far. Consider the example query below:
```sql
SELECT DISTINCT column, AGG_FUNC(column_or_expression), 
FROM mytable
    JOIN another_table
    ON mytable.column = another_table.column
    WHERE contraint_expression
    GROUP BY column
    HAVING contraint_expression
    ORDER BY column ASC/DESC 
    LIMIT count OFFSET COUNT;
    ```

- Each query always begins with finding the data we want to analyze and filtering it so that it can be processed and understood. 
- Remember that the order of statements in the example query is executed from top to bottom.

## Order of Execution 
1. `FROM and JOINS` 
The `FROM` clause and the `JOIN` clause right after will be executed first to determine the total working set of data. This often includes subqueries which may cause temporary tables to be made, containing all the columns and rows of the tables being joined.


2. `WHERE`
Once the total working set of data is determined, the `WHERE` cause gets executed which then includes all the rows that meet the constraint and discards all the rows that do not satisfy the contraints. This filtering process can only access the columns specified in the first part of this process.  

3. `GROUP BY` 
The results from the step above are then grouped based on some column that is specified. The number of rows depends on the amount of unique values in that column. 




4. `HAVING` 
The results from the step above are then group based on some column that is specified. Afterwards, the constaints in the `HAVING` clause are then applied to the rows that are grouped, which subsequently discards the grouped rows that do not satisfy the constraint.  

**Keep in mind that aliases are not accessible by neither the HAVING clause nor the WHERE clause**

5. `SELECT`

Any expressions in the SELECT part of the query are finally computed.
6. `DISTINCT`

Of the remaining rows, rows with duplicate values in the column marked as DISTINCT will be discarded.
7. `ORDER BY`

If an order is specified by the ORDER BY clause, the rows are then sorted by the specified data in either ascending or descending order. Since all the expressions in the SELECT part of the query have been computed, you can reference aliases in this clause.

8. `LIMIT / OFFSET`

Finally, the rows that fall outside the range specified by the LIMIT and OFFSET are discarded, leaving the final set of rows to be returned from the query.


## Exercise

1. Find the number of movies each director has directed.

```sql
SELECT 
    Title,
    COUNT(Title) AS Num_of_Movies
    Director
FROM 
  Movies  
GROUP BY Director;
```

2. Find the total domestic and international sales that are attributed to each director.

```sql
SELECT 
    Director, 
    Title,
    SUM(Domestic_sales + International_sales) AS Total_Sales
FROM 
    Boxoffice
INNER JOIN
    Movies 
    ON Movies.Id = Boxoffice.Movie_id
GROUP BY 
    Director;
```

