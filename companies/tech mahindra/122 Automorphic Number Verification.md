# **Problem 122: Automorphic Number Verification**

**Company:** Tech Mahindra

**Category:** Mathematics / Number Theory

**Difficulty:** Easy-Medium

---

# **Problem Description**

One of the most commonly asked mathematical interview screening problems involves identifying:

```text id="m2v8zk"
Automorphic Numbers
```

An integer is considered automorphic if the square of the number ends with exactly the same digits as the original number itself.

For example:

Since:

```text id="x7m1qa"
625
```

ends with:

```text id="u3m8qp"
25
```

the number:

```text id="f9m1zk"
25
```

is automorphic.

Your task is to determine whether a given integer satisfies this mathematical property.

This problem evaluates a candidate’s understanding of:

* modulo arithmetic
* digit boundary handling
* dynamic divisor generation
* integer manipulation
* numerical pattern recognition

Interviewers typically expect candidates to derive the divisor dynamically instead of hardcoding powers of:

```text id="r2m8vx"
10
```

---

# **Task**

Given an integer:

```text id="n7m2qa"
N
```

determine whether it is an automorphic number.

Return:

```text id="p4m9xp"
YES
```

if the number is automorphic, otherwise return:

```text id="v1m8zk"
NO
```

---

# **Definition of Automorphic Number**

A number:

```text id="g8m2vx"
N
```

is automorphic if:

where:

```text id="x2m1qa"
d
```

is the number of digits in:

```text id="m9v2zk"
N
```

---

# **Examples**

| Number | Square | Automorphic? |
| ------ | ------ | ------------ |
| 5      | 25     | Yes          |
| 6      | 36     | Yes          |
| 25     | 625    | Yes          |
| 76     | 5776   | Yes          |
| 13     | 169    | No           |

---

# **Input Format**

Single line contains integer:

```text id="k4m8qp"
N
```

---

# **Output Format**

Print:

```text id="u7m1xp"
YES
```

if the number is automorphic.

Otherwise print:

```text id="m4k8qa"
NO
```

---

# **Constraints**

* **0 ≤ N ≤ 10⁹**

---

# **Sample Input 1**

```text id="v8m2zk"
25
```

---

# **Sample Output 1**

```text id="x1m9vx"
YES
```

---

# **Explanation**

Square of:

```text id="z7m2qp"
25
```

is:

Last two digits:

```text id="u4m8zk"
25
```

match the original number.

Hence:

```text id="k2m1qa"
25
```

is automorphic.

---

# **Sample Input 2**

```text id="r7m2zk"
76
```

---

# **Sample Output 2**

```text id="u1m8xp"
YES
```

---

# **Explanation**

Square of:

```text id="m4k8qa"
76
```

is:

Last two digits:

```text id="v8m2zk"
76
```

match the original number.

Thus:

```text id="x1m9vx"
76
```

is automorphic.

---

# **Sample Input 3**

```text id="z7m2qp"
13
```

---

# **Sample Output 3**

```text id="u4m8zk"
NO
```

---

# **Explanation**

Square of:

```text id="k2m1qa"
13
```

is:

Last two digits are:

```text id="r7m2zk"
69
```

which do not match:

```text id="u1m8xp"
13
```

Hence the number is not automorphic.

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

Square of:

```text id="x1m9vx"
0
```

is:

Thus:

```text id="z7m2qp"
0
```

is automorphic.

---

# **Why Naive String-Based Approaches Are Discouraged**

Some candidates convert the square into a string and compare suffixes.

While valid, interviewers generally expect:

* modulo arithmetic
* divisor construction
* arithmetic digit reasoning

to demonstrate stronger mathematical understanding.

---

# **Efficient Mathematical Approach**

The key observation is:

If a number has:

```text id="u4m8zk"
d
```

digits, then the last:

```text id="k2m1qa"
d
```

digits of its square can be extracted using:

Use:

```text id="r7m2zk"
64-bit integer types
```

for square computation to avoid overflow.

---

# **Algorithm Overview**

---

## Step 1 — Count Digits

Determine number of digits:

```text id="u1m8xp"
d
```

in:

```text id="m4k8qa"
N
```

Special case:

```text id="v8m2zk"
N = 0
```

contains exactly:

```text id="x1m9vx"
1
```

digit.

---

## Step 2 — Generate Divisor Dynamically

Construct:

using iterative integer multiplication or integer exponentiation.

Avoid floating-point:

```text id="z7m2qp"
pow()
```

to prevent precision issues.

Examples:

| Digits | Divisor |
| ------ | ------- |
| 1      | 10      |
| 2      | 100     |
| 3      | 1000    |

---

## Step 3 — Compute Square

Calculate:

using 64-bit arithmetic.

---

## Step 4 — Extract Ending Digits

Compute:

---

## Step 5 — Verify Property

If:

return:

```text id="u4m8zk"
YES
```

otherwise return:

```text id="k2m1qa"
NO
```

---

# **Why This Works**

Modulo operation extracts the final:

```text id="r7m2zk"
d
```

digits of the square.

If those digits equal the original number, then the automorphic property holds.

---

# **Recommended Data Structures**

| Structure           | Purpose                                  |
| ------------------- | ---------------------------------------- |
| `Integer Variables` | Digit counting and arithmetic operations |

No additional data structures are required.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* `0` as input
* single-digit automorphic numbers
* large integers
* powers of `10`
* trailing zeros
* non-automorphic numbers

---

# **Expected Complexity**

## Arithmetic Modulo Solution

### Time Complexity

* **O(d)**

where:

```text id="u1m8xp"
d
```

is the number of digits.

Digit counting and divisor generation each require:

```text id="m4k8qa"
O(d)
```

operations.

Multiplication and modulo are treated as:

```text id="v8m2zk"
O(1)
```

for fixed-width integers.

---

### Space Complexity

* **O(1)**

Only constant extra variables are used.

---

# **Example Walkthrough**

Input:

```text id="x1m9vx"
76
```

---

## Count Digits

Digits:

```text id="z7m2qp"
2
```

---

## Generate Divisor

---

## Compute Square

---

## Extract Last Digits

Matches original number.

Result:

```text id="u4m8zk"
YES
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* String suffix comparison
* Recursive digit matching
* Logarithmic digit counting
* Base-K automorphic numbers

---

# **Follow-Up Variants**

Interviewers may ask:

* Print all automorphic numbers within a range
* Automorphic numbers in different bases
* Very large integer support
* Recursive suffix verification
* Trailing pattern detection problems

---

# **Execution Time Limit**

**2 seconds**