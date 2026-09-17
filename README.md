# 💰 Student Expense Tracker & Budget Analyzer

A simple and efficient **Student Expense Tracker & Budget Analyzer** built using **Python, SQLite, and Streamlit**. The system helps students record daily expenses, organize them into categories, set monthly budgets, and analyze their spending patterns through an interactive dashboard.

The project uses a **relational SQLite database** with proper tables, primary keys, foreign keys, and SQL-based analytics to maintain and analyze expense data over time.

---

## 🎯 Overview

Managing daily expenses as a student can be difficult, especially when spending is spread across food, travel, education, shopping, entertainment, and other categories.

This project provides a centralized system to:

* Record daily expenses
* Categorize expenses
* Create, update, and delete categories
* Set monthly budgets
* Track budget utilization
* Analyze monthly and category-wise spending
* Identify spending trends
* Store data persistently using SQLite
* Visualize financial information through an interactive dashboard

---

## ✨ Key Features

### 📝 Daily Expense Logging

Students can record their expenses with details such as:

* Expense amount
* Expense category
* Date
* Description
* Payment method

The system validates the entered values before storing them in the database.

---

### 🗂️ Category Management

Expenses can be organized into customizable categories such as:

* Food
* Travel
* Education
* Shopping
* Entertainment
* Bills
* Healthcare
* Other

Users can:

* Add categories
* Update categories
* Delete categories
* View available categories

---

### 💰 Monthly Budget Management

Students can define a monthly spending limit.

The system calculates:

* Total monthly budget
* Total amount spent
* Remaining budget
* Budget utilization percentage
* Budget status

Example:

```text
Monthly Budget       : ₹10,000
Total Spent          : ₹7,500
Remaining Budget     : ₹2,500
Budget Utilization   : 75%
```

---

### 📊 Expense Analytics

The dashboard provides useful insights such as:

* Monthly expenditure
* Category-wise expenditure
* Daily spending
* Budget utilization
* Spending trends
* Recent transactions

Interactive charts make it easier to understand spending behavior.

---

## 🗄️ Database Design

The project uses **SQLite** as a lightweight relational database.

### ER Model

```text
STUDENT
   |
   | 1
   |
   | M
EXPENSE
   |
   | M
   |
   | 1
CATEGORY


STUDENT
   |
   | 1
   |
   | M
BUDGET
```

### Database Tables

#### STUDENT

| Column     | Type    | Description   |
| ---------- | ------- | ------------- |
| student_id | INTEGER | Primary Key   |
| name       | TEXT    | Student name  |
| email      | TEXT    | Student email |

#### CATEGORY

| Column        | Type    | Description          |
| ------------- | ------- | -------------------- |
| category_id   | INTEGER | Primary Key          |
| category_name | TEXT    | Expense category     |
| description   | TEXT    | Category description |

#### EXPENSE

| Column         | Type    | Description         |
| -------------- | ------- | ------------------- |
| expense_id     | INTEGER | Primary Key         |
| student_id     | INTEGER | Foreign Key         |
| category_id    | INTEGER | Foreign Key         |
| amount         | REAL    | Expense amount      |
| expense_date   | DATE    | Date of expense     |
| description    | TEXT    | Expense description |
| payment_method | TEXT    | Cash/UPI/Card/etc.  |

#### BUDGET

| Column     | Type    | Description    |
| ---------- | ------- | -------------- |
| budget_id  | INTEGER | Primary Key    |
| student_id | INTEGER | Foreign Key    |
| month      | INTEGER | Budget month   |
| year       | INTEGER | Budget year    |
| amount     | REAL    | Monthly budget |

---

## 📈 Analytics

The system generates analytics from the stored expense data.

### Monthly Spending

Shows the total amount spent during each month.

### Category-wise Spending

Shows which categories contribute the most to total expenditure.

### Daily Spending

Tracks expenditure on a day-to-day basis.

### Budget Analysis

Compares the student's:

```text
Budget
   ↓
Actual Spending
   ↓
Remaining Amount
   ↓
Utilization %
```

### Spending Trends

Historical expense data can be analyzed to identify changes in spending patterns over time.

---

## 🖥️ Dashboard

The Streamlit dashboard provides an interactive interface for managing and analyzing expenses.

### Dashboard Components

* Total Expenses
* Monthly Budget
* Remaining Budget
* Budget Utilization
* Monthly Expense Chart
* Category-wise Expense Chart
* Daily Spending Chart
* Expense Transaction Table

Users can filter expenses by:

* Date
* Category
* Payment method
* Month

---

## 🛠️ Technology Stack

### Programming Language

* **Python**

### Database

* **SQLite**

### Data Processing

* **Pandas**

### Dashboard

* **Streamlit**

### Data Visualization

* **Plotly**

### Development Tools

* VS Code
* Jupyter Notebook
* Git & GitHub

---

## 📂 Project Structure

```text
Student-Expense-Tracker/
│
├── data/
│   └── sample_expenses.csv
│
├── database/
│   ├── database.py
│   └── expense_tracker.db
│
├── scripts/
│   ├── create_database.py
│   ├── seed_data.py
│   └── analytics.py
│
├── streamlit_app.py
│
├── views.sql
│
├── requirements.txt
│
└── README.md
```

---

## ⚙️ Functional Modules

The project is divided into three major functional modules.

### 1. Expense Management

Handles daily expense records.

```text
Add Expense
     ↓
Validate Input
     ↓
Store in SQLite
     ↓
View / Update / Delete
```

### 2. Category Management

Handles expense categorization.

```text
Create Category
       ↓
Assign Category
       ↓
Update / Delete Category
```

### 3. Monthly Budget Analytics

Analyzes spending against the defined budget.

```text
Monthly Budget
       ↓
Calculate Total Spending
       ↓
Compare Budget vs Actual
       ↓
Generate Analytics
       ↓
Display Dashboard
```

---

## 🔐 Error Handling & Validation

The application handles invalid inputs such as:

* Negative expense amounts
* Zero-value expenses
* Invalid dates
* Missing category
* Invalid budget values
* Duplicate categories
* Missing student records

Example validation:

```python
if amount <= 0:
    raise ValueError("Expense amount must be greater than zero.")
```

Database operations also use proper exception handling to prevent application crashes.

---

## ⚡ Non-Functional Requirements

### Maintainability

The project follows a modular structure with separate components for:

* Database operations
* Expense management
* Category management
* Budget calculations
* Analytics
* UI

This makes the system easier to modify and maintain.

### Resource Efficiency

SQLite is used because it is lightweight and does not require a separate database server.

### Scalability

The relational database design allows large numbers of expense records to be stored and analyzed over time.

Indexes and SQL queries can be added as the dataset grows.

### Reliability

Input validation and database error handling reduce incorrect or inconsistent records.

---

## 📊 Example Analytics

Example monthly report:

```text
-----------------------------------------
        MONTHLY EXPENSE REPORT
-----------------------------------------

Month              : September 2026
Budget             : ₹15,000
Total Spent        : ₹11,250
Remaining Budget   : ₹3,750
Utilization        : 75%

Top Categories:

Food               : ₹4,000
Travel             : ₹2,500
Education          : ₹2,000
Entertainment      : ₹1,500
Others             : ₹1,250
-----------------------------------------
```

---

## 🌟 Future Enhancements

The project can be extended with:

* Student authentication
* Multiple student accounts
* Recurring expenses
* Income tracking
* Savings goals
* Budget alerts
* Monthly PDF reports
* CSV/Excel export
* Advanced spending predictions
* Machine-learning based expense analysis
* Cloud database integration
* Deployment using Streamlit Cloud or AWS

---

## 🎓 Applications

This system can be used for:

* Students managing personal expenses
* College financial-management projects
* Budget planning
* Financial literacy applications
* Academic database/DBMS projects
* Expense pattern analysis

---

## 🏆 Project Outcomes

The project demonstrates the implementation of:

* ✅ CRUD operations
* ✅ Relational database design
* ✅ ER diagram and schema design
* ✅ Primary and foreign keys
* ✅ SQLite database
* ✅ Data validation
* ✅ Monthly budget calculations
* ✅ SQL-based analytics
* ✅ Data visualization
* ✅ Interactive Streamlit dashboard
* ✅ Modular and maintainable code

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/student-expense-tracker.git

cd student-expense-tracker
```

### 2. Create Virtual Environment

```bash
python -m venv venv
```

### 3. Activate Environment

**Windows:**

```bash
venv\Scripts\activate
```

**Linux / macOS:**

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Initialize Database

```bash
python scripts/create_database.py
```

### 6. Add Sample Data

```bash
python scripts/seed_data.py
```

### 7. Start the Application

```bash
streamlit run streamlit_app.py
```

The dashboard will be available at:

```text
http://localhost:8501
```

---

## 📌 Conclusion

**Student Expense Tracker & Budget Analyzer** provides a complete solution for recording, managing, and analyzing student expenses.

By combining **Python, SQLite, SQL, Pandas, and Streamlit**, the project demonstrates database management, CRUD operations, data processing, analytics, visualization, and software maintainability in a single real-world application.

```

Ye version original repo ke **finance-tracking concept ko copy-paste nahi karta**, balki tumhare assignment ke exact requirements—**Daily Expense Logging + Category CRUD + Monthly Budget Analytics + ER/Schema + Error Handling + Maintainability/Scalability**—ke around structure karta hai.

Agar tum original repository ko actually modify kar rahe ho, toh next step mein main **iske liye complete code file-by-file rewrite** kar sakta hoon: `database.py → CRUD → budget analytics → Streamlit dashboard → requirements.txt`.
```
