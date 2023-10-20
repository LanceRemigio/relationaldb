# Inner Join

In a relational database, we often have data that is distributed in related tables. These tables are linked together via foreign keys. We can query data from these tables by using the `INNER JOIN` clause. The function of this clause is to combine columns from the associated tables.   

Suppose we have two tables A and B. If A has columns `a1` and `a2`  and B has columns `b1` and `b2`where they both share the foreign key `f` , then we can use the inner join clause to write the following syntax: 
````sql
SELECT a1, a2, b1, b2
FROM A 
INNER JOIN B on B.f = A.f
````

The `INNER JOIN` clause does a comparison with each row of each table and checks if the foreign keys are equivalent. For every row that contains a match foreign key, that row gets added to the resulting table. When we do this, we will have rows `(a1,1)` and `(a3, 3)` be equivalent to the rows in the B table `(b1,1)` and `(b2,3)`. We can think of the `INNER JOIN` clause as the famous intersection in math.      

## Examples

Suppose we take the `tracks` table and the `albums` table. We know that these tables are linked together via the `AlbumId` column. 

Note that in the `tracks` table, the `AlbumId` column is a foreign key. We can query from both tables, using the following query: 
````sql
SELECT
	trackid,
	name,
	title
FROM
	tracks
INNER JOIN albums ON albums.albumid = tracks.albumid;
````

For every row, SQLite compares each value found in the `albumid` column of the `tracks` table with the values found in the `albums` table. If they are equivalent, then SQLite combines data of rows in both tables in the resulting set. We can be more specific by including the `AlbumId` columns from both tables after the `SELECT` clause by typing the following query:
````sql
SELECT
    trackid,
    name,
    tracks.albumid AS album_id_tracks,
    albums.albumid AS album_id_albums,
    title
FROM
    tracks
INNER JOIN albums ON albums.albumid = tracks.albumid;
````

## Using multiple inner joins 

Suppose we wanted to query from three tables and suppose we added the `artists` table. We know that the `tracks`  and `albums` tables are linked via the `AlbumId` keys. What about the `artists` table? We can see that both the `albums` and `artists` tables are both linked via the `ArtistId` keys. Now we have the proper info to query all three tables. What we need is two inner joins to do this. To query the data from all three tables, we can type the following:
````sql
SELECT
    trackid,
    tracks.name AS track,
    albums.title AS album,
    artists.name AS artist
FROM
    tracks
    INNER JOIN albums ON albums.albumid = tracks.albumid
    INNER JOIN artists ON artists.artistid = albums.artistid;
````








