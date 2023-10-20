
1. List all the **Canadian** cities and their populations.

```sql
SELECT 
   City,
   Country, 
   Population
FROM 
    north_american_cities
WHERE Country = "Canada"
```

which returns the following table:

````
city	    country	population
Toronto	    Canada	2795060
Montreal	Canada	1717767
````

2. Order all the cities in the United States by their latitude from north to south.

To order all the cities in the United States by latitude from north to south, we have to order the cities column in a descending order because north means positive and south means negative.


```sql
SELECT
    City,
    Country,
    Latitude
FROM 
    north_american_cities
WHERE Country = "United States"
ORDER BY Latitude DESC

```

3. List all the cities west of Chicago, ordered from west to east.

Remeber positive longitudes correspond to the **eastern** hemisphere while negative longitudes correspond to the **western** hemisphere.

It's a good idea to list out every city in the US first using the following query:

```sql
SELECT 
    City,
    Country,
    Longitude
FROM 
    north_american_cities
WHERE Country = "United States"
```

```sql
SELECT
    City,
    Country,
    Longitude
FROM 
    north_american_cities
WHERE Country = "United States" AND  Longitude < -87.629798 
ORDER BY Longitude ASC;
```
3. List the two largest cities in Mexico (by population).

```sql

SELECT
    City,
    Country,
    Population
FROM 
    north_american_cities
WHERE Country = "Mexico"
ORDER BY Population DESC
LIMIT 2;

```

````
City	        Country	Population
Mexico City	    Mexico	        8555500
Ecatepec de Morelos	Mexico	1742000
````

5. List the third and fourth largest cities (by population) in the United States and their population.

```sql
SELECT 
    Country, 
    City, 
    Population
FROM 
    north_american_cities
WHERE Country = "United States"
ORDER BY Population DESC
LIMIT 2 OFFSET 2;
```
which returns the following result:
````
country	        city	population
United States	Chicago	2718782
United States	Houston	2195914
````
