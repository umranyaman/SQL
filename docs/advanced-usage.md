# Advanced usage

Primary keys

A primary key is a column or a set of columns that uniquely identifies each record in a database table. It is usually created when the table is created, but it can also be added to an existing table that does not have one.

Here are the rules you should be familiar with when creating a primary key for a table:

a primary key must contain unique values.\
a primary key column cannot contain NULL values. each table can have only one primary key.

Here is an example. Let’s say that we want to create a table called buyers, with the id column serving as the primary key. The table should have three other columns: username, city, and country. Here is the syntax we would use:

CREATE TABLE buyers(\
id INT AUTO\_INCREMENT PRIMARY KEY, username VARCHAR(40),\
city VARCHAR(255),\
country VARCHAR(255)

);

The AUTO\_INCREMENT attribute causes MySQL to set a unique value for the id column in every row. Since no value was specified for the AUTO\_INCREMENT column, MySQL will assign sequence numbers automatically.

Let’s insert some records into our table:

mysql> INSERT INTO buyers (username, city, country) VALUES (‘john’,‘London’,‘UK’ );\
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO buyers (username, city, country) VALUES (‘mark’,‘Berlin’,‘Ger many’);\
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO buyers (username, city, country) VALUES (‘alejandra’,‘Madrid’ ,‘Spain’);\
Query OK, 1 row affected (0.00 sec)

mysql> SELECT \* FROM buyers; +–-+–––—+––—+–––+\
\| id | username | city | country | +–-+–––—+––—+–––+

\| 1|john |London|UK |\
\| 2|mark |Berlin|Germany| | 3 | alejandra | Madrid | Spain | +–-+–––—+––—+–––+\
3 rows in set (0.00 sec)

Notice how the AUTO\_INCREMENT attribute forced the id column to start with 1, and to increment by 1 for each new record.

MySQL functions

MySQL functions allow you to work on the data right in the database. There are many MySQL built-in functions for performing calculations on data. They can be divided into three general types:

String functions - used to manipulate strings of data. Examples of this type of functions are CONCAT, REPLACE, FORMAT, and LOCATE.\
Date functions - used to manipulate temporal values. Examples are DATE, DATEDIFF, and DATE\_ADD.

Aggregate functions - used to perform a calculation on a set of values and return a single value. Examples are AVG, COUNT, SUM, MIN, and MAX.

MySQL string functions

As we’ve mentioned in the previous article, the MySQL string functions enable you to manipulate strings of data. In this article we will describe some common string functions. We will use our old table testtb for the examples in this chapter:

mysql> SELECT \* FROM testtb; +––-+––––-+––+

\| name | surname +––-+––––-+––+ | Amy | Bryant\
\| Mark | Smith

\| year |

\| 1991 | | 1955 |

\| John | von Neumann | 1921 | | Aaron | Rogers | 1995 |\
\| Brian | Cormier | 1988 | +––-+––––-+––+

5 rows in set (0.00 sec)

CONCAT function

The CONCAT function is used to concatenate two or more strings together. For example, to return the full names of contacts, we will use the CONCAT function to concatenate the name and surname columns:

mysql> SELECT CONCAT (name,’ ‘,surname) FROM testtb; +–––––––––+\
\| CONCAT (name,’ ‘,surname) |\
\+–––––––––+

\| Amy Bryant\
\| Mark Smith\
\| John von Neumann\
\| Aaron Rogers\
\| Brian Cormier +–––––––––+\
5 rows in set (0.01 sec)

LENGTH function

\| |

\| |

|

The LENGTH function returns the length of a string in bytes. To get the actual number of characters in a string, we can use the CHAR\_LENGTH function.

For example, to get the character length of the records in the column name, we would use the following command:

mysql> SELECT CHAR\_LENGTH (name) FROM testtb; +––––––—+\
\| CHAR\_LENGTH (name) |\
\+––––––—+

|3| |4| |4| |5| |5| +––––––—+\
5 rows in set (0.00 sec)
