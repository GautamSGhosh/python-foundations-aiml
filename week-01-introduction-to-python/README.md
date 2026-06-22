# Week 01 — Python Basics

**Session:** Introduction to Python  
**Program:** AI/ML — UT Austin × Great Learning  

---

## 🎯 Session Objectives

By the end of this week, the goal was to be comfortable with:

- Creating and using **variables** to store different data types
- Using Python **operators** (arithmetic, comparison, membership)
- Working with **data structures** — Lists, Tuples, and Dictionaries
- Writing **conditional statements** (`if`, `elif`, `else`)
- Writing **looping statements** (`for`, `while`)
- Defining and calling **user-defined functions**

---

## 📂 Contents

| File | Description |
|------|-------------|
| [`notes/week01_concepts.md`](./notes/week01_concepts.md) | Concise reference notes on all session concepts |
| [`exercises/week01_practice.md`](./exercises/week01_practice.md) | Self-practice problems with answers |

---

## 🏢 Case Study — Cred-Pay

**Business Context:**  
Cred-Pay is a fintech startup that partners with banks to evaluate credit card applications. As a Data Scientist, the task was to organise customer data and build logic to make it accessible for eligibility decisions.

**Dataset:**

| Customer ID | Credit Score | Age | Debt Status | No. of Existing Credit Cards |
|-------------|-------------|-----|-------------|-------------------------------|
| cid-0001 | 650 | 25 | in-debt | 3 |
| cid-0002 | 723 | 28 | no-debt | 2 |
| cid-0003 | 581 | 38 | no-debt | 4 |
| cid-0004 | 462 | 41 | in-debt | 1 |
| cid-0005 | 773 | 62 | no-debt | 2 |

**What was built:**

1. Stored each feature in Python lists
2. Queried and updated data using list indexing
3. Updated credit scores conditionally using `if-else`
4. Automated score updates for all customers using `for` loops
5. Encapsulated the lookup logic in a reusable `customer_info()` function
6. Consolidated all lists into a dictionary → then converted to a Pandas DataFrame

---

## 💡 Key Takeaways

- Variables in Python are **dynamically typed** — no need to declare a type upfront
- Lists are **mutable** (can be changed); Tuples are **immutable** (fixed once created)
- Dictionaries let you store data as **key-value pairs**, making lookups faster and more readable
- Functions make code **reusable and modular** — one definition, callable with any input
- `for` loops are ideal when iterating over a known sequence; `while` loops run while a condition is true
- **Pandas DataFrames** are the standard structure for tabular data in ML workflows
