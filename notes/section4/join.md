# Join

Suppose we look at the `artists` and `albums` tables from our sample database.

Note that an artist can have zero or many albums while an album belongs to only one artist. Our goal is to query data from both tables at the same time. We can do this by using the `INNER JOIN`, `LEFT JOIN`, or `CROSS JOIN` clause. These clauses tell SQLite to match rows from one table in another table. 


## SQLite INNER JOIN

We can return the album titiles and their artist names by using the following query:
````sql
SELECT
    Title,
    Name, 
FROM 
    albums
INNER JOIN artists
    ON artists.ArtistId = albums.ArtistID;
ORDER BY Name
````
The `INNER JOIN` clause matches each row from the `albums` table with every row from the `artists` table based on the join condition `artists.ArtistId = albums.ArtistID` specified after the `ON` keyword. We can shorten the query by using the `USING` syntax as follows:
````sql
SELECT
   Title, 
   Name
FROM
   albums
INNER JOIN artists USING(ArtistId);
ORDER BY Name;
````

## LEFT JOIN    

The query below selects artist names and album titles from the `artists` and `albums` tables using the `LEFT JOIN` clause: 
````sql
SELECT 
    Name, 
    Title
FROM 
    artists
LEFT JOIN albums ON
    artists.ArtistId = albums.ArtistId
ORDER BY Name;
````

- The `LEFT JOIN` clause selects data starting from the left table `artists` and matching rows in the right table `albums` based on the condition `artists.ArtistId = albums.ArtistId`. 

- The left join returns all rows from the `artists` table regardless of whether or not rows match with the albums table. If there are no matches with the right table, then SQLite returns the table as if we queried the `artists` table by itself.

- We can shorten our query by using the `USING` syntax for the join condition as follows:

````sql
SELECT 
    Name, 
    Title
FROM 
    artists
LEFT JOIN albums USING (ArtistId)
ORDER BY
    Name;
````
If we want to return all the artists who don't have any albums then we can just add the `WHERE` clause in addition to `IS NULL` as follows


````sql
SELECT 
    Name, 
    Title
FROM 
    artists
LEFT JOIN albums USING (ArtistId)
WHERE Title IS NULL
ORDER BY
    Name;
````

Note that the `LEFT JOIN` and the `LEFT OUTER JOIN` are the equivalent in different versions of sql. 

## CROSS JOIN

Forms a cartesian product with with columns from a table with another table. This is different from the `INNER JOIN` and `LEFT JOIN` in that we don't need to specify a condition. We just type the following: 
````sql
SELECT *
FROM table1
CROSS JOIN table2;
````








