# Advanced Usage -2

REPLACE function

To replace a string in a column of a table by a new string, you can use the REPLACE function. The syntax:

REPLACE(str,old\_string,new\_string);

As you can see from the syntax above, the REPLACE function accepts three parameters: it replaces the old\_string by the new\_string in the str.

Here is an example. To replace a misspelled word webseite in the string About this webseite, we would use the following command:

mysql> SELECT REPLACE (‘About this webseite’,‘webseite’,‘website’); +––––––––––––––––––+\
\| REPLACE (‘About this webseite’,‘webseite’,‘website’) | +––––––––––––––––––+

\| About this website | +––––––––––––––––––+

1 row in set (0.00 sec)

MySQL date functions

As we’ve alreadly learned, the MySQL date functions enable you to manipulate temporal values. In this article we will describe some common date functions.

CURDATE function

The CURDATE function returns the current date in YYYY-MM-DD format. Here is an example:

mysql> SELECT CURDATE(); +––––+\
\| CURDATE() |\
\+––––+

\| 2016-03-10 | +––––+\
1 row in set (0.00 sec)

DATEDIFF function

You can use the DATEDIFF function to calculate the number of days between two dates. Here is an example:

mysql> SELECT DATEDIFF(‘2016-02-05’,‘1900-03-11’) days; +––-+\
\| days |\
\+––-+

\| 42334 |\
\+––-+\
1 row in set (0.00 sec)

DATE\_ADD function

You can use the DATE\_ADD function to add a number of days, weeks, months, or years, to a date. Here is an example. To add 75 days to a date, we would use the following command:

mysql> SELECT DATE\_ADD(‘2016-05-07’, INTERVAL 75 DAY); +–––––––––––––—+\
\| DATE\_ADD(‘2016-05-07’, INTERVAL 75 DAY) | +–––––––––––––—+

\| 2016-07-21 | +–––––––––––––—+\
1 row in set (0.00 sec)

Add 2 months:

mysql> SELECT DATE\_ADD(‘2016-05-07’, INTERVAL 2 MONTH); +––––––––––––––+\
\| DATE\_ADD(‘2016-05-07’, INTERVAL 2 MONTH) | +––––––––––––––+

\| 2016-07-07 | +––––––––––––––+\
1 row in set (0.00 sec)

Add 3 years:

mysql> SELECT DATE\_ADD(‘2016-05-07’, INTERVAL 3 YEAR); +–––––––––––––—+\
\| DATE\_ADD(‘2016-05-07’, INTERVAL 3 YEAR) | +–––––––––––––—+

\| 2019-05-07 | +–––––––––––––—+\
1 row in set (0.00 sec)



DAYNAME function

Returns the name of the weekday for the date specified. Here is an example:

mysql> SELECT DAYNAME(‘2016-03-10’); +–––––––—+\
\| DAYNAME(‘2016-03-10’) |\
\+–––––––—+

\| Thursday | +–––––––—+\
1 row in set (0.00 sec)
