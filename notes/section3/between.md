# The BETWEEN Operator


The `BETWEEN` operator can be used in the `WHERE` clause of the `SELECT`, `DELETE`, `UPDATE`, and `REPLACE` statements. The `BETWEEN` operator is typically paired with the `AND` and the `OR` logical operators.

The basic syntax of using this operator is illustrated below:
````sql
test_expression BETWEEN low_expression AND high_expression
````
Note that the `BETWEEN` operator is inclusive. This means that we can have the `test_expression` can be greater than or equal to the `low_expression` and less than or equal to the `high_expression`; that is, we have
````sql
test_expression >= low_expression AND test_expression <= high_expression
````
We can specify an exclusive range by adding replacing the inequalities above with `<` and `>` along with using the logical operator `OR` instead of `AND`. 

We can also negate the result of the `BETWEEN` operator by typing the following:
````sql
test_expression NOT BETWEEN low_expression AND high_expression
````
The statment above is equivalent to 
````sql
test_expression < low_expression OR test_expression > high_expression
````
# Examples

In the upcoming set of examples, we will use the `invoices` table from our sample database.

## Using BETWEEN

Suppose we want to get the invoices whose total is between 14.96 and 18.86 with the following query:
````sql
SELECT
    InvoiceId,
    BillingAddress,
    Total
FROM
    invoices
WHERE
    Total BETWEEN 14.91 and 18.86    
ORDER BY
    Total; 
````

## NOT BETWEEN  

What if negate the expression above, then we would just need to make slight modification to our query above by typing
````sql
SELECT
    InvoiceId,
    BillingAddress,
    Total
FROM
    invoices
WHERE
    Total NOT BETWEEN 14.91 and 18.86    
ORDER BY
    Total; 
````
which will return the rows with values that are greater than 18.86 OR smaller than 14.91 with both exclusive.

## BETWEEN dates

What if we want to invoices between two dates? Then we would just need to type the following query to do that:
````sql
SELECT 
    InvoiceId,
    BillingAddress,
    InvoiceDate,
    Total
FROM
    invoices
WHERE
    InvoiceDate BETWEEN '2010-01-01' AND '2010-01-31'
ORDER BY
    InvoiceDate;    
````
## NOT BETWEEN dates

Again, we can find out which invoices were taken that is outside of the set dates specified dates above (either greater than the high_expression or lower than the low_expression). Then we would just need to type the following:
````sql
SELECT 
    InvoiceId,
    BillingAddress,
    InvoiceDate,
    Total
FROM
    invoices
WHERE
    InvoiceDate NOT BETWEEN '2010-01-01' AND '2010-01-31'
ORDER BY
    InvoiceDate;    
````
