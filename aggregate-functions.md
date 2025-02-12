# Aggregate Functions

MySQL aggregate functions

As we’ve already learned, the MySQL aggregate functions enable you to perform a calculation on a set of values and return a single value. In this article we will describe some common aggregate functions.We will use our old table testtb for the examples in this chapter:

mysql> SELECT \* FROM testtb; +––-+––––-+––+

\| name | surname +––-+––––-+––+ | Amy | Bryant\
\| Mark | Smith

\| year |

\| 1991 | | 1955 |

\| John | von Neumann | 1921 | | Aaron | Rogers | 1995 |\
\| Brian | Cormier | 1988 | +––-+––––-+––+

5 rows in set (0.00 sec)

AVG function

You can use the MySQL AVG function to calculate the average value of a set of values or an expression. For example, to calculate the average birth year of all users in the testtb table, we would use the following command:

mysql> SELECT AVG(year) FROM testtb; +–––—+

\| AVG(year) | +–––—+\
\| 1970.0000 | +–––—+

1 row in set (0.00 sec)

MIN function

You can use the MIN function to find the minimum value in a set of values. For example, to find the oldest person in our testtb table, we would use the following command:

mysql> SELECT MIN(year) FROM testtb; +–––—+\
\| MIN(year) |\
\+–––—+

\| 1921 |\
\+–––—+\
1 row in set (0.00 sec)

MAX function

You can use the MAX function to get the maximum value in a set of values. For example, to find the youngest person in our testtb table, we would use the following command:

mysql> SELECT MAX(year) FROM testtb; +–––—+\
\| MAX(year) |\
\+–––—+

\| 1995 |\
\+–––—+\
1 row in set (0.00 sec)
