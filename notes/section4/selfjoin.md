# Self Join

We can compare and analyze relationships between data within a data table by self joining the tableto itself. Only one table is involved in a self join. 


## Example

Suppose we wanted to find the relationship between the employees and who they report to. We can grab the first name and last name of the employee and do an inner join so that we can get a match on which managers employees report to.

We can do this by creating the following query:
````python
SELECT m.firstname || ' ' || m.lastname AS 'Manager',
       e.firstname || '' || e.lastname AS 'Direct report'
FROM employees e 
INNER JOIN employees m ON m.employeeid = e.reportsto
ORDER BY manager;
````
which returns the following table:
````
Manager           Direct report  
----------------  ---------------
Andrew Adams      NancyEdwards   
Andrew Adams      MichaelMitchell
Michael Mitchell  RobertKing     
Michael Mitchell  LauraCallahan  
Nancy Edwards     JanePeacock    
Nancy Edwards     MargaretPark   
Nancy Edwards     SteveJohnson   
````

Since we used an inner join, the resulting set does not return any rows with null values. If we wanted to include people who don't report to anyone, we can simply replace the `INNER JOIN` clause with an `LEFT JOIN` clause. In this case, we would return the table above with an additional row that contains a null value:
````
Manager           Direct report  
----------------  ---------------
                  AndrewAdams    
Andrew Adams      NancyEdwards   
Andrew Adams      MichaelMitchell
Michael Mitchell  RobertKing     
Michael Mitchell  LauraCallahan  
Nancy Edwards     JanePeacock    
Nancy Edwards     MargaretPark   
Nancy Edwards     SteveJohnson   
````
