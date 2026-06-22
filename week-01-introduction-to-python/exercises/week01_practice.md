# Week 1 — Practice Exercises

> Self-practice problems based on session concepts. Try each one before looking at the answer.

---

## Section 1: Variables & Operators

**Q1.** Create a variable `loan_amount` with value `50000` and a variable `interest_rate` with value `0.085`. Calculate the interest owed after 1 year and store it in a variable called `interest_owed`. Print it.

<details>
<summary>Answer</summary>

```python
loan_amount = 50000
interest_rate = 0.085
interest_owed = loan_amount * interest_rate
print("Interest owed:", interest_owed)
# Output: Interest owed: 4250.0
```
</details>

---

**Q2.** What is the output of `7 % 3`? What does `%` do?

<details>
<summary>Answer</summary>

```python
7 % 3  # Output: 1
```
`%` is the modulus operator — it returns the **remainder** of a division. `7 / 3 = 2` with a remainder of `1`.
</details>

---

## Section 2: Lists

**Q3.** Using the Cred-Pay data, write code to find the credit score of the customer with `cid = 'cid-0003'`.

```python
cid = ['cid-0001', 'cid-0002', 'cid-0003', 'cid-0004', 'cid-0005']
credit_score = [650, 723, 581, 462, 773]
```

<details>
<summary>Answer</summary>

```python
pos = cid.index('cid-0003')
print("Credit score of cid-0003:", credit_score[pos])
# Output: Credit score of cid-0003: 581
```
</details>

---

**Q4.** Given `my_list = [1, "two", 3.5, "four", 5, 6.0, "seven", 8.2]`, which slice retrieves the two middle elements (`"four"` and `5`)?

<details>
<summary>Answer</summary>

```python
my_list = [1, "two", 3.5, "four", 5, 6.0, "seven", 8.2]

# Index positions: 0   1      2      3       4   5      6       7
# Middle elements: "four" (index 3) and 5 (index 4)

my_list[3:5]     # ✅ ['four', 5]
my_list[-5:-3]   # ✅ also works — negative indexing
```
`my_list[4:6]` gives `[5, 6.0]` — not the middle pair.  
`my_list[-4:-6]` gives `[]` — empty, because step is wrong direction.
</details>

---

**Q5.** Why does updating `customer_2[2] = 29` raise an error if `customer_2 = ("cid-0002", 723, 28, 'no-debt', 2)`?

<details>
<summary>Answer</summary>

`customer_2` is a **Tuple**, which is immutable. Tuples cannot be changed after creation. This raises a `TypeError: 'tuple' object does not support item assignment`.  
If you need to update values, use a **List** instead.
</details>

---

## Section 3: Conditional Statements

**Q6.** Write a function `loan_eligibility(score)` that returns:
- `"Eligible for premium loan"` if score > 750
- `"Eligible for standard loan"` if score > 600
- `"Not eligible for loan"` otherwise

Test it with scores 800, 680, and 540.

<details>
<summary>Answer</summary>

```python
def loan_eligibility(score):
    if score > 750:
        return "Eligible for premium loan"
    elif score > 600:
        return "Eligible for standard loan"
    else:
        return "Not eligible for loan"

print(loan_eligibility(800))  # Eligible for premium loan
print(loan_eligibility(680))  # Eligible for standard loan
print(loan_eligibility(540))  # Not eligible for loan
```
</details>

---

**Q7.** What is the correct Python keyword to check: `prec_on_time[i] < 0.4 ___ no_of_existing_credit_cards[i] > 2` (both conditions must be true)?

<details>
<summary>Answer</summary>

```python
if prec_on_time[i] < 0.4 and no_of_existing_credit_cards[i] > 2:
```
Python uses lowercase `and` / `or` / `not`.  
`AND`, `&`, `|` are NOT correct here (`&` and `|` are bitwise operators, not logical ones for if statements).
</details>

---

## Section 4: Loops

**Q8.** Using the Cred-Pay data, write a loop to count how many customers have a credit score greater than 700.

```python
credit_score = [650, 723, 581, 462, 773]
```

<details>
<summary>Answer</summary>

```python
count = 0
for i in range(0, len(credit_score)):
    if credit_score[i] > 700:
        count += 1
print("Customers with credit score > 700:", count)
# Output: 2
```
</details>

---

**Q9.** What is the output of this code?

```python
pending_loans = 3
while pending_loans > 0:
    print("Processing loan...")
    pending_loans -= 1
else:
    print("All loans processed!")
```

<details>
<summary>Answer</summary>

```
Processing loan...
Processing loan...
Processing loan...
All loans processed!
```
The `while` loop runs 3 times (for `pending_loans = 3, 2, 1`). When it becomes `0`, the condition is `False` and the `else` block runs.
</details>

---

## Section 5: Functions

**Q10.** What is the difference between these two functions? What does each print when called as `var = customer_age("cid-0001"); print(var)`?

```python
# Function 1
def customer_age_v1(c_id):
    idx = cid.index(c_id)
    print(age_of_customer[idx])

# Function 2
def customer_age_v2(c_id):
    idx = cid.index(c_id)
    return age_of_customer[idx]
```

<details>
<summary>Answer</summary>

```python
# Function 1 — uses print inside
var = customer_age_v1("cid-0001")
# → prints 25 (inside the function)
print(var)
# → prints None  ← because the function returned nothing

# Function 2 — uses return
var = customer_age_v2("cid-0001")
# → nothing printed yet
print(var)
# → prints 25  ← the returned value
```

**Key difference:** `print()` displays output but returns `None`. `return` passes the value back to the caller so it can be stored or used.
</details>

---

## Bonus Challenge

**Q11.** Write a function `update_credit_scores(cid_list, credit_scores, on_time_pct)` that:
- Increases the credit score by 2% if `on_time_pct > 0.7`
- Decreases the credit score by 2% if `on_time_pct < 0.4`
- Leaves it unchanged otherwise

Return the updated credit score list and print a message for each customer.

<details>
<summary>Answer</summary>

```python
def update_credit_scores(cid_list, credit_scores, on_time_pct):
    updated = credit_scores.copy()
    for i in range(len(cid_list)):
        if on_time_pct[i] > 0.7:
            updated[i] = round(updated[i] * 1.02)
            print(f"Credit score INCREASED for {cid_list[i]}: {credit_scores[i]} → {updated[i]}")
        elif on_time_pct[i] < 0.4:
            updated[i] = round(updated[i] * 0.98)
            print(f"Credit score DECREASED for {cid_list[i]}: {credit_scores[i]} → {updated[i]}")
        else:
            print(f"Credit score UNCHANGED for {cid_list[i]}: {updated[i]}")
    return updated

# Test
cid = ['cid-0001', 'cid-0002', 'cid-0003', 'cid-0004', 'cid-0005']
credit_score = [650, 723, 581, 462, 773]
prec_on_time = [0.62, 0.78, 0.20, 0.32, 0.85]

new_scores = update_credit_scores(cid, credit_score, prec_on_time)
print("\nFinal scores:", new_scores)
```
</details>
