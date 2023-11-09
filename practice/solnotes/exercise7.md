# SQL Lesson 7: Outer Joins

The syntax for outer joins are the same as the syntax used to create inner joins between two tables.

1. Find the list of all buildings that have employees.
*For future Lance* don't think about this too hard.
```sql
SELECT DISTINCT
    building
FROM 
    employees;
```


2. Find the list of all buildings and their capacity.

```sql
SELECT 
    building_name,
    capacity
FROM Buildings;
```




3. List all buldings and the distinct employee roles in each building (including empty buildings).

```sql
SELECT DISTINCT
    Building_name,
    Role
FROM Buildings
LEFT JOIN Employees
    ON Buildings.Building_name = Employee.Building;
```
