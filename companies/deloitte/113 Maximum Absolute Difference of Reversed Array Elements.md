# **Problem 113: Maximum Absolute Difference of Reversed Array Elements**

**Company:** Deloitte

**Category:** Arrays / Number Manipulation

**Difficulty:** Easy-Medium

---

# **Problem Description**

A digital analytics system stores a sequence of encoded numerical identifiers.

Before performing statistical analysis, each integer undergoes a digit-reversal transformation.

Examples:

| Original Number | Reversed Number |
| --------------- | --------------- |
| 20              | 2               |
| 54              | 45              |
| 100             | 1               |
| 907             | 709             |

After transforming every element, the system must determine the:

```text id="m2v8zk"
maximum absolute difference
```

between any two numbers in the transformed array.

This problem evaluates a candidate’s ability to:

* manipulate integers efficiently
* process arrays in multiple stages
* optimize min/max tracking
* avoid unnecessary sorting

---

# **Task**

Given an integer array:

```text id="x7m1qa"
nums
```

perform the following operations:

1. Reverse the digits of every integer
2. Construct the transformed array
3. Return the maximum absolute difference between any two transformed values

---

# **Important Rules**

* Leading zeros after reversal must be discarded automatically

Examples:

```text id="u3m8qp"
20 → 2
1000 → 1
```

* Absolute difference is defined as:

```text id="f9m1zk"
|a - b|
```

* Negative integers are NOT included in input

---

# **Input Format**

First line contains integer:

```text id="r2m8vx"
N
```

representing size of array.

Second line contains:

```text id="n7m2qa"
N space-separated integers
```

representing array elements.

---

# **Output Format**

Print a single integer representing:

```text id="p4m9xp"
maximum absolute difference
```

between any two transformed elements.

---

# **Constraints**

* **1 ≤ N ≤ 10⁵**
* **0 ≤ nums[i] ≤ 10⁹**

---

# **Sample Input 1**

```text id="v1m8zk"
4
20 33 54 92
```

---

# **Sample Output 1**

```text id="g8m2vx"
43
```

---

# **Explanation**

Transformed array:

```text id="x2m1qa"
[2, 33, 45, 29]
```

Maximum value:

```text id="m9v2zk"
45
```

Minimum value:

```text id="k4m8qp"
2
```

Maximum absolute difference:

```text id="u7m1xp"
|45 - 2| = 43
```

---

# **Sample Input 2**

```text id="m4k8qa"
5
1 10 100 1000 10000
```

---

# **Sample Output 2**

```text id="v8m2zk"
0
```

---

# **Explanation**

After reversal:

```text id="x1m9vx"
[1, 1, 1, 1, 1]
```

All values are identical.

Thus maximum absolute difference is:

```text id="z7m2qp"
0
```

---

# **Sample Input 3**

```text id="u4m8zk"
3
12 81 900
```

---

# **Sample Output 3**

```text id="k2m1qa"
12
```

---

# **Explanation**

Transformed array:

```text id="r7m2zk"
[21, 18, 9]
```

Maximum value:

```text id="u1m8xp"
21
```

Minimum value:

```text id="m4k8qa"
9
```

Maximum absolute difference:

```text id="v8m2zk"
|21 - 9| = 12
```

---

# **Sample Input 4**

```text id="x1m9vx"
4
5 50 500 5000
```

---

# **Sample Output 4**

```text id="z7m2qp"
0
```

---

# **Explanation**

After reversal:

```text id="u4m8zk"
[5, 5, 5, 5]
```

All transformed values are identical.

---

# **Naive Approach**

A brute-force solution may:

1. Reverse every integer
2. Compare every pair of transformed elements

This requires:

```text id="k2m1qa"
O(N²)
```

pairwise comparisons.

Too slow for large arrays.

---

# **Key Observation**

The maximum absolute difference between any two values is always:

```text id="r7m2zk"
maximum value - minimum value
```

Thus instead of comparing all pairs:

* track global minimum
* track global maximum

during traversal.

---

# **Digit Reversal Techniques**

Candidates may reverse digits using:

---

## Modulo Arithmetic

Repeatedly:

```text id="u1m8xp"
digit = num % 10
```

and construct reversed value.

This approach achieves true:

```text id="m4k8qa"
O(1)
```

auxiliary space.

---

## String Conversion

Convert integer to string:

1. Reverse string
2. Convert back to integer

This approach may require temporary:

```text id="v8m2zk"
O(K)
```

space where:

* `K` = number of digits in the integer.

Both approaches are acceptable.

---

# **Efficient Algorithm**

---

## Step 1 — Reverse Each Integer

Transform every array element individually.

---

## Step 2 — Track Minimum and Maximum

During traversal maintain:

| Variable   | Purpose                     |
| ---------- | --------------------------- |
| `minValue` | Smallest transformed number |
| `maxValue` | Largest transformed number  |

---

## Step 3 — Compute Final Answer

Return:

```text id="x1m9vx"
maxValue - minValue
```

---

# **Why This Works**

For any array:

```text id="z7m2qp"
maximum absolute difference
```

is achieved by:

```text id="u4m8zk"
largest element - smallest element
```

Thus only extrema are needed.

---

# **Recommended Data Structures**

| Structure           | Purpose            |
| ------------------- | ------------------ |
| `Array`             | Store input values |
| `Integer Variables` | Track min/max      |
| `Helper Function`   | Reverse digits     |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* numbers ending with zeros
* single-digit numbers
* repeated values
* all identical transformed numbers
* very large integers
* arrays of size one

---

# **Expected Complexity**

## Optimized Transformation Solution

### Time Complexity

* **O(N × K)**

Where:

* `N` = size of array
* `K` = maximum digits in an element

Each integer reversal processes its digits once.

---

### Space Complexity

* **O(1)** auxiliary space

when arithmetic reversal is used.

If string reversal is used internally, temporary digit storage may require:

```text id="k2m1qa"
O(K)
```

space per element.

---

# **Example Walkthrough**

Input:

```text id="r7m2zk"
[20, 33, 54, 92]
```

---

## Step 1 — Reverse Digits

| Original | Reversed |
| -------- | -------- |
| 20       | 2        |
| 33       | 33       |
| 54       | 45       |
| 92       | 29       |

Transformed array:

```text id="u1m8xp"
[2, 33, 45, 29]
```

---

## Step 2 — Find Extremes

| Value | Role    |
| ----- | ------- |
| 2     | Minimum |
| 45    | Maximum |

---

## Step 3 — Compute Difference

```text id="m4k8qa"
45 - 2 = 43
```

Final answer:

```text id="v8m2zk"
43
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* StringBuilder reversal
* Recursive digit reversal
* Sorting transformed values
* Stream processing optimization

---

# **Follow-Up Variants**

Interviewers may ask:

* Preserve leading zeros as strings
* Handle signed integers
* Reverse numbers in different bases
* Maximum difference after partial reversal
* Online streaming version

---

# **Execution Time Limit**

**3 seconds**