# **Problem 112: Evaluation of Product of Array Excluding the Current Index**

**Company:** Deloitte

**Category:** Arrays / Prefix-Suffix Products

**Difficulty:** Medium

---

# **Problem Description**

A distributed computing system assigns every processing unit a numerical:

```text id="m2v8zk"
power level
```

To evaluate dependency resilience, engineers must calculate the cumulative product contribution for every unit excluding the unit itself.

Given an integer array representing power levels, compute a new array where:

```text id="x7m1qa"
output[i]
```

contains the product of all elements except:

```text id="u3m8qp"
nums[i]
```

A direct solution using the mathematical division operator is strictly prohibited because:

* zero values may exist
* floating-point inaccuracies must be avoided
* fault-tolerant computation is required

Interviewers expect candidates to optimize beyond the naive:

```text id="f9m1zk"
O(N²)
```

approach by using:

* prefix products
* suffix products

to achieve linear-time complexity.

---

# **Task**

Given an integer array:

```text id="r2m8vx"
nums
```

return an array:

```text id="n7m2qa"
answer
```

such that:

```text id="p4m9xp"
answer[i]
```

equals the product of all array elements except:

```text id="v1m8zk"
nums[i]
```

---

# **Important Rules**

* Division operator is NOT allowed
* Output array must be computed efficiently
* Negative numbers and zeroes are valid inputs
* Product fits within signed 64-bit integer range

---

# **Input Format**

First line contains integer:

```text id="g8m2vx"
N
```

representing size of array.

Second line contains:

```text id="x2m1qa"
N space-separated integers
```

representing array elements.

---

# **Output Format**

Print:

```text id="m9v2zk"
N space-separated integers
```

where each value represents the product of all elements except the current index.

---

# **Constraints**

* **2 ≤ N ≤ 10⁵**
* **-30 ≤ nums[i] ≤ 30**
* Product of any prefix or suffix fits in signed 64-bit integer range

---

# **Sample Input 1**

```text id="k4m8qp"
4
1 2 3 4
```

---

# **Sample Output 1**

```text id="u7m1xp"
24 12 8 6
```

---

# **Explanation**

| Index | Product Except Self |
| ----- | ------------------- |
| 0     | 2 × 3 × 4 = 24      |
| 1     | 1 × 3 × 4 = 12      |
| 2     | 1 × 2 × 4 = 8       |
| 3     | 1 × 2 × 3 = 6       |

---

# **Sample Input 2**

```text id="m4k8qa"
5
-1 1 0 -3 3
```

---

# **Sample Output 2**

```text id="v8m2zk"
0 0 9 0 0
```

---

# **Explanation**

For index:

```text id="x1m9vx"
2
```

all remaining elements multiply to:

```text id="z7m2qp"
(-1) × 1 × (-3) × 3 = 9
```

All other positions include multiplication by zero.

---

# **Sample Input 3**

```text id="u4m8zk"
3
5 10 2
```

---

# **Sample Output 3**

```text id="k2m1qa"
20 10 50
```

---

# **Explanation**

| Index | Product Except Self |
| ----- | ------------------- |
| 0     | 10 × 2 = 20         |
| 1     | 5 × 2 = 10          |
| 2     | 5 × 10 = 50         |

---

# **Sample Input 4**

```text id="r7m2zk"
4
0 0 2 4
```

---

# **Sample Output 4**

```text id="u1m8xp"
0 0 0 0
```

---

# **Explanation**

More than one zero exists.

Thus every product contains at least one zero.

---

# **Why Division is Restricted**

A division-based approach:

1. Compute total product
2. Divide by current element

fails because:

* division by zero becomes invalid
* multiple zeroes complicate logic
* precision and overflow issues may arise

Interviewers explicitly prohibit division to test algorithmic reasoning.

---

# **Naive Brute Force Approach**

For every index:

1. Traverse entire array
2. Multiply all elements except current index

---

## Complexity of Brute Force Solution

### Time Complexity

* **O(N²)**

Too slow for large arrays.

---

### Space Complexity

* **O(1)**

excluding output array.

---

# **Optimized Prefix-Suffix Strategy**

For every index:

```text id="m4k8qa"
answer[i]
```

can be computed as:

```text id="v8m2zk"
(prefix product before i)
×
(suffix product after i)
```

Both prefix and suffix products are exclusive of the current index.

---

# **Prefix Product**

Define:

```text id="x1m9vx"
prefix[i]
```

as product of all elements strictly to the left of index:

```text id="z7m2qp"
i
```

---

# **Suffix Product**

Define:

```text id="u4m8zk"
suffix[i]
```

as product of all elements strictly to the right of index:

```text id="k2m1qa"
i
```

---

# **Efficient Algorithm**

---

## Step 1 — Build Prefix Products

Example:

```text id="r7m2zk"
nums = [1,2,3,4]
```

Prefix array:

```text id="u1m8xp"
[1,1,2,6]
```

---

## Step 2 — Build Suffix Products

Suffix array:

```text id="m4k8qa"
[24,12,4,1]
```

---

## Step 3 — Compute Final Answer

For every index:

```text id="v8m2zk"
answer[i] = prefix[i] × suffix[i]
```

Result:

```text id="x1m9vx"
[24,12,8,6]
```

---

# **Space Optimization**

Instead of maintaining separate prefix and suffix arrays:

* use output array for prefix products
* maintain running suffix product variable

This reduces auxiliary space complexity to:

```text id="z7m2qp"
O(1)
```

excluding the mandatory output array.

---

# **Recommended Data Structures**

| Structure           | Purpose                        |
| ------------------- | ------------------------------ |
| `Array`             | Store input values             |
| `Output Array`      | Store final products           |
| `Integer Variables` | Running prefix/suffix products |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* arrays containing zero
* arrays containing multiple zeroes
* negative numbers
* duplicate values
* large products
* minimum-size arrays

---

# **Expected Complexity**

## Optimized Prefix-Suffix Solution

### Time Complexity

* **O(N)**

Each element is processed a constant number of times.

---

### Space Complexity

* **O(1)** auxiliary space

excluding the mandatory output array.

If explicit prefix and suffix arrays are used:

```text id="u4m8zk"
O(N)
```

auxiliary space is required.

---

# **Example Walkthrough**

Input:

```text id="k2m1qa"
[1,2,3,4]
```

---

## Prefix Pass

| Index | Prefix Product |
| ----- | -------------- |
| 0     | 1              |
| 1     | 1              |
| 2     | 2              |
| 3     | 6              |

---

## Suffix Traversal

Running suffix products:

| Index | Suffix | Final Answer |
| ----- | ------ | ------------ |
| 3     | 1      | 6            |
| 2     | 4      | 8            |
| 1     | 12     | 12           |
| 0     | 24     | 24           |

Final output:

```text id="r7m2zk"
[24,12,8,6]
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Explicit prefix/suffix arrays
* Division-based invalid solution
* Parallel prefix multiplication
* Functional scan operations

---

# **Follow-Up Variants**

Interviewers may ask:

* Maximum product excluding one element
* Product modulo large prime
* Streaming product queries
* Dynamic array updates
* Product excluding K indices

---

# **Execution Time Limit**

**5 seconds**