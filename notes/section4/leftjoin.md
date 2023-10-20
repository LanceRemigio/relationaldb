# Left Join


## Intro and basics 

Suppose we have two tables A and B. 
    - A contains m and f columns.
    - B contains n and f columns.

We can left join A and B by using the `LEFT JOIN` clause. We can do this by typing the following query:
````sql
SELECT 
    a,
    b
FROM
    A
LEFT JOIN B ON  A.f = B.f
WHERE search_condition;
````

This returns a table of all the rows of in table A that match with rows in table B. In addtiion, all the rows of A are included regardless if they make a match with rows in table B. In this case, some rows will be returned with NULL values.

## Examples

Suppose we want to look at the artists who do have any albums first. We can do this by either 
    - Using the `ORDER BY` clause to list the rows that contains NULL values first. 
    - OR using the `WHERE` clause and `IS NULL` operator to only list the artists who do have any albums  

We can do the former by typing the following query:
````sql
SELECT
   artists.ArtistId, 
   AlbumId
FROM
   artists
LEFT JOIN albums ON
   albums.ArtistId = artists.ArtistId
ORDER BY
   AlbumId;
````

Likewise, the latter leads to the following query:
````sql
SELECT
   artists.ArtistId
   , AlbumId
FROM
   artists
LEFT JOIN albums ON
   albums.ArtistId = artists.ArtistId
WHERE
   AlbumId IS NULL;
````


