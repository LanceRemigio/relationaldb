# LIKE operator

Sometimes we can pattern match certain data from a table using the `LIKE` operator. Say, we are trying to do this based on partial information. We can just type `LIKE` in the `WHERE` clause of the `SELECT` statement as follows:
````sql
SELECT
	column_list
FROM
	table_name
WHERE
	column_1 LIKE pattern;
````
In addtion to using  `SELECT` statement we can use the `LIKE` operator on other statements such as `DELETE` and `UPDATE`. We can use wildcards to pattern match. These are the percent sign `%` and the underscore `_`

- `%` -> matches any sequences of zero or more characters
- `_` -> matches any single character

## Examples

### Matching based on a sequence of zero or more characters

- Suppose we want to match any string that starts with an `s`. Then we would just use the first wildcard `%` and type `s%`.
- The `%er` pattern matches any string that ends with `er` like `peter`, `clever`, etc.
- The `%per%` pattern matches any string that contains `per` such as `percent` and `peeper`.

### Pattern matching based on a single character

- Strings that have a pattern of `h_nt` matches  `hunt`, `hint`, etc. 
- The `__pple` pattern matches the following words `topple`, `supple`, and `tipple`, etc.

Note that the `LIKE` operator is case-insensitive for characters within the ASCII range. Otherwise, it is case sensitive. However, if we want to make the `LIKE` operator case-sensitive then we would just need to put
````sql
PRAGMA case_sensitive_like = true;
````


## LIKE examples

Using the `tracks` table from our database, we can grab the columns and rows that contain the `Wild` string by using the `%` wildcard.
````sql
SELECT
	trackid,
	name	
FROM
	tracks
WHERE
	name LIKE 'Wild%'

````
The query above finds all names of the songs with the starting with string `Wild`. 

Suppose we want to find all the rows whose name contains the string `Wild`. Then we would just need to type

````sql
SELECT
	trackid,
	name	
FROM
	tracks
WHERE
	name LIKE '%Wild%'
````
What about anything that comes before `Wild`. Then would just need to put
````sql

SELECT
	trackid,
	name	
FROM
	tracks
WHERE
	name LIKE '%Wild'
````

We can pattern match using a mixture of `%` and `_` wilcards as well.

An example of this is the following:

````sql
SELECT
	trackid,
	name
FROM
	tracks
WHERE
	name LIKE '%Br_wn%';
````

which selects all the name rows with the the string `Br_wn`.

## SQLite LIKE with ESCAPE clause

If the pattern matching involves having `%` and `_` as literal strings, then we can just use the `ESCAPE` clause to have SQLite recognize that character as a string instead of a wildcard.
 
We can do this by typing the following syntax:
````sql
column_1 LIKE pattern ESCAPE expression;
````
SQlite will evaluate the expression that comes after the `ESCAPE` clause which consists of a single character or an escape clause. An example, can be the following
````sql
column_1 LIKE '%10\%%' ESCAPE '\';
````
In this case, this part of a query will pattern match any string with `10%` in it, interpreting the percent signs at each end of the pattern as a wildcard, but the 2nd one as a literal string.
