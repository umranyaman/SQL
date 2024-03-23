---
description: SELECT
---

# SQL commands - 2

We’ve learned that a table consists of rows and columns. Often, you want to see a subset rows, a subset of columns, or a combination of two. To query data from tables in MySQL, the SELECT statement is used. Here is the basic syntax:

```sql
SELECT column_name,column_name FROM table_name
```

The SELECT statement is used to control which columns and rows will be displayed. For example, if we only want to display the first name and the surname of all users in our testtb, we would use the following command:

```sql
SELECT name, surname FROM testtb;
```

To display every column in the table, we can use the asterix (\*) character:

```sql
 SELECT * FROM testtb;
```

<mark style="color:green;background-color:yellow;">**Advanced SELECT statements**</mark>

We can use many different clauses to change the behaviour of the SELECT statement.&#x20;

<mark style="color:blue;">Display the number of rows in the table:</mark>

We can use the COUNT() function to return the number of rows that matches a specified criteria. For example, to display the number of all rows in a table, we can use the following command:

<pre class="language-sql"><code class="lang-sql"><strong>SELECT COUNT(*) FROM testtb;
</strong><strong>
</strong><strong>/* 
</strong><strong>Output: 
</strong>+–––-+
| COUNT(*) |
+–––-+
|4|
+–––-+
1 row in set (0.00 sec)
*/
</code></pre>

<mark style="color:blue;">Remove duplicate rows</mark>

Sometimes, when querying data from a table, you might get duplicate rows. To remove these duplicate rows you use the DISTINCT clause in the SELECT statement. Use this when duplicated values are not allowed:

```sql
SELECT DISTINCT name FROM testtb;
```

<mark style="color:blue;">Filter records</mark>

You can narrow down queries by returning only those where a certain expression is true. To do that, the WHERE clause is used. Here is the syntax:

```sql
SELECT column_name FROM table_name WHERE column_name operator value
```

