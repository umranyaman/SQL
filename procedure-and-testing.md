# Procedure and Testing

Procedures and Testing in MySQL

Procedures in MySQL are stored programs that you can pass parameters into. They allow you to encapsulate complex operations into a single callable routine.

**Creating a Procedure**

Here's how you can create a simple procedure in MySQL:

```sql
DELIMITER $$

CREATE PROCEDURE GetCustomerCount()
BEGIN
  SELECT COUNT(*) FROM customers;
END$$

DELIMITER ;
```

This procedure, `GetCustomerCount`, when called, will return the count of rows in the `customers` table.

**Calling a Procedure**

To call this procedure, you use the `CALL` statement like this:

```sql
CALL GetCustomerCount();
```

#### Additional Examples of MySQL Stored Procedures

Following the pattern of the `GetCustomerCount` procedure, let's consider another example where we want to fetch the latest registered customer's details. For this purpose, we can create a procedure named `GetLatestCustomer`.

1. **Creating the Procedure**
2.  ```sql
    DELIMITER $$

    CREATE PROCEDURE GetLatestCustomer()
    BEGIN
      SELECT * FROM customers ORDER BY registration_date DESC LIMIT 1;
    END$$

    DELIMITER ;
    ```

    This procedure selects all columns for the most recently registered customer based on a descending order of their registration date, returning only the topmost record.

    2. **Calling the Procedure**

    To execute this newly created procedure and get the details of the latest customer, you would use the following `CALL` statement:

    ```sql
    CALL GetLatestCustomer();
    ```



####
