# Cross Join

We can combine two or more result sets from multiplie tables using the `CROSS JOIN` method.

Suppose tables A and B have dimensions n and m respectively. When we form a `CROSS JOIN` between the two tables A and B, we create a cartesian product linking every value in each row in A and connecting it to B. The number of rows in the result of a cross join is the product of the dimensions of each table; that is, `n x m` in our case. If we add one more table say table C with dimension k, then the number of rows in the result set could be an obscenely large number.     


