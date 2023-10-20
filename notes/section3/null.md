
## IS NULL

- `NULL` is a special term to describe missing information or information that is not applicable. This describes situations when we don't know who the songwriter is for some songs.

- NULL is not equal to itself because we cannot compare two ambiguous data together. Hence, the expression `NULL = NULL` is always false.


## Examples

The following is an invalid way to find tracks whose composers are NULL.

````sql
SELECT
    Name, 
    Composer
FROM
    tracks
WHERE
    Composer = NULL;
````

The issue with this query lies in the expression found after the `WHERE` clause. We cannot compare a value `Composer` to `NULL` because `NULL` cannot compare two ambiguous values much less itself.

The syntax for using `IS NULL` is done as follows:
````sql
{column | expression } IS NULL;
````

We can use the `IS NULL` operator instead. We can do this in the following query
````sql
SELECT  
    Name,
    Composer
FROM 
    tracks
WHERE
    Composer IS NULL
ORDER BY
    Name;
````

## IS NOT NULL 

The syntax for the `IS NOT` operator is shown below:

````sql
expression | column IS NOT NULL 
````

We can use this on the `tracks` table from our sample database:

````sql
SELECT
    Name, 
    Composer
FROM
    tracks
WHERE
    Composer IS NOT NULL
ORDER BY
    Name;
````

This returns all the rows that do not contain a NULL value.
