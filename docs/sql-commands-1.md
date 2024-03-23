---
description: ALTER TABLE
---

# SQL commands - 1

<mark style="background-color:yellow;">**Rename a table**</mark>

The ALTER TABLE statement can be used to rename a table. The syntax:

```sql
ALTER TABLE old_name 
RENAME TO new_name
```

Here is how we can rename our table from testtable to testtb:

```sql
ALTER TABLE testtable 
RENAME TO testtb;
```

<mark style="background-color:yellow;">**Change the column data type**</mark>

```sql
ALTER TABLE table_name 
MODIFY column_name new_type
```

For example, to change the data type of a column called year from CHAR to INT, we can use the following command:

```sql
ALTER TABLE testtb 
MODIFY year INT;
```

<mark style="background-color:yellow;">**Add a new column**</mark>

```sql
ALTER TABLE table_name 
ADD COLUMN column_name TYPE
```

Here is an example. To add a new column called postcode of the INT type to our table testtb, we can use the following command:

```sql
ALTER TABLE testtb 
ADD COLUMN postcode INT;
```

<mark style="background-color:yellow;">**Remove a column**</mark>

```sql
ALTER TABLE table_name DROP COLUMN column_name
```

```sql
--Example:
ALTER TABLE testtb 
DROP COLUMN postcode;
```

