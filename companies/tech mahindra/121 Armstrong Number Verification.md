# **Problem 121: Armstrong Number Verification**

**Company:** Tech Mahindra

**Category:** Mathematics / Number Theory

**Difficulty:** Easy-Medium

---

# **Problem Description**

One of the most frequently asked mathematical screening problems in technical interviews involves identifying:

```text id="m2v8zk"
Armstrong Numbers
```

also known as:

```text id="x7m1qa"
Narcissistic Numbers
```

An integer is considered an Armstrong number if the sum of each of its digits raised to the power of the total number of digits equals the original number itself.

Your task is to determine whether a given integer satisfies this mathematical property.

This problem evaluates a candidate’s understanding of:

* iterative digit extraction
* modulo arithmetic
* exponentiation logic
* number decomposition
* efficient integer manipulation without string conversion

Interviewers often expect candidates to solve this using pure arithmetic operations instead of converting the number into a character array or string.

---

# **Task**

Given an integer:

```text id="u3m8qp"
N
```

determine whether it is an Armstrong number.

Return:

```text id="f9m1zk"
YES
```

if the number is an Armstrong number, otherwise return:

```text id="r2m8vx"
NO
```

---

# **Definition of Armstrong Number**

Suppose a number contains:

```text id="n7m2qa"
d
```

digits.

If:

then the number is an Armstrong number.

---

# **Examples**

| Number | Calculation              | Armstrong? |
| ------ | ------------------------ | ---------- |
| 153    | 1³ + 5³ + 3³ = 153       | Yes        |
| 370    | 3³ + 7³ + 0³ = 370       | Yes        |
| 9474   | 9⁴ + 4⁴ + 7⁴ + 4⁴ = 9474 | Yes        |
| 123    | 1³ + 2³ + 3³ = 36        | No         |

---

# **Input Format**

Single line contains integer:

```text id="p4m9xp"
N
```

---

# **Output Format**

Print:

```text id="v1m8zk"
YES
```

if the number is an Armstrong number.

Otherwise print:

```text id="g8m2vx"
NO
```

---

# **Constraints**

* **0 ≤ N ≤ 10¹⁸**

---

# **Sample Input 1**

```text id="x2m1qa"
153
```

---

# **Sample Output 1**

```text id="m9v2zk"
YES
```

---

# **Explanation**

Number of digits:

```text id="k4m8qp"
3
```

Calculation:

Result equals original number.

Thus:

```text id="u7m1xp"
153
```

is an Armstrong number.

---

# **Sample Input 2**

```text id="m4k8qa"
9474
```

---

# **Sample Output 2**

```text id="v8m2zk"
YES
```

---

# **Explanation**

Number of digits:

```text id="x1m9vx"
4
```

Calculation:

Hence:

```text id="z7m2qp"
9474
```

is an Armstrong number.

---

# **Sample Input 3**

```text id="u4m8zk"
123
```

---

# **Sample Output 3**

```text id="k2m1qa"
NO
```

---

# **Explanation**

Number of digits:

```text id="r7m2zk"
3
```

Calculation:

Since:

```text id="u1m8xp"
36 ≠ 123
```

the number is not an Armstrong number.

---

# **Sample Input 4**

```text id="m4k8qa"
0
```

---

# **Sample Output 4**

```text id="v8m2zk"
YES
```

---

# **Explanation**

Digit count:

```text id="x1m9vx"
1
```

Calculation:

Thus:

```text id="z7m2qp"
0
```

is an Armstrong number.

---

# **Why Naive String-Based Approaches Are Discouraged**

Some candidates convert the integer into a string and iterate through characters.

While functionally correct, interviewers often expect:

* arithmetic digit extraction
* modulo operations
* division-based traversal

to demonstrate stronger mathematical reasoning.

---

# **Efficient Mathematical Approach**

The algorithm can be implemented using:

* modulo:

```text id="u4m8zk"
N % 10
```

to extract digits

* integer division:

```text id="k2m1qa"
N / 10
```

to remove processed digits

without converting the integer into a string.

Use:

```text id="r7m2zk"
64-bit integer types
```

for accumulation and exponentiation to safely handle large values.

---

# **Algorithm Overview**

---

## Step 1 — Count Digits

Determine total number of digits:

```text id="u1m8xp"
d
```

using either:

* iterative division
* logarithmic computation

Special case:

```text id="m4k8qa"
N = 0
```

contains exactly:

```text id="v8m2zk"
1
```

digit.

---

## Step 2 — Extract Digits

Repeatedly extract digits using:

```text id="x1m9vx"
digit = temp % 10
```

---

## Step 3 — Compute Power Sum

Accumulate:

for every digit.

Integer exponentiation should be preferred over floating-point:

```text id="z7m2qp"
pow()
```

to avoid precision issues for large values.

---

## Step 4 — Verify Result

If:

```text id="u4m8zk"
sum == N
```

return:

```text id="k2m1qa"
YES
```

otherwise:

```text id="r7m2zk"
NO
```

---

# **Why This Works**

Every digit contributes independently to the Armstrong property.

The algorithm reconstructs the mathematical definition exactly using pure arithmetic operations.

---

# **Recommended Data Structures**

| Structure           | Purpose                        |
| ------------------- | ------------------------------ |
| `Integer Variables` | Digit extraction and summation |

No additional data structures are required.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* `0` as input
* single-digit numbers
* very large integers
* non-Armstrong numbers
* large digit counts
* repeated digits

---

# **Expected Complexity**

## Arithmetic Extraction Solution

### Time Complexity

* **O(d)**

where:

```text id="u1m8xp"
d
```

is the number of digits.

Each digit is processed exactly once.

Assuming fixed-width integer exponentiation is:

```text id="m4k8qa"
O(1)
```

---

### Space Complexity

* **O(1)**

Only constant extra variables are used.

---

# **Example Walkthrough**

Input:

```text id="v8m2zk"
153
```

---

## Count Digits

Digits:

```text id="x1m9vx"
3
```

---

## Extract Digits

| Digit | Power Calculation | Running Sum |
| ----- | ----------------- | ----------- |
| 3     | 3³ = 27           | 27          |
| 5     | 5³ = 125          | 152         |
| 1     | 1³ = 1            | 153         |

Final sum:

```text id="z7m2qp"
153
```

Matches original number.

Result:

```text id="u4m8zk"
YES
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Recursive digit extraction
* Precomputed power tables
* Logarithmic digit counting
* String-based implementations

---

# **Follow-Up Variants**

Interviewers may ask:

* Print all Armstrong numbers in a range
* Generalized narcissistic number detection
* Base-K Armstrong numbers
* Very large integer handling
* Memoized exponentiation optimization

---

# **Execution Time Limit**

**2 seconds**