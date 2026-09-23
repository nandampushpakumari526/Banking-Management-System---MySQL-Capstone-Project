# 🏦 Banking Database Management System

## 📌 Project Overview

The **Banking Database Management System** is a MySQL-based database project designed to manage banking operations such as branches, customers, accounts, account types, and transactions.

This project demonstrates practical SQL concepts including **DDL, DML, Joins, Subqueries, Aggregate Functions, GROUP BY, HAVING, Views, Stored Procedures, Transactions, and Triggers**.

---

## 🎯 Objectives

* Manage bank branch information.
* Store and manage customer details.
* Maintain different types of bank accounts.
* Track account balances and account status.
* Record customer transactions.
* Maintain data consistency using transactions and triggers.

---

## 🗂️ Database Structure

**Database Name:** `bank`

### Main Tables

### 1. Branches

Stores information about bank branches.

| Column      | Description             |
| ----------- | ----------------------- |
| branch_id   | Unique ID of the branch |
| branch_name | Name of the branch      |
| location    | Branch location         |
| ifsc_code   | IFSC code of the branch |

### 2. Customers

Stores customer information.

| Column        | Description           |
| ------------- | --------------------- |
| customer_id   | Unique customer ID    |
| customer_name | Customer name         |
| phone         | Customer phone number |
| email         | Customer email        |
| address       | Customer address      |

### 3. Account_Types

Stores different types of bank accounts.

| Column            | Description            |
| ----------------- | ---------------------- |
| account_type_id   | Unique account type ID |
| account_type_name | Savings or Current     |

### 4. Accounts

Stores customer account information.

| Column          | Description                |
| --------------- | -------------------------- |
| account_id      | Unique account ID          |
| branch_id       | Reference to Branches      |
| customer_id     | Reference to Customers     |
| account_type_id | Reference to Account_Types |
| account_number  | Bank account number        |
| balance         | Current account balance    |
| opening_date    | Account opening date       |
| status          | Active or Inactive         |

### 5. Transactions

Stores account transaction information.

| Column           | Description                      |
| ---------------- | -------------------------------- |
| transaction_id   | Unique transaction ID            |
| account_id       | Reference to Accounts            |
| transaction_type | Deposit, Withdrawal, or Transfer |
| amount           | Transaction amount               |
| transaction_date | Date of transaction              |
| description      | Transaction description          |

### 6. Transaction_Log

Stores transaction information automatically using a trigger whenever a new transaction is inserted.

---

## 🔗 Table Relationships

The database uses **Primary Keys and Foreign Keys** to establish relationships between tables.

```text
Branches
   │
   └── Accounts
          │
          ├── Customers
          │
          ├── Account_Types
          │
          └── Transactions
```

### Relationships

* One branch can have multiple accounts.
* One customer can have multiple accounts.
* One account belongs to one account type.
* One account can have multiple transactions.

---

## 🛠️ Technologies Used

* **MySQL**
* SQL
* MySQL Workbench

---

## 📚 SQL Concepts Used

* Database and Table Creation
* `CREATE DATABASE`
* `CREATE TABLE`
* `ALTER TABLE`
* `INSERT`
* `UPDATE`
* `SELECT`
* `PRIMARY KEY`
* `FOREIGN KEY`
* `JOIN`
* `LEFT JOIN`
* Subqueries
* Aggregate Functions
* `GROUP BY`
* `HAVING`
* `ORDER BY`
* `LIMIT`
* `CASE`
* String Functions
* Date Functions
* Mathematical Functions
* Views
* Stored Procedures
* Transactions
* `COMMIT`
* `ROLLBACK`
* Triggers

---

## 👁️ View

A view named `active_customers` is created to display active account details along with customer and branch information.

It combines information from:

* `Accounts`
* `Customers`
* `Branches`

Example:

```sql
SELECT * FROM active_customers;
```

---

## ⚙️ Stored Procedures

### Customer Accounts

A stored procedure is designed to display all accounts belonging to a particular customer.

It displays:

* Account Number
* Account Type
* Balance
* Account Status

Example:

```sql
CALL customer_accounts(4);
```

### Account Transactions

A stored procedure is designed to display all transactions for a particular account.

It displays:

* Transaction Type
* Amount
* Transaction Date
* Description

Example:

```sql
CALL account_transactions(101);
```

---

## 🔄 Transactions

The project demonstrates transferring money between two accounts using MySQL transactions.

Example:

```sql
START TRANSACTION;

UPDATE Accounts
SET balance = balance - 10000
WHERE account_id = 101;

UPDATE Accounts
SET balance = balance + 10000
WHERE account_id = 102;

COMMIT;
```

Transactions help maintain **data consistency** when multiple related operations need to be performed together.

`ROLLBACK` can be used to undo changes when required.

---

## 🔔 Triggers

### Transaction Logging Trigger

A trigger is used to automatically record newly inserted transaction details into the `Transaction_Log` table.

The logged information includes:

* Transaction ID
* Account ID
* Transaction Type
* Amount
* Transaction Date

### Negative Balance Validation

Another trigger is designed to prevent an account balance from being updated to a negative value.

This helps maintain business rules and data integrity.

---

## 📁 Project Structure

```text
Banking-Database-Management-System/
│
├── Banking_Database.sql
└── README.md
```

---

## 🚀 How to Run the Project

### Step 1: Install MySQL

Install **MySQL Server** and **MySQL Workbench**.

### Step 2: Open MySQL Workbench

Open the SQL script in MySQL Workbench.

### Step 3: Create the Database

Run:

```sql
CREATE DATABASE bank;
USE bank;
```

### Step 4: Execute the SQL Script

Run the SQL statements in the project file in the correct order.

The script will:

* Create tables
* Add constraints
* Insert sample data
* Create views
* Create stored procedures
* Create triggers
* Demonstrate transactions

---

## 🎓 Key Learning Outcomes

Through this project, I gained practical experience in:

* Designing a relational database.
* Creating tables and relationships.
* Using primary and foreign keys.
* Writing SQL queries.
* Working with multiple-table joins.
* Performing data analysis using aggregate functions.
* Creating views and stored procedures.
* Implementing transactions using `COMMIT` and `ROLLBACK`.
* Using triggers for automation and data validation.
* Understanding database integrity and consistency.

---

## 👩‍💻 Author

**Pushpa Kumari**

B.Tech – Computer Science and Engineering

### Skills Used

`MySQL` `SQL` `Database Management` `Joins` `Subqueries` `Views` `Stored Procedures` `Triggers` `Transactions`

---

## ⭐ Project Highlights

This project demonstrates how SQL can be used to build a practical banking database system while maintaining **data relationships, consistency, integrity, and database management capabilities**.
