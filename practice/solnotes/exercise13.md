# SQL Lesson 13: Inserting Rows


## What is a Schema?

- Recall that a table is just a two-dimensional data set that contains rows and columns with thr columns containing the properties and the rows containing the values. 

- The *database schema* describes the structure of the table as well as the datatypes each column contains.

- For example, the **Movies** table contains the column **Year** which contains values that have a type integer whereas the values of the **Title** column are type strings.

## Inserting New Data

We can insert data by using the `INSERT` statement. The `INSERT` statement does three things. It 
- declares which table to write into.
- specfies the columns of data that we are filling. 
- one or more rows of data to insert.

```sql
INSERT INTO mytable
VALUES (value_or_expr, another_value_or_expr, /*... */) , /* first row */
(value_or_expr_2, another_value_or_expr_2, /*... */) /* second row */ 
/*...*/ ;
```

When inserting values into a table, each of row data must contain values for each column in the data table. It is good practice to specify the exact data you have by specifying.

```sql
INSERT INTO mytable
(column , another_column ...)
VALUES ```(value_or_expr, another_value_or_expr, ...), /* first row */
(value_or_expr_2, another_value_or_expr2, ...) /* second row */
`````

It is required that for every row we insert into a table, the number of values inserted must match the number of columns available inside the table.


## Exercise

1. Add the studio's new production, **Toy Story 4** to the list of movies (you can use any director).
```sql
INSERT INTO Movies
(Id, Title, Director, Year, Length_minutes)
VALUES (4, 'Toy Story 4', 'John Lasseter', 2023, 92);
```
2. Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally. Add the record to the `BoxOffice` table. 

```sql
INSERT INTO Boxoffice
(Movie_id, Rating, Domestic_sales, International_sales)
VALUES (4, 8.7, 1000000 * 340, 1000000 * 270);
```





