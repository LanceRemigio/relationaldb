SQL Lesson 1: Updating Rows

## Basics
- We can update existing data using the `UPDATE` statement. 
- Just like the `INSERT` statement, one has to specify the table, columns, and rows to update.
- Make sure the data type of the columns being updated match data type of the columns in the table.

The usual syntax for using the `UPDATE` statement is:
```sql
UPDATE mytable
SET column = value_or_expr
    other_column = another_value_or_expr
WHERE condition
```

The query above updates the rows of the columns specified satisfying the conditions specified in the `WHERE` clause.

To limit mistakes when updating tables is to use a `SELECT` statement fist to make sure the right rows are selected before updating them.


## Exercise

1. The director for A Bug's Life is incorrect, it was actually directed by **John Lasseter**.

```sql
UPDATE Movies
SET Director = 'John Lasseter'
WHERE Id = 2

```



2. The year that Toy Story 2 was released is incorrect, it was actually released in **1999**.

```sql
UPDATE Movies
SET Title = 'Toy Story 2', Year = 1999
WHERE Id = 3
```




3. Both the title and director for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by **Lee Unkrich**.

```sql
UPDATE Movies
SET Title = 'Toy Story 3', Director = 'Lee Unkrich'
WHERE Id = 11
```

