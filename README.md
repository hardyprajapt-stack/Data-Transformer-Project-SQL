# sql.project2
Data Transformer is a SQL-based project that manages customers, orders, and employee data. It demonstrates SQL operations including JOINs, subqueries, date functions, string functions, window functions, and CASE statements for data analysis and transformation.



# 🔄 Data Transformer Project — SQL

![MySQL](https://img.shields.io/badge/MySQL-Database-blue?style=for-the-badge\&logo=mysql)
![SQL](https://img.shields.io/badge/SQL-Data%20Transformation-orange?style=for-the-badge)
![Joins](https://img.shields.io/badge/SQL-JOINs-purple?style=for-the-badge)
![Analytics](https://img.shields.io/badge/Data-Analytics-success?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

# 📌 Project Overview

**Data Transformer Project** is a practical **MySQL SQL project** created to demonstrate how raw relational data can be connected, transformed, cleaned, analyzed, and converted into useful business information using SQL.

The project contains three main datasets:

* 👥 **Customers**
* 🛒 **Orders**
* 👨‍💼 **Employees**

The SQL implementation covers a wide range of practical data-analysis techniques, including:

* Database creation
* Table creation
* Primary Keys
* Foreign Keys
* Data insertion
* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL OUTER JOIN simulation
* Subqueries
* Average-based filtering
* Date extraction
* Date difference
* Date formatting
* String concatenation
* String replacement
* Uppercase / lowercase transformation
* TRIM for data cleaning
* Running totals
* Ranking
* CASE statements
* Conditional business logic
* Salary categorization
* Data inspection

The project demonstrates how SQL can be used to transform database records into structured information that can support **business analysis and reporting**.

---

# 🎯 Project Objectives

The main objectives of this project are:

1. Create a relational SQL database.
2. Store customer information.
3. Store customer order information.
4. Store employee information.
5. Establish relationships between customers and orders.
6. Combine information from multiple tables.
7. Identify customers with above-average orders.
8. Identify employees with above-average salaries.
9. Extract useful information from dates.
10. Calculate the difference between dates.
11. Format dates into readable formats.
12. Clean and transform text data.
13. Calculate cumulative order values.
14. Rank orders based on their total amount.
15. Apply conditional business rules.
16. Categorize employee salaries.
17. Demonstrate practical SQL techniques used in data analytics.

---

# 🗄️ Database Information

## Database Name

```text
DataTransformerProject
```

The database is created using:

```sql
CREATE DATABASE DataTransformerProject;

USE DataTransformerProject;
```

---

# 🏗️ Database Structure

The project contains **3 tables**:

```text
DataTransformerProject
│
├── Customers
│
├── Orders
│
└── Employees
```

The relationship between the tables is:

```text
Customers
    │
    │ CustomerID
    │
    ▼
Orders
```

The `Employees` table is an independent table used for employee salary analysis.

---

# 📊 Table 1 — Customers

The `Customers` table stores basic customer information.

## Columns

| Column     | Data Type    | Description                |
| ---------- | ------------ | -------------------------- |
| CustomerID | INT          | Unique customer identifier |
| FirstName  | VARCHAR(50)  | Customer first name        |
| LastName   | VARCHAR(50)  | Customer last name         |
| Email      | VARCHAR(100) | Customer email address     |
| City       | VARCHAR(50)  | Customer city              |

## Primary Key

```text
CustomerID
```

Each customer has a unique `CustomerID`.

---

# 📦 Table 2 — Orders

The `Orders` table stores customer order information.

## Columns

| Column      | Data Type     | Description                   |
| ----------- | ------------- | ----------------------------- |
| OrderID     | INT           | Unique order identifier       |
| CustomerID  | INT           | Customer who placed the order |
| OrderDate   | DATE          | Date of order                 |
| TotalAmount | DECIMAL(10,2) | Total order value             |

## Primary Key

```text
OrderID
```

## Foreign Key

```text
CustomerID
```

The `CustomerID` column connects the `Orders` table with the `Customers` table.

Relationship:

```text
Customers.CustomerID
        ↓
Orders.CustomerID
```

---

# 👨‍💼 Table 3 — Employees

The `Employees` table contains employee information and salary details.

## Columns

| Column     | Data Type     | Description                |
| ---------- | ------------- | -------------------------- |
| EmployeeID | INT           | Unique employee identifier |
| FirstName  | VARCHAR(50)   | Employee first name        |
| LastName   | VARCHAR(50)   | Employee last name         |
| Department | VARCHAR(50)   | Employee department        |
| HireDate   | DATE          | Employee hiring date       |
| Salary     | DECIMAL(10,2) | Employee salary            |

## Departments Included

The sample data contains:

* Sales
* HR
* IT
* Finance

---

# 🔗 Database Relationship

The primary relationship in this project is:

```text
┌─────────────────────┐
│      Customers      │
├─────────────────────┤
│ CustomerID PK       │
│ FirstName           │
│ LastName            │
│ Email               │
│ City                │
└──────────┬──────────┘
           │
           │ 1 : Many
           │
           ▼
┌─────────────────────┐
│       Orders        │
├─────────────────────┤
│ OrderID PK          │
│ CustomerID FK       │
│ OrderDate           │
│ TotalAmount         │
└─────────────────────┘


┌─────────────────────┐
│     Employees       │
├─────────────────────┤
│ EmployeeID PK       │
│ FirstName           │
│ LastName            │
│ Department          │
│ HireDate            │
│ Salary              │
└─────────────────────┘
```

One customer can have multiple orders.

```text
1 Customer → Many Orders
```

---

# 📥 Sample Customer Data

The project contains sample customers such as:

| CustomerID | Name          | City        |
| ---------: | ------------- | ----------- |
|          1 | John Doe      | New York    |
|          2 | Jane Smith    | Los Angeles |
|          3 | Michael Brown | Chicago     |
|          4 | Emily Davis   | Houston     |

---

# 🛒 Sample Order Data

The project contains sample orders such as:

| OrderID | CustomerID | OrderDate  | TotalAmount |
| ------: | ---------: | ---------- | ----------: |
|     101 |          1 | 2023-07-01 |      150.50 |
|     102 |          2 | 2023-07-03 |      200.75 |
|     103 |          1 | 2023-07-05 |      300.00 |
|     104 |          3 | 2023-07-07 |      450.25 |
|     105 |          2 | 2023-07-10 |      120.00 |

---

# 👨‍💼 Sample Employee Data

The project contains employees from multiple departments.

| EmployeeID | Name         | Department | Hire Date  | Salary |
| ---------: | ------------ | ---------- | ---------- | -----: |
|          1 | Mark Johnson | Sales      | 2020-01-15 |  50000 |
|          2 | Susan Lee    | HR         | 2021-03-20 |  55000 |
|          3 | David Wilson | IT         | 2019-06-11 |  70000 |
|          4 | Nancy Taylor | Finance    | 2022-02-05 |  48000 |
|          5 | Chris Martin | Sales      | 2018-08-22 |  65000 |

---

# 🔄 SQL Data Transformation Techniques

This project focuses heavily on transforming raw database information into useful analytical outputs.

The major transformation categories are:

```text
Raw Data
   ↓
JOIN
   ↓
Filter
   ↓
Aggregate
   ↓
Transform
   ↓
Calculate
   ↓
Classify
   ↓
Analyze
```

---

# 1️⃣ INNER JOIN

The first query combines customers with their orders.

```sql
SELECT
    Customers.CustomerID,
    Customers.FirstName,
    Customers.LastName,
    Orders.OrderID,
    Orders.OrderDate,
    Orders.TotalAmount
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

## Purpose

Returns customers who have matching orders.

The result combines information from:

```text
Customers
+
Orders
```

For example:

```text
John Doe
    ↓
Order 101
    ↓
$150.50
```

## Concept Demonstrated

```text
INNER JOIN = Matching records from both tables
```

---

# 2️⃣ LEFT JOIN

```sql
SELECT
    Customers.CustomerID,
    Customers.FirstName,
    Customers.LastName,
    Orders.OrderID,
    Orders.TotalAmount
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

## Purpose

Returns **all customers**, along with their orders when a matching order exists.

This is useful for finding customers who:

* Have orders
* Do not have orders

If a customer has no matching order, order-related columns will contain `NULL`.

---

# 3️⃣ RIGHT JOIN

```sql
SELECT
    Orders.OrderID,
    Orders.OrderDate,
    Customers.FirstName,
    Customers.LastName
FROM Customers
RIGHT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

## Purpose

Returns all records from the `Orders` table and matching customer information.

This demonstrates how a `RIGHT JOIN` can preserve all records from the right-side table.

---

# 4️⃣ FULL OUTER JOIN Simulation

MySQL does not provide a native `FULL OUTER JOIN` syntax.

Therefore, this project simulates a full outer join using:

```text
LEFT JOIN
+
UNION
+
RIGHT JOIN
```

Query:

```sql
SELECT
    Customers.CustomerID,
    Customers.FirstName,
    Orders.OrderID,
    Orders.TotalAmount
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID

UNION

SELECT
    Customers.CustomerID,
    Customers.FirstName,
    Orders.OrderID,
    Orders.TotalAmount
FROM Customers
RIGHT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

## Concept

A full outer join conceptually returns:

```text
All Customers
+
Matching Orders
+
Unmatched records
```

The `UNION` combines the two result sets and removes duplicate rows.

---

# 5️⃣ Subquery — Customers With Above-Average Orders

```sql
SELECT DISTINCT CustomerID
FROM Orders
WHERE TotalAmount > (
    SELECT AVG(TotalAmount)
    FROM Orders
);
```

## How It Works

First, the inner query calculates the average order amount:

```sql
SELECT AVG(TotalAmount)
FROM Orders;
```

Then the outer query finds orders whose amount is greater than that average.

Conceptually:

```text
All Order Amounts
       ↓
Calculate Average
       ↓
Compare Each Order
       ↓
Above-Average Orders
       ↓
Return Customer IDs
```

## SQL Concepts

* Subquery
* `AVG()`
* `WHERE`
* `DISTINCT`

---

# 6️⃣ Employees With Above-Average Salary

```sql
SELECT *
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

## Purpose

Identifies employees whose salary is above the average employee salary.

The query first calculates:

```text
Average Employee Salary
```

Then compares every employee's salary against that value.

## Business Use Case

This type of analysis can help HR teams examine:

* Salary distribution
* Above-average employees
* Compensation patterns

---

# 📅 Date Transformation & Analysis

The project also demonstrates several useful SQL date functions.

---

# 7️⃣ Extract Year and Month

```sql
SELECT
    OrderID,
    YEAR(OrderDate) AS OrderYear,
    MONTH(OrderDate) AS OrderMonth
FROM Orders;
```

## Purpose

Extracts separate year and month values from the order date.

Example:

```text
2023-07-05
    ↓
Year  = 2023
Month = 7
```

## Functions Used

```text
YEAR()
MONTH()
```

These functions are useful for:

* Monthly analysis
* Yearly analysis
* Time-based reporting
* Trend analysis

---

# 8️⃣ Date Difference

```sql
SELECT
    OrderID,
    OrderDate,
    DATEDIFF(CURDATE(), OrderDate) AS DaysDifference
FROM Orders;
```

## Purpose

Calculates the number of days between the order date and the current date.

### Functions Used

```text
CURDATE()
DATEDIFF()
```

Concept:

```text
Current Date
     -
Order Date
     =
Number of Days
```

Because `CURDATE()` is dynamic, the result changes depending on the date when the query is executed.

---

# 9️⃣ Format Date

```sql
SELECT
    OrderID,
    DATE_FORMAT(OrderDate, '%d-%M-%Y') AS FormattedDate
FROM Orders;
```

## Purpose

Converts the original date into a more readable format.

Example:

```text
2023-07-01
      ↓
01-July-2023
```

## Function Used

```text
DATE_FORMAT()
```

This is useful when preparing SQL output for reports or users.

---

# 🔤 String Transformation

SQL can also be used to clean and transform text data.

---

# 🔟 Concatenate First Name and Last Name

```sql
SELECT
    CONCAT(FirstName, ' ', LastName) AS FullName
FROM Customers;
```

## Purpose

Combines separate first-name and last-name columns into a single full-name column.

Example:

```text
John
+
Doe
↓
John Doe
```

## Function

```text
CONCAT()
```

This is commonly used when preparing customer or employee reports.

---

# 1️⃣1️⃣ Replace String

```sql
SELECT
    REPLACE(FirstName, 'John', 'Jonathan') AS UpdatedName
FROM Customers;
```

## Purpose

Replaces a specific text value with another value.

Example:

```text
John
 ↓
Jonathan
```

## Function

```text
REPLACE()
```

This demonstrates basic text transformation using SQL.

---

# 1️⃣2️⃣ Uppercase and Lowercase

```sql
SELECT
    UPPER(FirstName) AS FirstNameUpper,
    LOWER(LastName) AS LastNameLower
FROM Customers;
```

## Purpose

Transforms text into uppercase or lowercase.

Example:

```text
John → JOHN
Doe  → doe
```

## Functions

```text
UPPER()
LOWER()
```

These functions can be useful when standardizing text data.

---

# 1️⃣3️⃣ TRIM Email

```sql
SELECT
    TRIM(Email) AS CleanEmail
FROM Customers;
```

## Purpose

Removes unwanted spaces from the beginning and end of text.

Concept:

```text
"  john@example.com  "
          ↓
"john@example.com"
```

## Function

```text
TRIM()
```

This is a common data-cleaning operation.

---

# 📈 Window Functions

The project also demonstrates SQL window functions.

Window functions allow calculations across related rows while keeping individual records visible.

---

# 1️⃣4️⃣ Running Total

```sql
SELECT
    OrderID,
    CustomerID,
    TotalAmount,
    SUM(TotalAmount)
        OVER (ORDER BY OrderID) AS RunningTotal
FROM Orders;
```

## Purpose

Calculates a cumulative total of order amounts based on `OrderID`.

Concept:

```text
Order 101 → $150.50
Running Total → $150.50

Order 102 → $200.75
Running Total → $351.25

Order 103 → $300.00
Running Total → $651.25
```

The running total continues to increase with each order.

## SQL Concepts

* `SUM()`
* `OVER()`
* `ORDER BY`
* Window Function

---

# 🏆 1️⃣5️⃣ Rank Orders

```sql
SELECT
    OrderID,
    TotalAmount,
    RANK() OVER (
        ORDER BY TotalAmount DESC
    ) AS OrderRank
FROM Orders;
```

## Purpose

Ranks orders from highest order amount to lowest order amount.

Concept:

```text
Highest Amount
      ↓
Rank 1

Second Highest
      ↓
Rank 2

Third Highest
      ↓
Rank 3
```

## Function

```text
RANK()
```

This is useful for:

* Top orders
* Customer ranking
* Product ranking
* Sales analysis
* Performance analysis

---

# 🎁 1️⃣6️⃣ Discount Based on Order Amount

```sql
SELECT
    OrderID,
    TotalAmount,
    CASE
        WHEN TotalAmount > 1000 THEN '10% Discount'
        WHEN TotalAmount > 500 THEN '5% Discount'
        ELSE 'No Discount'
    END AS DiscountOffer
FROM Orders;
```

## Purpose

Creates a discount category based on order amount.

### Business Logic

```text
TotalAmount > 1000
       ↓
10% Discount

TotalAmount > 500
       ↓
5% Discount

Otherwise
       ↓
No Discount
```

## SQL Concept

```text
CASE
WHEN
THEN
ELSE
END
```

This demonstrates how SQL can implement business rules directly inside a query.

---

# 💰 1️⃣7️⃣ Employee Salary Category

```sql
SELECT
    EmployeeID,
    FirstName,
    Salary,
    CASE
        WHEN Salary >= 70000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END AS SalaryCategory
FROM Employees;
```

## Purpose

Classifies employees into salary categories.

### Classification Logic

```text
Salary >= 70,000
       ↓
     High

Salary >= 50,000
       ↓
    Medium

Salary < 50,000
       ↓
      Low
```

This creates a derived analytical column without modifying the original table.

---

# 🧠 SQL Functions Used

| Function / Feature | Purpose                   |
| ------------------ | ------------------------- |
| `AVG()`            | Calculate average         |
| `SUM()`            | Calculate totals          |
| `RANK()`           | Rank records              |
| `YEAR()`           | Extract year              |
| `MONTH()`          | Extract month             |
| `DATEDIFF()`       | Calculate date difference |
| `CURDATE()`        | Get current date          |
| `DATE_FORMAT()`    | Format dates              |
| `CONCAT()`         | Combine strings           |
| `REPLACE()`        | Replace text              |
| `UPPER()`          | Convert text to uppercase |
| `LOWER()`          | Convert text to lowercase |
| `TRIM()`           | Remove extra spaces       |
| `CASE`             | Apply conditional logic   |
| `DISTINCT`         | Remove duplicates         |
| `UNION`            | Combine result sets       |

---

# 📚 SQL Concepts Demonstrated

## Database Fundamentals

* Database creation
* Database selection
* Table creation
* Primary Keys
* Foreign Keys
* Relational database structure

## Data Manipulation

* `INSERT`
* `SELECT`

## Data Transformation

* String transformation
* Date transformation
* Conditional transformation
* Derived columns

## Data Analysis

* Average calculations
* Above-average analysis
* Running totals
* Ranking
* Date analysis

## Advanced SQL

* Subqueries
* Window functions
* `CASE` expressions
* Multiple JOIN types
* FULL OUTER JOIN simulation

---

# 🔍 JOIN Comparison

| JOIN                  | Main Purpose                              |
| --------------------- | ----------------------------------------- |
| INNER JOIN            | Returns matching records                  |
| LEFT JOIN             | All left records + matching right records |
| RIGHT JOIN            | All right records + matching left records |
| FULL OUTER JOIN       | All records from both sides               |
| UNION-based FULL JOIN | Simulates FULL OUTER JOIN in MySQL        |

### Visual Concept

```text
INNER JOIN
Only matching data

Customers ∩ Orders


LEFT JOIN
All Customers
+ matching Orders


RIGHT JOIN
All Orders
+ matching Customers


FULL OUTER JOIN
All Customers
+ All Orders
```

---

# 💼 Business Questions Answered

This project demonstrates how SQL can answer real-world business questions.

## Customer Analysis

* Which customers have placed orders?
* Which customers have multiple orders?
* Which customers have above-average order values?
* What are the customers' cities?
* How can customer names be standardized?

## Order Analysis

* What is each order's date?
* What year and month was the order placed?
* How many days have passed since the order?
* Which orders have the highest values?
* What is the cumulative order value?
* Which orders qualify for discounts?

## Employee Analysis

* Which employees earn above the average salary?
* How can employees be categorized by salary?
* Which departments do employees belong to?
* What are the employee hiring dates?

---

# 📊 Analytical Workflow

The project follows a practical SQL data-analysis workflow:

```text
              RAW DATABASE
                   │
                   ▼
          ┌─────────────────┐
          │   Data Storage   │
          └────────┬────────┘
                   │
                   ▼
              SQL JOINs
                   │
                   ▼
             Data Filtering
                   │
                   ▼
          Data Transformation
                   │
          ┌────────┼────────┐
          ▼        ▼        ▼
        Dates   Strings   Numbers
          │        │        │
          └────────┼────────┘
                   ▼
             SQL Analysis
                   │
          ┌────────┼────────┐
          ▼        ▼        ▼
       Ranking  Running   Categories
                Total
                   │
                   ▼
              Final Report
```

---

# 📈 Example Analytical Pipeline

A typical analysis can follow this pattern:

```text
Customers
    +
Orders
    ↓
INNER JOIN
    ↓
Customer Order Dataset
    ↓
Calculate Average
    ↓
Identify Above-Average Orders
    ↓
Rank Orders
    ↓
Calculate Running Total
    ↓
Generate Business Insights
```

---

# 🧹 Data Cleaning Techniques

The project includes basic SQL-based data cleaning techniques.

### Text Cleaning

```sql
TRIM()
UPPER()
LOWER()
REPLACE()
CONCAT()
```

### Date Transformation

```sql
YEAR()
MONTH()
DATE_FORMAT()
DATEDIFF()
```

These operations demonstrate how SQL can prepare raw database information before further analysis.

---

# 📊 Data Transformation Examples

## Name Transformation

```text
John + Doe
   ↓
John Doe
```

## Text Standardization

```text
john
   ↓
JOHN
```

or:

```text
Doe
   ↓
doe
```

## Date Transformation

```text
2023-07-01
    ↓
01-July-2023
```

## Salary Classification

```text
Salary
   ↓
CASE
   ↓
High / Medium / Low
```

## Order Ranking

```text
Order Amount
     ↓
RANK()
     ↓
1, 2, 3, ...
```

---

# 🧪 Testing & Validation

The project includes queries to display all records from each table.

```sql
SELECT * FROM Customers;

SELECT * FROM Orders;

SELECT * FROM Employees;
```

These queries can be used to verify that the tables were created successfully and the sample data was inserted correctly.

---

# ▶️ How to Run the Project

## Step 1 — Install MySQL

Install:

* MySQL Server
* MySQL Workbench or another MySQL-compatible SQL client

## Step 2 — Open the SQL File

Open the project SQL file in MySQL Workbench.

Example:

```text
DataTransformerProject.sql
```

## Step 3 — Create Database

Run:

```sql
CREATE DATABASE DataTransformerProject;

USE DataTransformerProject;
```

## Step 4 — Create Tables

Run the `CREATE TABLE` statements.

## Step 5 — Insert Data

Run all `INSERT INTO` statements.

## Step 6 — Execute Analysis Queries

Run the queries one by one and inspect the results.

## Step 7 — Verify Tables

Run:

```sql
SELECT * FROM Customers;
SELECT * FROM Orders;
SELECT * FROM Employees;
```

---

# 📂 Recommended GitHub Project Structure

```text
Data-Transformer-Project/
│
├── DataTransformerProject.sql
│
├── README.md
│
└── Screenshots/
    ├── database.png
    ├── customers.png
    ├── orders.png
    ├── employees.png
    ├── joins.png
    ├── subqueries.png
    └── window-functions.png
```

---

# 🚀 Future Improvements

This project can be expanded into a larger real-world data analytics project.

Possible improvements include:

### Customer Analysis

* Customer lifetime value
* Total spending per customer
* Number of orders per customer
* Customer segmentation
* Repeat customer analysis

### Order Analysis

* Monthly sales
* Yearly sales
* Average order value
* Maximum order value
* Minimum order value
* Sales by city
* Sales growth

### Employee Analysis

* Average salary by department
* Maximum salary by department
* Minimum salary by department
* Employee tenure
* Department-wise employee count
* Salary distribution

### Advanced SQL

* CTEs
* More window functions
* `ROW_NUMBER()`
* `DENSE_RANK()`
* `LAG()`
* `LEAD()`
* Stored Procedures
* Views
* Indexing
* Query optimization

### Visualization

The SQL database can also be connected to:

```text
MySQL
   ↓
Python / Excel / Power BI
   ↓
Data Analysis
   ↓
Dashboard
```

---

# 🎓 Learning Outcomes

After completing this project, the following practical skills are demonstrated:

* Relational database understanding
* MySQL database creation
* Table design
* Primary and foreign keys
* Data insertion
* SQL JOINs
* Subqueries
* Aggregate functions
* Date functions
* String functions
* Data cleaning
* Conditional logic
* Window functions
* Running totals
* Ranking
* Business-rule implementation
* Analytical SQL
* Report-oriented SQL queries

---

# 💼 Data Analyst Skills Demonstrated

This project is particularly useful for demonstrating SQL skills required in a **Data Analyst** workflow.

```text
SQL
│
├── Database Design
├── Data Retrieval
├── Data Cleaning
├── Data Transformation
├── Data Joining
├── Data Filtering
├── Data Aggregation
├── Date Analysis
├── String Transformation
├── Business Logic
├── Ranking
├── Running Totals
├── Subqueries
└── Analytical Reporting
```

---

# ⭐ Project Highlights

### 🔹 Relational Database

Three structured tables represent customers, orders, and employees.

### 🔹 Multiple JOIN Types

The project demonstrates:

```text
INNER JOIN
LEFT JOIN
RIGHT JOIN
FULL OUTER JOIN simulation
```

### 🔹 Advanced Filtering

Subqueries are used to compare records against calculated averages.

### 🔹 Data Cleaning

Text transformation functions such as `TRIM()`, `UPPER()`, `LOWER()` and `REPLACE()` are demonstrated.

### 🔹 Date Analysis

The project uses year, month, date difference and date formatting operations.

### 🔹 Window Functions

Running totals and ranking are implemented using SQL window functions.

### 🔹 Business Logic

`CASE` statements convert numerical values into meaningful business categories such as:

```text
Discount Offer
Salary Category
```

---

# 📌 Complete Project Summary

**Data Transformer Project** is a practical MySQL project focused on transforming, combining, cleaning and analyzing relational data using SQL.

The project works with **Customers, Orders and Employees** datasets and demonstrates a complete range of SQL techniques, from basic database creation and data retrieval to advanced analytical operations.

The project includes **INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN simulation, subqueries, aggregate functions, date functions, string functions, data-cleaning functions, window functions, running totals, ranking and CASE-based business logic**.

Through these queries, raw database records are converted into useful analytical information such as **above-average orders, above-average salaries, formatted dates, customer names, cumulative order totals, order rankings, discount categories and salary classifications**.

This project provides hands-on practice in using SQL as a **data transformation and data analysis tool**, making it suitable for a SQL/Data Analyst portfolio.

---

# 🏆 Skills & Technologies

```text
MySQL
SQL
Relational Database
Data Transformation
Data Cleaning
Data Analysis
JOINs
Subqueries
Aggregate Functions
Date Functions
String Functions
Window Functions
CASE Statements
Business Logic
Analytical Reporting
```

---

# 👨‍💻 Author

**Hardik Kumawat**

Aspiring **Data Analyst**

### Skills

* SQL
* Excel
* Power BI
* Python
* Data Analytics
* Data Visualization
* Business Analytics

---

# 📌 Project Status

```text
Project Status : Completed ✅
Database       : MySQL
Project Type   : SQL / Data Transformation / Data Analytics
Level          : Beginner → Advanced SQL
```

---

## ⭐ Final Note

This project demonstrates the practical use of SQL to move from:

```text
RAW DATA
   ↓
RELATIONAL DATA
   ↓
JOIN
   ↓
CLEAN
   ↓
TRANSFORM
   ↓
CALCULATE
   ↓
CLASSIFY
   ↓
ANALYZE
   ↓
BUSINESS INFORMATION
```

**Built with MySQL & SQL 📊💻**

