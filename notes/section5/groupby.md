# GROUP BY

The purpose of the `GROUP BY` clause is to group rows by one or more columns.


The usual syntax for using the `GROUP BY` clause can be done in the following way:
```sql
SELECT 
    column_1,
    aggregate_function(column_2)
FROM 
    table
GROUP BY
    column_1,
    column_2;
```

If there is a `WHERE` clause included, then the `GROUP BY` clause must come after it.


## Using an aggregate function example

Suppose we use our sample database and grab the following columns 
```sql
SELECT 
    albumid,
    COUNT(trackid)
FROM 
    tracks
GROUP BY
    albumid;
```
This query returns two columns with one of them storing the `Albumid` and the other storing the number of tracks associated with each album.

````
AlbumId  COUNT(trackid)
-------  --------------
1        10            
2        1             
3        3             
4        8             
5        15            
6        13            
7        12            
8        14            
9        8             
10       14            
````

We can go ahead and organize this result via the `ORDER BY` clause. We order in a descending order (greatest to least).
```sql
SELECT 
    albumid,
    COUNT(trackid)
FROM 
    tracks
GROUP BY
    albumid
ORDER BY COUNT(trackid) DESC;
```

## SQLite GROUP BY and INNER JOIN clause

We can use the `INNER JOIN` clause in addition to the `GROUP BY` clause to group rows into summary rows.

For example, we can join two tables, `tracks` and `albums`, to return the album's titles and number of tracks per album using the `COUNT` function. 

This can be done in the following way:

```sql
SELECT 
    tracks.albumid,
    title,
    COUNT(trackid)
FROM 
    tracks
INNER JOIN albums ON albums.albumid = tracks.albumid
GROUP BY
    tracks.albumid;
```

## Using the GROUP BY clause with HAVING

Suppose we wanted the group the rows according to which albums have more than 15 tracks. This can be done using the following statement:
```sql
SELECT 
    tracks.albumid,
    title,
    COUNT(trackid)
FROM     
    tracks
INNER JOIN albums ON albums.albumid = tracks.albumid
GROUP BY
    tracks.albumid
HAVING COUNT(trackid) > 15;
```
## GROUP BY clause with SUM 

We can also calculate the total length and bytes of each album in our tracks table.

This can be observed in the following query:

```sql
SELECT 
    albumid,
    SUM(milliseconds) AS  length, 
    SUM(bytes) AS  size
FROM 
    tracks
GROUP BY
    albumid;
```
## GROUP BY with MAX,MIN, and AVG functions

Another way we can query data from the `tracks` table is to grab the album id, album title, max length, min length, and avg length of tracks. This can be done using the quert below:

```sql
SELECT 
    tracks.albumid,
    title,
    MIN(milliseconds),
    MAX(milliseconds),
    round(avg(milliseconds), 2)
FROM 
    tracks
INNER JOIN albums ON albums.albumid = tracks.albumid 
GROUP BY 
    tracks.albumid;
```
We are grabbing the column `albumid` and grouping our rows based (all by `albumid`) on the shortest song (in milliseconds) and the longest song in each album as well as the average length of each song.  

## Grouping by multiple columns

Suppose we group the rows in our `tracks` table according to media type and genre:
```sql
SELECT
    MediaTypeId,
    GenreId,
    COUNT(TrackId)
FROM
    tracks
GROUP BY
    MediaTypeId,
    GenreId;
```
## Using the GROUP BY to grab the date 

Suppose we want to return a data table with the total number of invoices by years.

```sql
SELECT 
    STRFTIME('%Y', InvoiceDate) InvoiceYear,
    COUNT(InvoiceID) InvoiceCount
FROM 
    invoices
GROUP BY
    STRFTIME('%Y', InvoiceDate)
ORDER BY
    InvoiceYear;
```


