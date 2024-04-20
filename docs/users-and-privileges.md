# Users and Privileges

#### Creating Users in MySQL

To create a user in MySQL, use the following syntax:

```sql
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```

Replace `username` with the name of the user you want to create, and `password` with the user's password.

#### Granting Privileges

After creating a user, you need to grant them privileges so they can perform operations. Use the GRANT statement:

```sql
GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';
```

This grants all privileges to the user on the specified database. You can replace `ALL PRIVILEGES` with specific privileges like `SELECT`, `INSERT` etc., and `database_name.*` with specific databases or tables.

#### Applying the Changes

To make the privilege changes take effect, use:

```sql
FLUSH PRIVILEGES;
```

This command reloads the grant tables in the MySQL database, enabling the changes to take effect.

#### Granting Specific Privileges

Instead of granting all privileges, you can specify which actions a user can perform on a database or table. For example, to grant a user the ability to only read (select) and insert data into the `sales` database, you would use:

```sql
GRANT SELECT, INSERT ON sales.* TO 'username'@'localhost';
```

This command allows the user to perform `SELECT` and `INSERT` operations on all tables within the `sales` database.

#### Granting Privileges on Specific Tables

If you need to restrict a user's privileges to specific tables, you can specify the table name instead of using `*`. For example, to allow a user to only insert data into the `orders` table in the `sales` database, you would use:

```sql
GRANT INSERT ON sales.orders TO 'username'@'localhost';
```

This narrows down the privileges to a specific action on a specific table, providing fine-grained control over database access.
