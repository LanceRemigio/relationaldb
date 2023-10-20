# SQL Lesson 4: Filtering and sorting query results

## Exercise 4 


1. List all directors of Pixar movies (alphabetically), without duplicates.


To list all the directors of Pixar movies alphabetically without duplicates, we need to type the following:
```sql
SELECT DISTINCT
    Director
FROM 
    movies
ORDER BY 
    Director ASC;
```

which will return the following result:
````
Director:
Andrew Stanton
Brad Bird
Brenda Chapman
Dan Scanlon
John Lasseter
Lee Unkrich
Pete Docter
````
2. List the last four Pixar movies released (ordered from most recent to least).

There are a couple of ways to do this:

We can use a combination of the `LIMIT` and `ORDER BY`  to filter the movies in the following way
```sql
SELECT 
    Title, 
    Year
FROM 
    movies
ORDER BY Year DESC
LIMIT 4 
```

OR we can use the `WHERE` clause and specify a range of values the `YEAR` has to meet:

```sql
SELECT 
    Title,
    Year
FROM 
    movies
WHERE Year >= 2010 AND Year <= 2013
ORDER BY Year DESC
```

Both of these queries result in the following table:

````
Title	            Year
Monsters University	2013
Brave	            2012
Cars 2	            2011
Toy Story 3	        2010
````

3. List the **first** five Pixar movies sorted alphabetically.

```sql
SELECT 
    Title
FROM 
    movies
ORDER BY
    Title ASC
LIMIT 5
```
which filters the `Movies` table to the following result:
````
Title
A Bug's Life
Brave
Cars
Cars 2
Finding Nemo
````

4. List the **next** five Pixar movies sorted alphabetically.

````sql
SELECT 
    Title
FROM 
    movies
ORDER BY
    Title ASC
LIMIT 5 OFFSET 5
````

