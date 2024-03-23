# CRUD operations

#### CRUD Operations in MySQL

CRUD stands for Create, Read, Update, and Delete.&#x20;

Below is a brief explanation of each operation in the context of MySQL.

<mark style="color:red;background-color:yellow;">**Create**</mark>

To insert data into a database, you use the `INSERT` statement.

```sql
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```

<mark style="color:red;background-color:yellow;">**Read**</mark>

To query or read data from a database, you use the `SELECT` statement.

```sql
SELECT column1, column2 FROM table_name WHERE condition;
```

<mark style="color:red;background-color:yellow;">**Update**</mark>

To modify existing data within a table, you use the `UPDATE` statement.

```sql
 UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```

<mark style="color:red;background-color:yellow;">**Delete**</mark>

To remove data from a table, you use the `DELETE` statement.

```sql
DELETE FROM table_name WHERE condition;
```

For example the table below has the following schema: `id` (unique identifier), `title`, `author`, and `year_published`.



<mark style="color:orange;">**EXAMPLES**</mark>

**Create**

To add multiple entries into our `books` table, we use the INSERT statement as follows:

```sql
INSERT INTO books (id, title, author, year_published) VALUES 
(1, 'The Great Gatsby', 'F. Scott Fitzgerald', 1925),
(2, '1984', 'George Orwell', 1949),
(3, 'To Kill a Mockingbird', 'Harper Lee', 1960);
```

This statement inserts three new rows into the `books` table, each representing a distinct book.

**Read**

To find all books published before the year 1970, we utilize the SELECT statement for a conditional query:

```sql
SELECT * FROM books WHERE year_published < 1970;
```

This query fetches all rows (representing books) from the `books` table where `year_published` is less than 1970.

**Complex Read Operations**

If we want to count the number of books each author has in the database, we can use a more complex SELECT statement:

```sql
SELECT author, COUNT(author) AS number_of_books FROM books GROUP BY author;
```

This returns a count of books for each author by grouping the results based on the author column.

**Update**

Suppose a book has a revised edition, and we need to update both its title and year of publication. For example, updating the year of publication and title for 'The Great Gatsby':

```sql
UPDATE books SET title = 'The Great Gatsby: Revised Edition', year_published = 2023 WHERE id = 1;
```

This statement modifies the title and year\_published of the book whose ID is 1.

**Delete**

If a book is no longer available or relevant, it can be removed from the database:

```sql
DELETE FROM books WHERE year_published < 1950;
```

This command will delete all records of books published before 1950, ensuring the dataset remains up to date with relevant entries.

