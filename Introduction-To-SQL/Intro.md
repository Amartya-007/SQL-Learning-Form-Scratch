### **1. Introduction to SQL**

SQL, or Structured Query Language, is the cornerstone of managing and interacting with relational databases. It’s a standardized language that allows you to perform various operations on the data stored in a database.

---

### **History of SQL**

- **Origin and Development**:

  - SQL was developed in the early 1970s by IBM researchers Raymond Boyce and Donald Chamberlin.
  - It was initially called SEQUEL (Structured English Query Language) but was later renamed SQL due to trademark issues.
  - The language was designed to be user-friendly, with a syntax similar to English, to enable users to manage and retrieve data from databases easily.

- **Standardization**:

  - SQL was first standardized by ANSI in 1986 and by ISO in 1987.
  - Over time, the standard has evolved with additional features and capabilities.

- **Importance of SQL in Database Management**:
  - SQL is critical in database management because it allows for:
    - Efficient data retrieval and manipulation.
    - Consistency in how data is managed across different platforms.
    - Scalability in handling large volumes of data.

---

### **What is SQL?**

- **Definition and Purpose**:

  - SQL stands for Structured Query Language.
  - It is used to interact with relational databases, performing tasks such as querying data, updating records, and managing access control.

- **Overview of Relational Databases**:
  - A relational database is a collection of data organized into tables, where data is stored in rows and columns.
  - Tables in a relational database can be linked to each other through relationships, which makes it easier to manage and retrieve related data.

---

### **SQL Syntax**

- **Basic SQL Syntax Rules**:

  - SQL statements are not case-sensitive, but it’s common practice to write SQL keywords in uppercase (e.g., SELECT, FROM, WHERE).
  - Each SQL statement typically ends with a semicolon (`;`).
  - Comments can be added using `--` for single-line comments or `/* */` for multi-line comments.

- **Structure of SQL Statements**:

  - A basic SQL query follows this structure:
    ```sql
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition;
    ```
  - **SELECT**: Specifies which columns of data to retrieve.
  - **FROM**: Indicates the table from which to retrieve the data.
  - **WHERE**: Filters the records based on a specific condition.

- **Writing Your First SQL Query**:
  - Example:
    ```sql
    SELECT CustomerName, City
    FROM Customers
    WHERE Country = 'USA';
    ```
  - This query retrieves the names and cities of customers who are located in the USA from the `Customers` table.

---

### **Additional Example Tables**

- **Products Table**:

  - Imagine a table that stores information about products:

    | ProductID | ProductName | SupplierID | CategoryID | Price |
    | --------- | ----------- | ---------- | ---------- | ----- |
    | 1         | Laptop      | 1          | 2          | 800   |
    | 2         | Smartphone  | 2          | 1          | 600   |
    | 3         | Tablet      | 3          | 2          | 300   |

  - **Columns**:
    - `ProductID`: Unique identifier for each product.
    - `ProductName`: Name of the product.
    - `SupplierID`: ID of the supplier providing the product.
    - `CategoryID`: ID of the category to which the product belongs.
    - `Price`: Price of the product.

- **Orders Table**:

  - A table that stores information about customer orders:

    | OrderID | CustomerID | OrderDate  | TotalAmount |
    | ------- | ---------- | ---------- | ----------- |
    | 101     | 1          | 2024-08-10 | 1500        |
    | 102     | 2          | 2024-08-11 | 2000        |
    | 103     | 1          | 2024-08-12 | 500         |

  - **Columns**:
    - `OrderID`: Unique identifier for each order.
    - `CustomerID`: ID of the customer who placed the order.
    - `OrderDate`: Date when the order was placed.
    - `TotalAmount`: Total amount for the order.
