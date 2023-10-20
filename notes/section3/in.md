# IN

The main use case for the `IN` operator is to check whether a test value matches any value in a list of values or a result of a subquery.

## Syntax 

````sql
expression [NOT] IN (value_list|subquery);
````
The expression part can be any column from a table.

The list of values can be either a fixed value list or a result from a column by a subquery. Note that the return type of both the expression and the list of values must be the same.

The `IN` operator returns either a true or false depending on the test expression meets the conditions specified or matches the value in a list of values or not. We can negate the `IN` operator by using `NOT IN` operator.





