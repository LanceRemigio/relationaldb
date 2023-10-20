# Having Clause


## Basics

The `HAVING` clause is used along side the `GROUP BY` clause to filter groups of rows based on a specified condition.

Note that the `HAVING` clause must be used after the `GROUP BY` clause or else an error will be returned:
````
Error: a GROUP BY clause is required before HAVING
````
Another observation worth noting is that the `HAVING` clause is used after the `GROUP BY` clause while the `WHERE` clause is applied before  the `GROUP BY` clause.

Applying the `HAVING` clause involves following the syntax below:

```sql
SELECT
	column_1, 
    column_2,
	aggregate_function (column_3)
FROM
	table
GROUP BY
	column_1,
    column_2
HAVING
	search_condition;
```

The `HAVING` clause evaluates the `search_condition` based on a boolean value.


## Examples

Suppose we wanted to return a data table with the number of tracks associated with a track id. We can do this by executing the query below:

```sql
SELECT
	albumid,
	COUNT(trackid)
FROM
	tracks
GROUP BY
	albumid;
```




Assume that we wanted to specify a condition where the `albumid = 1`. Then we would need to type the following query to do that:




```sql
SELECT
	albumid,
	COUNT(trackid)
FROM
	tracks
GROUP BY
	albumid
HAVING albumid = 1;
```

Which should return the following row:
````
AlbumId  COUNT(trackid)
-------  --------------
1        10            
````

Now suppose that we wanted to return a data table containing albums thta have between 18 and 20 tracks. We can use an aggregate function `COUNT()` to do this. Hence, we have the following statement:
```sql
SELECT
   albumid,
   COUNT(trackid)
FROM
   tracks
GROUP BY
   albumid
HAVING 
   COUNT(albumid) BETWEEN 18 AND 20
ORDER BY albumid;
```
which returns the following data table:
````

AlbumId  COUNT(trackid)
-------  --------------
21       18            
37       20            
54       20            
55       20            
72       18            
102      18            
115      20            
.       .
.       . 
.       .
````

## HAVING clause with INNER JOIN

Suppose we wanted to filter an inner join between two tables using a specified condition. Suppose we do this on the `tracks` and `albums` tables where we want to return the rows whose total length is greater than 60,000,000 milliseconds.

```sql
SELECT
	tracks.AlbumId,
	title,
	SUM(Milliseconds) AS length
FROM
	tracks
INNER JOIN albums ON albums.AlbumId = tracks.AlbumId
GROUP BY
	tracks.AlbumId 
HAVING
	length > 60000000;
```
This query returns the following data table:

````

AlbumId  Title                                     length  
-------  ----------------------------------------  --------
229      Lost, Season 3                            70665582
230      Lost, Season 1                            64854936
231      Lost, Season 2                            63289631
253      Battlestar Galactica (Classic), Season 1  70213784
````




