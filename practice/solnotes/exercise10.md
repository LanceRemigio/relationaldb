# SQL Lesson 10: Queries with aggregates 
## Basics
We can use aggregate functions like the `MAX` function to answer questions like , "What is the highest grossing Pixar film each year?". Using function like `MAX` allow us to summarize information about a group of rows in a data table.

The syntax used to create a query with an aggregate function goes someting like:
```sql
SELECT AGG_FUNC(some_column) AS aggregate_description
FROM mytable
WHERE constraint_expression;
```

## Grouped aggregate functions

We can apply aggregate functions on groups of rows within a data table. This can be done by using the `GROUP BY` clause.

The basic syntax goes someting like:

````sql
SELECT AGG_FUNC(some_column) AS aggregate_description
FROM mytable
WHERE constraint_expression
GROUP BY column;
````

## Exercise


1. Find the longest time that an employee has been at the studio.

```sql
SELECT 
    Name, 
    Building,
    MAX(Years_employed) AS Max_year
FROM Employees
ORDER BY Max_year;
```
2. For each role, find the average number of years employed by employees in that role.


```sql
SELECT 
    Role,
    AVG(Years_employed) AS avg_year_employed
FROM Employees
GROUP BY role;
```


3. Find the total number of employee years worked in each building.


```sql
SELECT  
    SUM(Years_employed) AS total_years_employed, 
    Building
FROM Employees
GROUP BY Building;
```






