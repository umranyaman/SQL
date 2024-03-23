# SQL Commands - 4

Use logical operators

You can use the logical operators AND, OR, and NOT to filter records based on more than one condition and narrow down your selection. Here are the meanings of these operators:

AND - displays a record if both the first condition and the second condition are true. OR - displays a record if either the first condition or the second condition is true. NOT - displays a record if the opposite of the condition is true

Here are the examples. We will work with our old testtb table:

mysql> SELECT \* FROM testtb; +––-+––––-+––+

\| name | surname +––-+––––-+––+ | Amy | Bryant\
\| Mark | Smith

\| year |

\| 1991 | | 1955 |

\| John | von Neumann | 1921 | | Aaron | Rogers | 1995 |\
\| Brian | Cormier | 1988 | +––-+––––-+––+

5 rows in set (0.00 sec)

AND example:

mysql> SELECT \* FROM testtb WHERE name=‘Amy’ AND surname=‘Bryant’; +––+–––+––+\
\| name | surname | year |\
\+––+–––+––+

\| Amy | Bryant | 1991 |

\+––+–––+––+\
1 row in set (0.01 sec)



