# SQL Lecture Notes

## 1. Introduction to SQL

### 1.1 What is SQL?

SQL (Structured Query Language) is a standard programming language used for managing and manipulating relational databases. It allows users to perform various tasks, including querying, updating, inserting, and deleting data.

### 1.2 History and Importance of SQL

SQL was developed in the 1970s by IBM for managing relational databases. It has become the standard language for interacting with relational database management systems (RDBMS) due to its simplicity and powerful capabilities.

### 1.3 Relational Databases Overview

Relational databases store data in tables, which consist of rows and columns. Each table represents an entity, and relationships between tables are established using keys.

### 1.4 Basic SQL Syntax Rules

- SQL statements are case-insensitive but conventionally written in uppercase.
- Statements end with a semicolon (`;`).
- Keywords are reserved words in SQL (e.g., `SELECT`, `INSERT`).

### 1.5 Writing Your First SQL Query

```sql
SELECT * FROM EMPLOYEES;
```

**Explanation:** This query retrieves all columns from the `EMPLOYEES` table.

## 2. Basic SQL Commands

### 2.1 SELECT Statement

The `SELECT` statement is used to query data from a table.

**SQL Code:**

```sql
SELECT FirstName, LastName FROM EMPLOYEES;
```

**Explanation:** Retrieves only the `FirstName` and `LastName` columns from the `EMPLOYEES` table.

### 2.2 SELECT DISTINCT

The `DISTINCT` keyword removes duplicate values from the results.

**SQL Code:**

```sql
SELECT DISTINCT Department FROM EMPLOYEES;
```

**Explanation:** Retrieves unique department names from the `EMPLOYEES` table.

### 2.3 WHERE Clause

The `WHERE` clause filters records based on specific conditions.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES WHERE Salary > 50000;
```

**Explanation:** Retrieves employees with a salary greater than 50,000.

### 2.4 ORDER BY

The `ORDER BY` clause sorts the result set.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES ORDER BY Salary DESC;
```

**Explanation:** Sorts employees by salary in descending order.

### 2.5 AND, OR, NOT Operators

These operators are used to combine multiple conditions in a `WHERE` clause.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES WHERE Department = 'Sales' AND Salary > 40000;
```

**Explanation:** Retrieves employees in the 'Sales' department with a salary greater than 40,000.

### 2.6 INSERT INTO

The `INSERT INTO` statement adds new rows to a table.

**SQL Code:**

```sql
INSERT INTO EMPLOYEES (FirstName, LastName, Department, Salary, JoinDate)
VALUES ('John', 'Doe', 'Marketing', 60000, '2024-01-15');
```

**Explanation:** Inserts a new employee record into the `EMPLOYEES` table.

### 2.7 Handling NULL Values

Use `IS NULL` or `IS NOT NULL` to handle NULL values.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES WHERE Department IS NULL;
```

**Explanation:** Retrieves employees with no specified department.

### 2.8 UPDATE Statement

The `UPDATE` statement modifies existing records.

**SQL Code:**

```sql
UPDATE EMPLOYEES SET Salary = 65000 WHERE EmployeeID = 1;
```

**Explanation:** Updates the salary of the employee with `EmployeeID` 1.

### 2.9 DELETE Statement

The `DELETE` statement removes records from a table.

**SQL Code:**

```sql
DELETE FROM EMPLOYEES WHERE EmployeeID = 1;
```

**Explanation:** Deletes the employee with `EmployeeID` 1.

### 2.10 SELECT TOP

The `TOP` keyword limits the number of rows returned.

**SQL Code:**

```sql
SELECT TOP 5 * FROM EMPLOYEES ORDER BY Salary DESC;
```

**Explanation:** Retrieves the top 5 highest-paid employees.

## 3. SQL Keys

### 3.1 Primary Key

#### Definition

A Primary Key is a unique identifier for a record in a table. It must be unique and not NULL.

**SQL Code:**

```sql
CREATE TABLE EMPLOYEES (
    EmployeeID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(255) NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    Department VARCHAR(255),
    Salary DECIMAL(10, 2),
    JoinDate DATE
);
```

**Explanation:** The `EmployeeID` column is the primary key.

### 3.2 Foreign Key

#### Definition

A Foreign Key is a column that links to the Primary Key of another table, establishing a relationship.

**SQL Code:**

```sql
CREATE TABLE PROJECTS (
    ProjectID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    ProjectName VARCHAR(255) NOT NULL
);

CREATE TABLE PROJECT_ASSIGNMENTS (
    EmployeeID INT,
    ProjectID INT,
    AssignmentDate DATE,
    PRIMARY KEY (EmployeeID, ProjectID),
    FOREIGN KEY (EmployeeID) REFERENCES EMPLOYEES(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES PROJECTS(ProjectID)
);
```

**Explanation:** `EmployeeID` and `ProjectID` are foreign keys in the `PROJECT_ASSIGNMENTS` table.

### 3.3 Unique Key

#### Definition

A Unique Key constraint ensures that all values in a column are unique.

**SQL Code:**

```sql
ALTER TABLE EMPLOYEES ADD UNIQUE (Email);
```

**Explanation:** Ensures that each email in the `EMPLOYEES` table is unique.

### 3.4 Composite Key

#### Definition

A Composite Key is a combination of multiple columns to uniquely identify a record.

**SQL Code:**

```sql
CREATE TABLE PROJECT_ASSIGNMENTS (
    EmployeeID INT,
    ProjectID INT,
    AssignmentDate DATE,
    PRIMARY KEY (EmployeeID, ProjectID),
    FOREIGN KEY (EmployeeID) REFERENCES EMPLOYEES(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES PROJECTS(ProjectID)
);
```

**Explanation:** Combines `EmployeeID` and `ProjectID` to create a unique key.

### 3.5 Candidate Key

#### Definition

A Candidate Key is a column or set of columns that can uniquely identify a record. There can be multiple candidate keys, but only one is chosen as the primary key.

**Example:**
In the `EMPLOYEES` table, both `EmployeeID` and `Email` could serve as candidate keys. The `EmployeeID` is chosen as the primary key.

## 4. Aggregate Functions

### 4.1 COUNT Function

#### Definition

Counts the number of rows that match a specified condition.

**SQL Code:**

```sql
SELECT COUNT(*) FROM EMPLOYEES;
```

**Explanation:** Retrieves the total number of employees.

### 4.2 SUM Function

#### Definition

Calculates the total sum of a numeric column.

**SQL Code:**

```sql
SELECT SUM(Salary) FROM EMPLOYEES;
```

**Explanation:** Retrieves the total salary of all employees.

### 4.3 AVG Function

#### Definition

Calculates the average value of a numeric column.

**SQL Code:**

```sql
SELECT AVG(Salary) FROM EMPLOYEES;
```

**Explanation:** Retrieves the average salary of all employees.

### 4.4 MIN and MAX Functions

#### Definition

Finds the minimum and maximum values of a numeric column.

**SQL Code:**

```sql
SELECT MIN(Salary) AS MinSalary, MAX(Salary) AS MaxSalary FROM EMPLOYEES;
```

**Explanation:** Retrieves the lowest and highest salaries among employees.

## 5. Advanced SQL Queries

### 5.1 LIKE Operator

#### Definition

The `LIKE` operator is used for pattern matching.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES WHERE LastName LIKE 'S%';
```

**Explanation:** Retrieves employees whose last names start with 'S'.

### 5.2 Wildcards

#### Definition

Wildcards are used with the `LIKE` operator to define search patterns.

- `%` represents zero or more characters.
- `_` represents a single character.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES WHERE LastName LIKE 'J_n%';
```

**Explanation:** Retrieves employees whose last names start with 'J', followed by any character, and then any number of characters.

### 5.3 IN Operator

#### Definition

The `IN` operator is used to specify multiple possible values for a column.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES WHERE Department IN ('Sales', 'Marketing');
```

**Explanation:** Retrieves employees who are in either 'Sales' or 'Marketing' departments.

### 5.4 BETWEEN Operator

#### Definition

The `BETWEEN` operator is used to filter records within a certain range.

**SQL Code:**

```sql
SELECT * FROM EMPLOYEES WHERE Salary BETWEEN 40000 AND 60000;
```

**Explanation:** Retrieves employees with a salary between 40,000 and 60,000.

### 5.5 Aliases (AS)

#### Definition

Aliases are used to rename columns or tables temporarily.

**SQL Code:**

```sql
SELECT FirstName AS 'First Name', Last

Name AS 'Last Name' FROM EMPLOYEES;
```

**Explanation:** Renames `FirstName` and `LastName` columns for the query output.

## 6. SQL Joins

### 6.1 INNER JOIN

#### Definition

The `INNER JOIN` returns rows when there is a match in both tables.

**SQL Code:**

```sql
SELECT EMPLOYEES.FirstName, PROJECTS.ProjectName
FROM EMPLOYEES
INNER JOIN PROJECT_ASSIGNMENTS ON EMPLOYEES.EmployeeID = PROJECT_ASSIGNMENTS.EmployeeID
INNER JOIN PROJECTS ON PROJECT_ASSIGNMENTS.ProjectID = PROJECTS.ProjectID;
```

**Explanation:** Retrieves employees and their assigned projects.

### 6.2 LEFT JOIN

#### Definition

The `LEFT JOIN` returns all rows from the left table and matched rows from the right table. Non-matching rows from the right table will have NULLs.

**SQL Code:**

```sql
SELECT EMPLOYEES.FirstName, PROJECTS.ProjectName
FROM EMPLOYEES
LEFT JOIN PROJECT_ASSIGNMENTS ON EMPLOYEES.EmployeeID = PROJECT_ASSIGNMENTS.EmployeeID
LEFT JOIN PROJECTS ON PROJECT_ASSIGNMENTS.ProjectID = PROJECTS.ProjectID;
```

**Explanation:** Retrieves all employees and their assigned projects, including those who are not assigned to any project.

### 6.3 RIGHT JOIN

#### Definition

The `RIGHT JOIN` returns all rows from the right table and matched rows from the left table. Non-matching rows from the left table will have NULLs.

**SQL Code:**

```sql
SELECT EMPLOYEES.FirstName, PROJECTS.ProjectName
FROM EMPLOYEES
RIGHT JOIN PROJECT_ASSIGNMENTS ON EMPLOYEES.EmployeeID = PROJECT_ASSIGNMENTS.EmployeeID
RIGHT JOIN PROJECTS ON PROJECT_ASSIGNMENTS.ProjectID = PROJECTS.ProjectID;
```

**Explanation:** Retrieves all projects and the employees assigned to them, including projects without assigned employees.

### 6.4 FULL JOIN

#### Definition

The `FULL JOIN` returns all rows when there is a match in one of the tables. Non-matching rows from both tables will have NULLs.

**SQL Code:**

```sql
SELECT EMPLOYEES.FirstName, PROJECTS.ProjectName
FROM EMPLOYEES
FULL JOIN PROJECT_ASSIGNMENTS ON EMPLOYEES.EmployeeID = PROJECT_ASSIGNMENTS.EmployeeID
FULL JOIN PROJECTS ON PROJECT_ASSIGNMENTS.ProjectID = PROJECTS.ProjectID;
```

**Explanation:** Retrieves all employees and projects, including those with no matches in the other table.

### 6.5 SELF JOIN

#### Definition

A `SELF JOIN` is a regular join but the table is joined with itself.

**SQL Code:**

```sql
SELECT E1.FirstName AS Employee, E2.FirstName AS Manager
FROM EMPLOYEES E1
INNER JOIN EMPLOYEES E2 ON E1.ManagerID = E2.EmployeeID;
```

**Explanation:** Retrieves a list of employees and their managers by joining the `EMPLOYEES` table with itself.

### 6.6 UNION

#### Definition

The `UNION` operator combines the results of two or more SELECT statements, removing duplicate rows.

**SQL Code:**

```sql
SELECT FirstName FROM EMPLOYEES
UNION
SELECT ProjectName FROM PROJECTS;
```

**Explanation:** Combines employee names and project names into a single result set, removing duplicates.

## 7. SQL Subqueries

### 7.1 Introduction to Subqueries

A subquery is a query within another query. It is used to retrieve data that will be used in the main query.

### 7.2 Subqueries in SELECT Statements

**SQL Code:**

```sql
SELECT FirstName, LastName
FROM EMPLOYEES
WHERE Salary > (SELECT AVG(Salary) FROM EMPLOYEES);
```

**Explanation:** Retrieves employees whose salary is above the average salary.

### 7.3 IN and EXISTS Subqueries

#### IN Subquery

**SQL Code:**

```sql
SELECT FirstName FROM EMPLOYEES
WHERE Department IN (SELECT Department FROM PROJECTS WHERE ProjectName = 'Project X');
```

**Explanation:** Retrieves employees in departments that have a project named 'Project X'.

#### EXISTS Subquery

**SQL Code:**

```sql
SELECT FirstName FROM EMPLOYEES
WHERE EXISTS (SELECT 1 FROM PROJECT_ASSIGNMENTS WHERE EMPLOYEES.EmployeeID = PROJECT_ASSIGNMENTS.EmployeeID);
```

**Explanation:** Retrieves employees who are assigned to at least one project.

### 7.4 Correlated Subqueries

#### Definition

A correlated subquery refers to columns from the outer query.

**SQL Code:**

```sql
SELECT FirstName, Salary
FROM EMPLOYEES E1
WHERE Salary > (SELECT AVG(Salary) FROM EMPLOYEES E2 WHERE E1.Department = E2.Department);
```

**Explanation:** Retrieves employees whose salary is above the average salary within their own department.

## 8. SQL Constraints

### 8.1 Check Constraint

#### Definition

The `CHECK` constraint ensures that all values in a column satisfy a specific condition.

**SQL Code:**

```sql
CREATE TABLE EMPLOYEES (
    EmployeeID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(255) NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    Salary DECIMAL(10, 2) CHECK (Salary > 0)
);
```

**Explanation:** Ensures that the `Salary` column contains only positive values.

### 8.2 Default Constraint

#### Definition

The `DEFAULT` constraint provides a default value for a column when no value is specified.

**SQL Code:**

```sql
CREATE TABLE EMPLOYEES (
    EmployeeID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(255) NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    Department VARCHAR(255) DEFAULT 'General'
);
```

**Explanation:** Sets the default department to 'General' if no value is provided.

## 9. SQL Indexes

### 9.1 What is an Index?

An index improves the speed of data retrieval operations on a table at the cost of additional space and maintenance overhead.

### 9.2 Creating and Dropping Indexes

#### Creating Index

**SQL Code:**

```sql
CREATE INDEX idx_department ON EMPLOYEES(Department);
```

**Explanation:** Creates an index on the `Department` column to speed up queries filtering by department.

#### Dropping Index

**SQL Code:**

```sql
DROP INDEX idx_department ON EMPLOYEES;
```

**Explanation:** Removes the index from the `Department` column.

### 9.3 Unique Indexes

#### Definition

A Unique Index ensures that all values in the index are unique.

**SQL Code:**

```sql
CREATE UNIQUE INDEX idx_email ON EMPLOYEES(Email);
```

**Explanation:** Creates a unique index on the `Email` column, ensuring all emails are unique.

### 9.4 Composite Indexes

#### Definition

A Composite Index is an index on multiple columns.

**SQL Code:**

```sql
CREATE INDEX idx_salary_department ON EMPLOYEES(Salary, Department);
```

**Explanation:** Creates an index on both `Salary` and `Department` columns.

## 10. SQL Views

### 10.1 Introduction to Views

A View is a virtual table based on the result of a SELECT query. It does not store data itself but presents data from one or more tables.

### 10.2 Creating and Managing Views

#### Creating View

**SQL Code:**

```sql
CREATE VIEW EmployeeView AS
SELECT FirstName, LastName, Department
FROM EMPLOYEES
WHERE Salary > 50000;
```

**Explanation:** Creates a view that includes employees with a salary greater than 50,000.

#### Updating Data through Views

**SQL Code:**

```sql
UPDATE EmployeeView
SET Salary = 55000
WHERE FirstName = 'John';
```

**Explanation:** Updates the salary of employees through the view.

## 11. SQL Transactions

### 11.1 What is a Transaction?

A Transaction is a sequence of SQL statements that are executed as a single unit of work.

### 11.2 COMMIT and ROLLBACK

#### COMMIT

**SQL Code:**

```sql
COMMIT;
```

**Explanation:** Saves all changes made during the current transaction.

#### ROLLBACK

**SQL Code:**

```sql
ROLLBACK;
```

**Explanation:** Reverts all changes made during the current transaction.

### 11.3 Transaction Control Statements

**SQL Code:**

```sql
START TRANSACTION;
-- SQL statements
COMMIT;
```

**Explanation:** Begins a transaction, executes SQL statements, and commits the transaction.

## 12. SQL Security

### 12.1 User Privileges and Roles

#### Definition

User privileges and roles control access to database objects and actions.

**SQL Code:**

```sql
GRANT SELECT, INSERT ON EMPLOYEES TO 'user'@'localhost';
```

**Explanation:** Grants SELECT and INSERT privileges on the `EMPLOYEES` table to a specific user.


### 12.2 Granting and Revoking Privileges

#### Granting Privileges

**SQL Code:**

```sql
GRANT ALL PRIVILEGES ON EMPLOYEES TO 'user'@'localhost';
```

**Explanation:** Grants all privileges on the `EMPLOYEES` table to a user.

#### Revoking Privileges

**SQL Code:**

```sql
REVOKE SELECT, INSERT ON EMPLOYEES FROM 'user'@'localhost';
```

**Explanation:** Revokes SELECT and INSERT privileges from a user.

### 12.3 SQL Injection and How to Prevent It

#### Definition

**SQL Injection** is a type of security vulnerability that occurs when an attacker is able to manipulate a SQL query by injecting malicious SQL code into it. This can lead to unauthorized access to or manipulation of the database, potentially compromising sensitive data, altering database content, or even gaining administrative access to the database system.

**How SQL Injection Works:**
SQL injection typically occurs when user input is improperly sanitized and is directly included in a SQL query. Attackers can exploit this by injecting malicious SQL code through input fields or URL parameters.

**Example of SQL Injection:**
Consider a simple login form where users provide a username and password. If the backend SQL query is constructed by directly embedding user input, it might look like this:

```sql
SELECT * FROM USERS WHERE Username = 'user_input' AND Password = 'password_input';
```

If an attacker provides `user_input` as `' OR '1'='1` and `password_input` as anything, the query becomes:

```sql
SELECT * FROM USERS WHERE Username = '' OR '1'='1' AND Password = '';
```

Here, `'1'='1'` is always true, so the query returns all rows in the `USERS` table, potentially allowing unauthorized access.

#### Prevention Techniques

**1. Use Prepared Statements**

Prepared statements (also known as parameterized queries) ensure that user inputs are treated as data, not executable code. This approach separates the query logic from the data being supplied, thus preventing injection attacks.

**Example Using Prepared Statements in MySQL:**

```sql
-- Prepare the SQL statement
PREPARE stmt FROM 'SELECT * FROM EMPLOYEES WHERE EmployeeID = ?';

-- Execute the prepared statement with a specific EmployeeID
SET @EmployeeID = 1;
EXECUTE stmt USING @EmployeeID;

-- Deallocate the prepared statement
DEALLOCATE PREPARE stmt;
```

**Explanation:** In this example, the `?` placeholder is used for the `EmployeeID`, which is supplied later. This ensures that `EmployeeID` is treated strictly as a value, not as part of the SQL code.

**2. Validate Input**

**Definition:** Input validation involves ensuring that user-provided data adheres to expected formats and constraints. This can help prevent SQL injection by rejecting or sanitizing data that does not conform to these expectations.

**Validation Techniques:**

- **Type Checking:** Ensure data types match expected types (e.g., integer, string).
- **Length Checking:** Enforce limits on input length.
- **Format Checking:** Ensure input matches expected patterns (e.g., email addresses, phone numbers).

**Example Validation in Java:**

```java
// Example of validating an integer input in Java
public boolean isValidEmployeeID(String input) {
    try {
        Integer.parseInt(input);
        return true;
    } catch (NumberFormatException e) {
        return false;
    }
}
```

**3. Employ ORM Libraries**

**Definition:** Object-Relational Mapping (ORM) libraries abstract database operations into higher-level programming constructs. They handle SQL generation and data access in a way that minimizes the risk of SQL injection.

**Popular ORM Libraries:**

- **Hibernate** (Java)
- **Entity Framework** (C#)
- **SQLAlchemy** (Python)

**Example Using Hibernate (Java):**

```java
// Using Hibernate to query employees safely
Session session = sessionFactory.openSession();
Query query = session.createQuery("FROM Employee WHERE employeeId = :id");
query.setParameter("id", 1);
List results = query.list();
session.close();
```

**Explanation:** Hibernate abstracts SQL queries and ensures that parameters are properly handled, reducing the risk of SQL injection.

**Additional Prevention Measures:**

- **Use Stored Procedures:** Ensure user inputs are handled safely within stored procedures.
- **Escape User Inputs:** Escape special characters in user inputs to neutralize potential injection code.
- **Limit Database Privileges:** Apply the principle of least privilege by restricting database user permissions.

By employing these techniques, you can significantly reduce the risk of SQL injection and enhance the security of your database systems.
