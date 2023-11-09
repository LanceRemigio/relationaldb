# SQL Lesson 11: Queries with aggregates (pt.2)

## Basics

- Notice that the `GROUP BY` clause is always exected after the `WHERE` clause (this filters rows about to be grouped).
- We can further filter our rows using the `HAVING` clause.
- The syntax for using the `HAVING` clause goes something like:

````sql
SELECT 
    group_by_column, 
    AGG_FUNC(column_expression) AS aggregate_result_alias, ...
FROM
    mytable
WHERE condition 
GROUP BY column
HAVING group_condition;
````

- The `HAVING` clause is used the same way as the `WHERE` condition. 
- Both keywords are applied to the grouped rows.

## Exercise

For this exercise, you are going to dive deeper into **Employee** data at the film studio. Think about the different clause you want to apply for each task.

1. Find the number of Artists in the stuio (without a `HAVING` clause). 


```sql
SELECT
    Role,
    COUNT(Role) as Number_of_Roles
FROM  
    Employees
WHERE Role = "Artist"
GROUP BY Role
    
```

2. Find the number of Employees of each role in the studio.

```sql
SELECT
    Role,
    COUNT(Role) as Number_of_Roles
FROM  
    Employees
GROUP BY Role
```

3. Finf the total number of years employed by all Engineers.

```sql
SELECT 
    Role, 
    SUM(Years_employed) as total_years_employed
FROM 
    Employees
WHERE Role = 'Engineer';
```


