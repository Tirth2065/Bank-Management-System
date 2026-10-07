# 🏦 Bank Management System

A desktop-based **Bank Management System** developed using **Java Swing** and **MySQL** with **JDBC**. The application simulates basic banking and ATM operations such as customer registration, login authentication, deposits, withdrawals, fast cash, balance enquiry, mini statements, and PIN management.

---

## 📌 Project Overview

The **Bank Management System** is designed to provide a simple graphical interface for managing basic banking operations.

The system provides a multi-step customer registration process, generates a card number and PIN for new customers, stores customer and transaction information in a MySQL database, and allows authenticated users to perform different banking operations.

### 🔑 Main Technologies

- **Java**
- **Java Swing / AWT**
- **MySQL**
- **JDBC**
- **IntelliJ IDEA / Eclipse / VS Code**
- **MySQL Workbench**

---

## ✨ Features

### 👤 Customer Registration

The registration process is divided into three steps:

#### Page 1 – Personal Details

- Name
- Father's Name
- Date of Birth
- Gender
- Email
- Marital Status
- Address
- City
- State
- PIN Code

#### Page 2 – Additional Details

- Religion
- Category
- Income
- Education
- Occupation
- PAN Number
- Aadhaar Number
- Senior Citizen Status
- Existing Account Status

#### Page 3 – Account Details

- Account Type
  - Saving Account
  - Fixed Deposit Account
  - Current Account
  - Recurring Deposit Account
- Banking Services
  - ATM Card
  - Internet Banking
  - Mobile Banking
  - Email Alerts
  - Cheque Book
  - E-Statement
- Automatic Card Number Generation
- Automatic 4-Digit PIN Generation

---

## 🔐 Login & Authentication

Users can log in using:

- Card Number
- PIN

The credentials are verified against the MySQL `login` table before accessing the main banking dashboard.

---

## 💰 Banking Operations

### Deposit

Users can enter an amount and deposit money into their account.

The transaction is stored in the `bank` table with:

```text
PIN
Date
Transaction Type
Amount
```

---

### 💸 Cash Withdrawal

Users can enter a custom withdrawal amount.

Before processing the transaction, the system:

1. Fetches the user's transactions.
2. Calculates the current balance.
3. Checks whether sufficient balance is available.
4. Inserts the withdrawal transaction if the balance is sufficient.

---

### ⚡ Fast Cash

Provides predefined withdrawal amounts such as:

- ₹100
- ₹500
- ₹1,000
- ₹2,000
- ₹5,000
- ₹10,000

This provides a faster alternative to manually entering a withdrawal amount.

---

### 📊 Balance Enquiry

The system calculates the current balance using:

```text
Total Deposits - Total Withdrawals
```

Example:

```text
Deposits     = ₹10,000
Withdrawals  = ₹3,000

Balance      = ₹7,000
```

---

### 📄 Mini Statement

Displays:

- Masked card number
- Transaction date
- Transaction type
- Transaction amount
- Total balance

Example:

```text
Card Number: 1234XXXXXXXX3456

Date          Type          Amount
-----------------------------------
07/10/2026    Deposit       ₹10,000
07/10/2026    Withdrawal     ₹2,000

Total Balance: ₹8,000
```

---

### 🔑 PIN Change

Users can change their existing PIN by entering:

- New PIN
- Confirm PIN

The updated PIN is synchronized across the relevant database tables.

---

## 🏗️ Application Flow

```text
                         BANK MANAGEMENT SYSTEM
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
                 Login                       Signup
                    │                           │
             Card + PIN                 ┌───────┴───────┐
                    │                    │               │
                    │                Signup Page 1   Personal Details
                    │                    │
                    │                Signup Page 2   Additional Details
                    │                    │
                    │                Signup Page 3   Account Details
                    │                    │
                    │                Card + PIN Generation
                    │                    │
                    │                Database Storage
                    │                    │
                    └────────────┬───────┘
                                 │
                           Main ATM Menu
                                 │
             ┌──────────┬────────┼────────┬──────────┐
             │          │        │        │          │
          Deposit   Withdrawal Fast Cash Balance   Mini Statement
             │          │        │        │          │
             └──────────┴────────┴────────┴──────────┘
                                 │
                            PIN Change
```

---

## 🗄️ Database Design

The project uses **MySQL** as the database.

### Main Tables

| Table | Purpose |
|---|---|
| `signup` | Stores personal/customer information |
| `Signuptwo` | Stores additional customer details |
| `signupthree` | Stores account-related information |
| `login` | Stores login-related card and PIN information |
| `bank` | Stores deposit and withdrawal transactions |

### Transaction Structure

The `bank` table stores transactions conceptually as:

```text
PIN
Date
Transaction Type
Amount
```

For example:

```text
1234 | 2026-10-07 | Deposit    | 5000
1234 | 2026-10-07 | Withdrawal | 2000
```

The application calculates:

```text
Balance = Deposits - Withdrawals
```

---

## 🔌 JDBC Architecture

The application communicates with MySQL using JDBC.

```text
Java Application
       │
       ▼
      JDBC
       │
       ▼
DriverManager
       │
       ▼
Connection
       │
       ▼
Statement
       │
       ▼
MySQL Database
       │
       ▼
ResultSet
       │
       ▼
Java Application
```

The `Connn` class is responsible for creating the database connection and SQL statement.

---

## 📁 Project Structure

```text
Bank-Management-System/
│
├── src/
│   └── bank/
│       └── management/
│           └── system/
│
│               ├── Login.java
│               ├── Signup.java
│               ├── Signup2.java
│               ├── Signup3.java
│               │
│               ├── main_Class.java
│               ├── Deposit.java
│               ├── Withdrawl.java
│               ├── FastCash.java
│               ├── BalanceEnquriy.java
│               ├── mini.java
│               ├── Pin.java
│               │
│               └── Connn.java
│
├── icon/
│   └── Application images
│
├── database/
│   └── MySQL database scripts
│
└── README.md
```

> The exact folder structure may vary depending on the IDE and project configuration.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Java** | Core application development |
| **Java Swing** | Graphical User Interface |
| **AWT** | GUI components and event handling |
| **JDBC** | Java-MySQL connectivity |
| **MySQL** | Database management |
| **MySQL Workbench** | Database administration |
| **JCalendar** | Date selection during registration |

---

## ⚙️ How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/Tirth2065/Bank-Management-System.git
```

### 2. Open the Project

Open the project in:

- IntelliJ IDEA
- Eclipse
- VS Code with Java support

### 3. Configure MySQL

Create a MySQL database:

```sql
CREATE DATABASE bankSystem;
```

Import/create the required tables:

```text
signup
Signuptwo
signupthree
login
bank
```

### 4. Configure Database Connection

Open:

```text
Connn.java
```

Update the database credentials:

```java
connection = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/bankSystem",
    "root",
    "YOUR_PASSWORD"
);
```

Replace:

```text
YOUR_PASSWORD
```

with your local MySQL password.

### 5. Add Required Libraries

Make sure the project has the required JDBC and JCalendar dependencies.

### 6. Run the Application

Run:

```text
Login.java
```

The login window will appear.

For a new customer:

```text
Login → Sign Up → Registration → Account Creation
```

For an existing customer:

```text
Login → Card Number + PIN → Main Menu
```

---

## 🔄 Complete User Workflow

```text
New User
   │
   ▼
Signup
   │
   ▼
Personal Details
   │
   ▼
Signup2
   │
   ▼
Additional Details
   │
   ▼
Signup3
   │
   ▼
Account Type + Services
   │
   ▼
Card Number + PIN Generated
   │
   ▼
Database
   │
   ▼
Login
   │
   ▼
Main ATM Menu
   │
   ├── Deposit
   ├── Cash Withdrawal
   ├── Fast Cash
   ├── Mini Statement
   ├── PIN Change
   ├── Balance Enquiry
   └── Exit
```

---

## 🧠 Key OOP Concepts Used

The project demonstrates several Java OOP concepts.

### Inheritance

```java
public class Login extends JFrame
```

Application classes inherit GUI functionality from `JFrame`.

### Interface

```java
implements ActionListener
```

Classes implement `ActionListener` to handle button events.

### Encapsulation

User and transaction information is maintained inside the respective classes.

### Polymorphism

The `actionPerformed()` method is overridden to handle different user actions.

### Object Creation

Different screens are created dynamically:

```java
new Deposit(pin);
new Withdrawl(pin);
new FastCash(pin);
new BalanceEnquriy(pin);
```

---

## 🎯 Learning Outcomes

Through this project, I practiced:

- Java OOP
- Java Swing GUI development
- Event-driven programming
- JDBC and MySQL integration
- SQL queries
- CRUD operations
- Exception handling
- Form validation
- Database-driven application development
- Multi-screen application navigation
- Basic banking transaction logic

---

## 🔒 Security & Production Improvements

This project is developed as an educational banking application. For a production banking system, several improvements would be required.

### Current areas for improvement

- Replace `Statement` with `PreparedStatement`
- Avoid hard-coded database credentials
- Implement secure PIN/password handling
- Add stronger input validation
- Add database transactions for multi-query operations
- Properly close `Connection`, `Statement`, and `ResultSet`
- Add proper exception logging
- Enforce transaction limits at the application level
- Add database constraints for unique card numbers
- Improve concurrent transaction handling
- Separate UI, business logic, and database access layers

### Recommended Architecture

```text
UI Layer
   ↓
Service / Business Layer
   ↓
DAO Layer
   ↓
JDBC
   ↓
MySQL
```

---

## 🚀 Future Enhancements

Possible future improvements include:

- 🔐 Secure authentication and PIN handling
- 💳 Unique and secure card number generation
- 📱 Mobile banking integration
- 📧 Email/SMS transaction notifications
- 📊 Admin dashboard
- 📈 Transaction analytics
- 🧾 PDF transaction statements
- 🔎 Transaction search and filtering
- 💰 Fund transfer between accounts
- 🏦 Multiple account support
- 🔄 Proper transaction management and concurrency control
- 🌐 REST API backend for web/mobile applications

---

## 📸 Screenshots

Add screenshots of the major screens here:

```text
Login Screen
Signup Page 1
Signup Page 2
Signup Page 3
Main ATM Menu
Deposit
Withdrawal
Fast Cash
Balance Enquiry
Mini Statement
PIN Change
```

Example:

```markdown
![Login Screen](screenshots/login.png)
```

---

## 👨‍💻 Developer

**Tirthkumar Gabani**

Computer Engineering  
Government
