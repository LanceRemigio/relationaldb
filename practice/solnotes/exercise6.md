# SQL Lesson 6: Multi-table queries with JOINS

1. Find the domestic and international sales for each movie.

```sql
SELECT 
    Title,
    Domestic_sales, 
    International_sales
FROM 
    Movies
INNER JOIN Boxoffice
    ON Movies.id = Boxoffice.Movie_id
```

2. Show the sales numbers for each movie that did better internationally rather than domestically.

```sql
SELECT 
    Title,
    Domestic_sales,
    International_sales
FROM
    Movies
INNER JOIN Boxoffice
    ON Movies.id = Boxoffice.Movie_id
WHERE International_sales > Domestic_sales;
```
3. List all the movies by their ratings in descending order. 

```sql
SELECT 
    Title,
    Rating
FROM 
    Movies
INNER JOIN Boxoffice
    ON Movies.id = Boxoffice.Movie_id
ORDER BY Rating DESC;
```





