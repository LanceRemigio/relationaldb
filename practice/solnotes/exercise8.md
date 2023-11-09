# SQL Lesson 8: A short note on NULLS


- Sometimes we have rows of values in our data tables that aren't filled in yet.
- We fill these values in using `NULL` values until they are actually filled in later.
- `NULL` values also help with preventing future analyses from being skewed (for example: taking averages of numerical data).

The basic syntax for using the `IS NULL` or `IS NOT NULL` is to add 

```sql
SELECT column, another_column, …
FROM mytable
WHERE column IS/IS NOT NULL
AND/OR another_condition
AND/OR …;
```

Suppose we use the same table from the last exercise but this time we added a few more employees but haven't assign them to any building.

1. Find the name and role of all employees who have not been assigned to a building.

```sql
SELECT
    Name, 
    Role,
    Building
FROM Employees
WHERE Building IS NULL;
```

2. Find the names of the buildings that hold no employees.

```sql
SELECT 
    Building_name
FROM Buildings
LEFT JOIN Employees
    ON Buildings.building_name = Employees.Building
WHERE Building IS NULL;
    
```

