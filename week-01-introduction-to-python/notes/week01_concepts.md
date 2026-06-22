# Week 1 — Concept Notes: Python Basics

> Quick-reference notes from the Introduction to Python session.

---

## 1. Variables

- Used to **store any type of data** — integers, floats, strings, booleans, or complex data structures
- Created using the `=` assignment operator
- Values can be **modified** at any time

```python
num = 100        # integer
num = 3.14       # reassigned to float — Python allows this
name = "Gautam"  # string
flag = True      # boolean
```

**Naming rules:**
- Must start with a letter or underscore (`_`)
- Cannot start with a number
- Case-sensitive (`age`, `Age`, `AGE` are all different)
- Only alphanumeric characters and underscores allowed

---

## 2. Operators

| Symbol | Operation | Example | Output |
|--------|-----------|---------|--------|
| `+`, `-` | Addition, Subtraction | `1 + 7` | `8` |
| `*`, `/` | Multiplication, Division | `6 / 2` | `3.0` |
| `%` | Modulus (remainder) | `6 % 2` | `0` |
| `**` | Exponentiation | `2 ** 4` | `16` |
| `==`, `!=`, `>`, `<`, `>=`, `<=` | Comparison | `5 <= 4` | `False` |
| `in`, `not in` | Membership | `5 in [1,2,3,4,5]` | `True` |
| `()` | Grouping | `(1+2) * (2+3)` | `15` |

---

## 3. Data Structures

### 3.1 List
- Ordered, **mutable** (can be modified)
- Defined with square brackets `[]`

```python
cid = ['cid-0001', 'cid-0002', 'cid-0003', 'cid-0004', 'cid-0005']
credit_score = [650, 723, 581, 462, 773]

# Indexing (0-based)
cid[0]      # 'cid-0001'
cid[-1]     # 'cid-0005'  (negative indexing from end)

# Slicing: list[start:end] — end index is EXCLUDED
cid[1:3]    # ['cid-0002', 'cid-0003']

# Finding an element's index
pos = cid.index('cid-0002')  # returns 1

# Updating
debt_status[0] = 'in-debt'
```

### 3.2 Tuple
- Ordered, **immutable** (cannot be modified after creation)
- Defined with parentheses `()`

```python
customer_2 = ("cid-0002", 723, 28, 'no-debt', 2)
# customer_2[2] = 29  ← This raises a TypeError!
```

**When to use tuple vs list:**  
Use tuples for data that should not change (e.g. coordinates, config values).  
Use lists when you need to add/remove/update items.

### 3.3 Dictionary
- Key-value pairs, ordered (Python 3.7+), **mutable**
- Keys must be unique; values can be any type
- Defined with curly braces `{}`

```python
df1 = {
    'cust_id': cid,
    'cred_score': credit_score,
    'age': age_of_customer,
    'debt_status': debt_status,
    'curr_cred_cards': no_of_existing_credit_cards
}

# Accessing values
df1['cust_id']       # full list
df1['cust_id'][2]    # third element

# Iterating key-value pairs
for key, value in df1.items():
    print(key, value[0])
```

---

## 4. Conditional Statements

Used to make decisions based on rules.

```python
# Single condition
if credit_score[0] > 700:
    print("High score")
else:
    print("Low score")

# Multiple conditions
if credit_score[0] > 750:
    status = "Premium"
elif credit_score[0] > 600:
    status = "Standard"
else:
    status = "Not eligible"
```

**Key point:** `elif` runs only if all preceding `if`/`elif` conditions evaluated to `False`.

---

## 5. Looping Statements

### 5.1 `for` loop
- Iterates over a **sequence** (list, range, etc.)

```python
for i in range(0, len(cid)):
    if prec_on_time[i] < 0.4:
        credit_score[i] = round(credit_score[i] * 0.98)
        print('Credit Score updated for', cid[i])
    else:
        print('Credit Score unchanged for', cid[i])
```

### 5.2 `while` loop
- Runs while a **condition** is True

```python
pending_loans = 3
while pending_loans > 0:
    print("Processing loan...")
    pending_loans -= 1
else:
    print("All loans processed!")
```

**`for` vs `while`:**  
Use `for` when iterating a known sequence.  
Use `while` when repeating until a dynamic condition changes.

---

## 6. Functions

A block of reusable instructions that performs a specific task.

```python
# Defining a function
def customer_info(c_id):
    for i in range(0, len(cid)):
        if cid[i] == c_id:
            print('Customer ID:', cid[i])
            print('Credit Score:', credit_score[i])
            print('Age:', age_of_customer[i])
            print('Debt Status:', debt_status[i])
            print('Credit Cards:', no_of_existing_credit_cards[i])

# Calling the function
customer_info('cid-0001')
customer_info('cid-0003')
```

**`return` vs `print` in functions:**

```python
# Using print — returns None when assigned to a variable
def get_age_print(c_id):
    idx = cid.index(c_id)
    print(age_of_customer[idx])

var = get_age_print("cid-0001")   # prints 25
print(var)                         # prints None ← common mistake!

# Using return — actually passes the value back
def get_age_return(c_id):
    idx = cid.index(c_id)
    return age_of_customer[idx]

var = get_age_return("cid-0001")  # var = 25
print(var)                         # prints 25 ✅
```

**Key point:** `return` is **optional** but necessary if you want to use the function's output elsewhere.

---

## 7. Pandas Introduction (Preview)

```python
import pandas as pd

# Convert dictionary to DataFrame
df = pd.DataFrame(df1)

df.head(3)      # first 3 rows
df.tail(3)      # last 3 rows
df.shape        # (rows, columns)
df.info()       # column names, types, null counts
df.describe()   # statistical summary of numeric columns
```

> Full Pandas coverage continues in Week 2.
