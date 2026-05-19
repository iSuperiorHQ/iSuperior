# **Problem 115: Even Pairing Verification of Array Elements**

**Company:** Deloitte

**Category:** Arrays / Mathematical Observation

**Difficulty:** Easy-Medium

---

# **Problem Description**

A logistics company processes numbered packages in pairs before shipment.

For safety validation, every pair of package IDs must satisfy the condition that:

```text id="m2v8zk"
their sum is even
```

Each package must belong to exactly one pair.

Your task is to determine whether the entire array can be partitioned into:

```text id="x7m1qa"
mutually exclusive pairs
```

such that the sum of the two elements in every pair is even.

This problem appears combinatorial at first glance, but interviewers expect candidates to identify an important mathematical property that leads to an optimal linear-time solution.

---

# **Task**

Given an integer array:

```text id="u3m8qp"
nums
```

determine whether all elements can be grouped into disjoint pairs where every pair has an even sum.

Return:

```text id="f9m1zk"
YES
```

if such a pairing is possible, otherwise return:

```text id="r2m8vx"
NO
```

---

# **Mathematical Observation**

The sum of two integers is even:

* if both integers are even
* if both integers are odd

Examples:

| Pair  | Sum | Even? |
| ----- | --- | ----- |
| 2 + 4 | 6   | Yes   |
| 3 + 5 | 8   | Yes   |
| 2 + 3 | 5   | No    |

Thus:

```text id="n7m2qa"
even numbers must pair with even numbers
```

and:

```text id="p4m9xp"
odd numbers must pair with odd numbers
```

---

# **Key Insight**

A valid pairing is possible:

```text id="v1m8zk"
IFF
```

* total number of even elements is even
* total number of odd elements is even

because each valid pair consumes exactly two numbers of the same parity.

Additionally:

```text id="g8m2vx"
a complete pairing requires the array size to be even
```

otherwise one element will always remain unpaired.

---

# **Input Format**

First line contains integer:

```text id="x2m1qa"
N
```

representing size of array.

Second line contains:

```text id="m9v2zk"
N space-separated integers
```

representing array elements.

---

# **Output Format**

Print:

```text id="k4m8qp"
YES
```

if valid pairing exists.

Otherwise print:

```text id="u7m1xp"
NO
```

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* **-10⁹ ≤ nums[i] ≤ 10⁹**

---

# **Sample Input 1**

```text id="m4k8qa"
6
2 4 6 1 3 5
```

---

# **Sample Output 1**

```text id="v8m2zk"
NO
```

---

# **Explanation**

Even numbers:

```text id="x1m9vx"
2 4 6
```

Count:

```text id="z7m2qp"
3
```

Odd numbers:

```text id="u4m8zk"
1 3 5
```

Count:

```text id="k2m1qa"
3
```

Both parity groups contain an odd number of elements.

Thus complete valid pairing is impossible.

---

# **Sample Input 2**

```text id="r7m2zk"
8
2 4 6 8 1 3 5 7
```

---

# **Sample Output 2**

```text id="u1m8xp"
YES
```

---

# **Explanation**

Even count:

```text id="m4k8qa"
4
```

Odd count:

```text id="v8m2zk"
4
```

Both counts are even.

Thus all elements can be perfectly paired.

---

# **Sample Input 3**

```text id="x1m9vx"
5
2 4 6 8 10
```

---

# **Sample Output 3**

```text id="z7m2qp"
NO
```

---

# **Explanation**

Total even count:

```text id="u4m8zk"
5
```

Odd number of even elements means one element will remain unpaired.

---

# **Sample Input 4**

```text id="k2m1qa"
4
1 9 3 7
```

---

# **Sample Output 4**

```text id="r7m2zk"
YES
```

---

# **Explanation**

All numbers are odd.

Odd count:

```text id="u1m8xp"
4
```

which is even.

Valid pairs exist:

```text id="m4k8qa"
(1,9)
(3,7)
```

---

# **Naive Misconception**

Some candidates attempt:

* generating all pair combinations
* backtracking
* graph matching approaches

These solutions are unnecessarily complex.

---

# **Optimal Observation-Based Solution**

Only parity matters.

For every element:

* increment even counter if divisible by 2
* otherwise increment odd counter

Finally check:

```text id="v8m2zk"
evenCount % 2 == 0
AND
oddCount % 2 == 0
```

---

# **Efficient Algorithm**

---

## Step 1 — Traverse Array

Count:

* even elements
* odd elements

---

## Step 2 — Validate Pairing Condition

If both counts are even:

```text id="x1m9vx"
YES
```

Otherwise:

```text id="z7m2qp"
NO
```

---

# **Why This Works**

Each valid pair requires:

* two even numbers

OR

* two odd numbers

Therefore parity groups must themselves contain an even number of elements.

No explicit pairing construction is necessary.

---

# **Recommended Data Structures**

| Structure           | Purpose               |
| ------------------- | --------------------- |
| `Array`             | Store elements        |
| `Integer Variables` | Track even/odd counts |

No additional structures are required.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* arrays with all even numbers
* arrays with all odd numbers
* single-element arrays
* negative integers
* zero values
* mixed parity arrays
* very large arrays

---

# **Expected Complexity**

## Optimized Counting Solution

### Time Complexity

* **O(N)**

Each element is processed exactly once.

---

### Space Complexity

* **O(1)**

Only constant extra variables are maintained.

---

# **Example Walkthrough**

Input:

```text id="u4m8zk"
[2,4,6,8,1,3,5,7]
```

---

## Counting Phase

| Number | Type |
| ------ | ---- |
| 2      | Even |
| 4      | Even |
| 6      | Even |
| 8      | Even |
| 1      | Odd  |
| 3      | Odd  |
| 5      | Odd  |
| 7      | Odd  |

---

## Final Counts

| Type | Count |
| ---- | ----- |
| Even | 4     |
| Odd  | 4     |

Both counts are even.

Result:

```text id="k2m1qa"
YES
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Explicit pair construction
* Bipartite matching misconceptions
* Modular arithmetic extensions
* Pairing under additional constraints

---

# **Follow-Up Variants**

Interviewers may ask:

* Pair sums divisible by K
* Minimize pairing cost
* Return actual valid pairs
* Dynamic insertion/deletion queries
* Pairing with frequency constraints

---

# **Execution Time Limit**

**2 seconds**