# SQLite Glob

The `GLOB` operator determines whether a string matches a specific pattern (just like the `LIKE` operator). Except this time, the `GLOB` operator is case-sensitive and uses the UNIX wildcards (i.e the `*` and `?` operators).

- The `*` operator matches any number of characters and the `?` operator matches exactly one character. 

- We can pass list of letters, characters, or numbers into a list and the `GLOB` will match any one that belongs to that list.
    - Example:
        ````sql
        SELECT
            trackid,
            name
        FROM
            tracks
        WHERE
            name GLOB '*[^1-9]*';
        ````
        This query filters strings that have do not have any numbers belonging to the list specified above.
- We can also pass in a series of letters and numbers all together like `[a-zA-Z0-9]`. This list matches any number or character found in the list. 

## Matching with Everything after Man

````sql
SELECT
	trackid,
	name
FROM
	tracks
WHERE
	name GLOB 'Man*';
````

## Matching strings with anything before Man

````sql
SELECT
	trackid,
	name
FROM
	tracks
WHERE
	name GLOB '*Man';
````


## More Examples

````sql
SELECT
	trackid,
	name
FROM
	tracks
WHERE
	name GLOB '*[1-9]*';
````

This selects tracks that contain numbers that are placed between two strings (including whitespace).


````sql
SELECT
	trackid,
	name
FROM
	tracks
WHERE
	name GLOB '*[^1-9]*';
````

````sql
SELECT
	trackid,
	name
FROM
	tracks
WHERE
	name GLOB '*[1-9]';
````
