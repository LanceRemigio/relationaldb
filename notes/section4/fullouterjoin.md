# Full Outer Join 

The following query emulates the `FULL OUTER JOIN` clause in SQLite: 
````sql
SELECT d.type, 
    d.color,
    c.type,
    c.color
FROM dogs d 
LEFT JOIN cats c USING(color)
UNION ALL
SELECT d.type, 
    d.color,
    c.type,
    c.color
FROM cats c 
LEFT JOIN dogs d USING (color)
WHERE d.color IS NULL;
````
Explanation of query:
    - Since the outer join and right joins are not supported by sqlite, we can use the left join clause two times but switching the positions of the table in the two select statements shown above.
    - We also include the `WHERE` clause and `IS NULL` clause to prevent any rows from being duplicated in the resulting set.

The output should result in the following table:
````
type     color  type     color
-------  -----  -------  -----
Hunting  Black  Outdoor  Black
Guard    Brown                
                Indoor   White
````

Since this is a `FULL OUTER JOIN`, we have a result set that returns both columns that have matching values and NULL VALUES if there no matching values found. 
