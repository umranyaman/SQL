# SQL Commands - 3

Remove a row

You can use the DELETE command to remove a row from a table. The syntax:

DELETE FROM table\_name WHERE column\_name operator value

Here is an example. We have our old table testtb:



SELECT \* FROM testtb;

Let’s say that we watn to delete the last row. We can do it by specifying the surname Jones with the WHERE clause:



DELETE FROM testtb WHERE surname=‘Jones’;

<mark style="color:red;">NOTE - make sure to include the WHERE clause. If you omit it, all records in the table will be deleted!</mark>



LIMIT clause

Sometimes tables contain thousands of rows and if you run a SELECT statement to display all rows, you will impact performance and possibly even crash the system. However, you can use the LIMIT clause to choose how many rows will be returned in a query. Here is an example:

SELECT \* FROM employees LIMIT 5;

The employees table mentioned above contains thousands of rows. Using the LIMIT clause, we were able to display only the first 5 rows.

You can also specify the starting position. For example, to start at the position 2 and return 7 rows, we can use the following command:

SELECT \* FROM employees LIMIT 2,7;

<mark style="color:green;">NOTE - notice that the second row in the employees table was not included in the output above. The LIMIT 2,7 keyword means return seven rows starting from the third row.</mark>

Update the contents of a field

One of the most common tasks when working with MySQL databases is the data update. To update records in an MySQL table, the UPDATE statement is used. Here is the syntax:

UPDATE table\_name SET column1=value1,column2=value2,... WHERE column\_name operator value

As you can see from the syntax above, you first need to specify the table name. Second, you need to specify which columns will be modified and their new values after the SET clause. Lastly, you need to specify which rows will be updated using the WHERE clause.



Here is an example. We have our old table testtb:

SELECT \* FROM testtb;

Let’s say that Amy Goodridge married and changed her surname to Bryant. To update the surname field, we can use the following syntax:

UPDATE testtb SET surname=‘Bryant’ WHERE surname=‘Goodridge’;

SELECT \* FROM testtb;



NOTE - make sure to include the WHERE clause; otherwise, the UPDATE statement

will update all rows in the table!



Sort results

You might have noticed that, when you use the SELECT statement to query data, the results are not sorted in any orders. To sort returned results by one or more columns in ascending or descending order, you can use the ORDER BY clause. Here is the syntax:



SELECT column1, column2,... FROM table\_name ORDER BY column1 \[ASC|DESC], column2 \[ASC|DESC],...

Here is a simple example. We will work with the following table:



SELECT \* FROM testtb;

To sort the results by name, we would use the following command:

SELECT \* FROM testtb ORDER BY name;

To sort in descending order, we would add the DESC keyword after the column name:

SELECT \* FROM testtb ORDER BY name DESC;

