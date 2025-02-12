# AS - Union

Aliases

An alias is just an alternate name for a field or value that improves the readability of the queries. They are assigned with the AS keyword and can be single words or complete strings.

Consider the following example to understand the usefulness of aliases. Let’s say that we want to return the current date. We can do it with the following command:

mysql> SELECT CURDATE(); +––––+\
\| CURDATE() |\
\+––––+

\| 2016-03-10 | +––––+\
1 row in set (0.00 sec)

Notice how the column returned was named CURDATE(). We can define more user friendly name for the column using aliases. Here is how we would do that:

mysql> SELECT CURDATE() AS CurrentDate; +––––-+\
\| CurrentDate |\
\+––––-+

\| 2016-03-10 | +––––-+\
1 row in set (0.00 sec)

The column now has a more descriptive name - CurrentDate.

Combine multiple SELECT statements\
You can combine multiple SELECT statements into one result set using the UNION

operator. The syntax is:\
SELECT column1, column2 UNION SELECT column1, column2

Here is an example. Let’s say that we have the following two tables:

mysql> SELECT \* FROM buyers; +–-+–––—+––—+–––+\
\| id | username | city | country | +–-+–––—+––—+–––+

\| 1|john |London|UK |\
\| 2|mark |Berlin|Germany| | 3 | alejandra | Madrid | Spain | +–-+–––—+––—+–––+\
3 rows in set (0.00 sec)

mysql> SELECT \* FROM testtb; +––-+––––-+––+

\| name | surname +––-+––––-+––+ | Amy | Bryant\
\| Mark | Smith

\| year |

\| 1991 | | 1955 |

\| John | von Neumann | 1921 | | Aaron | Rogers | 1995 |\
\| Brian | Cormier | 1988 | +––-+––––-+––+

5 rows in set (0.00 sec)

We want to combine the username column from the buyers table with the name column from the testtb table. Here is how we would do that:

mysql> SELECT username FROM buyers UNION SELECT name FROM testtb; +–––—+\
\| username |\
\+–––—+

\| john |\
\| mark\
\| alejandra |

\| Amy\
\| Aaron | Brian

|

|

\| |

\+–––—+\
6 rows in set (0.00 sec)

NOTE - the number of columns in the SELECT statements must be equal.
