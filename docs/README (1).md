# Data Types in MySQL

#### MySQL Data Types

MySQL supports a wide range of data types, categorized into three main types: String, Numeric, and Date and Time.

**String Data Types**

* **CHAR(size)**: A fixed-length string (can contain letters, numbers, and special characters) between 1 and 255 characters in length.
* **VARCHAR(size)**: A variable-length string with a maximum length specified in size (1 to 65535).
* **TEXT**: Holds a string with a maximum length of 65,535 bytes.

**Numeric Data Types**

* **INT**: A medium-sized integer that can be signed or unsigned.
* **DECIMAL(M,D)**: An exact fixed-point number where M is the total number of digits and D is the number of digits after the decimal.
* **FLOAT(M,D)**: A floating-point number where M is the total number of digits and D is the number of digits after the decimal.

**Date and Time Data Types**

* **DATE**: For date values (YYYY-MM-DD).
* **DATETIME**: To store date and time values (YYYY-MM-DD HH:MM:SS).
* **TIMESTAMP**: For timestamp values (YYYY-MM-DD HH:MM:SS), automatically updated to the current date and time on each modification.
* **YEAR**: Stores a year in 2-digit or 4-digit format. The valid range for the 4-digit format is from 1901 to 2155, and 0000.

#### Binary Data Types

* **BINARY(size):** Similar to CHAR, but stores binary byte strings. Size can vary from 1 to 255 bytes.
* **VARBINARY(size):** Corresponds to VARCHAR, but for binary byte strings, with a size range from 1 to 65535 bytes.
* **BLOB:** A binary large object that can hold a variable amount of data up to 65,535 bytes.

#### Miscellaneous Data Types

* **ENUM(val1, val2, val3, ...):** A string object that can have only one value, chosen from a list of values which are explicitly enumerated when the table is created, up to 65535 distinct values.
* **SET(val1, val2, val3, ...):** Similar to ENUM but can hold one or more of the values listed. A SET can store up to 64 different values.

**Other Data Types**

* BOOLEAN: Synonymous with TINYINT(1), where values '0' and '1' represent 'false' and 'true', respectively.

#### Spatial Data Types

* **GEOMETRY**: A type that can store any type of Geometry.
* **POINT**: Represents a single point on a coordinate plane.
* **LINESTRING**: A series of points used to form a line.
* **POLYGON**: A geometry type that represents a polygon.
* **MULTIPOINT**, **MULTILINESTRING**, **MULTIPOLYGON**, and **GEOMETRYCOLLECTION**: Collection types that can store combinations of the other geometry types.

````markdown
### Example Table Creation and Data Insertion

#### Creating a Sample Table

```sql
CREATE TABLE example_table (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    balance DECIMAL(10,2),
    birth_date DATE,
    signup_datetime DATETIME,
    document TEXT,
    user_status ENUM('active', 'inactive', 'suspended'),
    preferences SET('email', 'sms', 'push'),
    location POINT
);
````

**Inserting Data Into the Table**

```sql
INSERT INTO example_table (name, age, balance, birth_date, signup_datetime, document, user_status, preferences, location) 
VALUES ('John Doe', 30, 10000.00, '1990-01-01', '2023-01-01 08:30:00', 'This is a sample document text.', 'active', 'email,sms', ST_PointFromText('POINT(1 1)'));
```

`ENUM` data type for `user_status` has a value of 'active', and the `SET` type for `preferences` includes both 'email' and 'sms'. The `location` column, which is a `POINT` data type, is filled with the `ST_PointFromText` function, which takes a string representation of a point.

**Working with CHAR and VARCHAR**

```sql
CREATE TABLE user_profiles (
user_id INT AUTO_INCREMENT PRIMARY KEY,
username CHAR(50),
email VARCHAR(255),
bio TEXT
);

INSERT INTO user_profiles (username, email, bio)
VALUES ('johndoe', 'johndoe@example.com', 'Just a regular guy who loves coding.');
```

**Utilizing Numeric Data Types**

```sql
CREATE TABLE financial_records (
record_id INT AUTO_INCREMENT PRIMARY KEY,
monthly_income DECIMAL(10,2),
yearly_expense FLOAT(12,2)
);

INSERT INTO financial_records (monthly_income, yearly_expense)
VALUES (5000.00, 48000.00);
```

**Date and Time Data Types Example**

```sql
CREATE TABLE events (
event_id INT AUTO_INCREMENT PRIMARY KEY,
event_name VARCHAR(100),
event_date DATE,
start_time DATETIME,
end_time TIMESTAMP
);

INSERT INTO events (event_name, event_date, start_time)
VALUES ('Tech Conference', '2023-09-15', '2023-09-15 09:00:00');
```

**Incorporating Binary and Miscellaneous Data Types**

```sql
CREATE TABLE file_storage (
file_id INT AUTO_INCREMENT PRIMARY KEY,
file_name VARCHAR(100),
file_data BLOB,
file_type ENUM('document', 'image', 'video'),
privacy_setting SET('private', 'public', 'friends_only')
);

INSERT INTO file_storage (file_name, file_data, file_type, privacy_setting)
VALUES ('profile_pic.png', LOAD_FILE('/path/to/image'), 'image', 'private');
```

### <mark style="color:blue;background-color:yellow;">Similar MySQL Data Types and Best Practices</mark>

When working with MySQL, understanding the similarities and differences between various data types can help prevent confusion and ensure data integrity. Here are some similar data types and suggestions on how not to mix them up:

#### String vs. Binary Data Types

* **CHAR and BINARY**: Both are fixed-length types that store exact character lengths. Use CHAR for text and BINARY for binary data like images or files.
* **VARCHAR and VARBINARY**: These are variable-length types. VARCHAR is ideal for text that varies in length, while VARBINARY is suited for variable-length binary data.

#### Numeric Data Types

* **INT vs. DECIMAL**: INT is used for integers without decimals, and DECIMAL is for precise fixed-point numbers. Avoid using DECIMAL when dealing with whole numbers to save space.
* **FLOAT vs. DECIMAL**: FLOAT is for floating-point numbers with approximate precision. Use DECIMAL for numbers where exact precision is crucial, like in financial calculations.

#### Date and Time Data Types

* **DATETIME vs. TIMESTAMP**: Both store date and time, but TIMESTAMP values are converted to UTC and from UTC upon retrieval, which makes them sensitive to time zone settings. Use TIMESTAMP for values that should reflect the current time or are affected by time zones, and DATETIME for static or historical timestamps that should not change with time zone shifts.

#### ENUM vs. SET

* Although ENUM and SET can appear similar since both define a list of allowable values, ENUM restricts a field to a single value from the list, while SET allows multiple values from the list to be stored together. It's important not to use ENUM when you might need to store multiple, non-exclusive options.
