# **Problem 103: Maximum Subarray (Kadane's Algorithm)**

**Company:** ServiceNow

**Category:** Arrays / Dynamic Programming

**Difficulty:** Medium

---

# **Problem Description**

A financial analytics platform tracks daily profit and loss values for multiple investment portfolios.

Analysts want to identify the continuous time period that generated the maximum overall profit.

Given an integer array representing gains and losses over time:

* positive values represent profit
* negative values represent loss

your task is to determine the contiguous subarray having the maximum possible sum.

This is the classic:

```text id="m2v8zk"
Maximum Subarray Problem
```

commonly solved using:

```text id="x7m1qa"
Kadane's Algorithm
```

---

# **Task**

Given an integer array:

```text id="u3m8qp"
arr
```

find the contiguous subarray with the largest sum and return that maximum sum.

A subarray must contain:

```text id="f9m1zk"
at least one element
```

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
maximum possible subarray sum
```

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* **-10⁹ ≤ arr[i] ≤ 10⁹**

---

# **Important Note**

Use:

```text id="v1m8zk"
64-bit integers
```

for storing sums because the maximum subarray sum may exceed 32-bit integer limits.

---

# **Sample Input 1**

```text id="g8m2vx"
9
-2 1 -3 4 -1 2 1 -5 4
```

---

# **Sample Output 1**

```text id="x2m1qa"
6
```

---

# **Explanation**

Maximum sum subarray is:

```text id="m9v2zk"
[4, -1, 2, 1]
```

Sum:

```text id="k4m8qp"
4 + (-1) + 2 + 1 = 6
```

---

# **Sample Input 2**

```text id="u7m1xp"
5
1 2 3 4 5
```

---

# **Sample Output 2**

```text id="m4k8qa"
15
```

---

# **Explanation**

Entire array forms the maximum subarray.

---

# **Sample Input 3**

```text id="v8m2zk"
5
-8 -3 -6 -2 -5
```

---

# **Sample Output 3**

```text id="x1m9vx"
-2
```

---

# **Explanation**

All elements are negative.

The maximum subarray must still contain at least one element.

Thus:

```text id="z7m2qp"
[-2]
```

gives the maximum sum.

---

# **Sample Input 4**

```text id="u4m8zk"
6
5 -2 3 4 -1 2
```

---

# **Sample Output 4**

```text id="k2m1qa"
11
```

---

# **Explanation**

Maximum subarray:

```text id="r7m2zk"
[5, -2, 3, 4, -1, 2]
```

Sum:

```text id="u1m8xp"
11
```

Although the subarray contains negative values, the overall sum remains maximum.

---

# **Naive Approach**

Generate all possible subarrays.

For each subarray:

1. Compute sum
2. Track maximum value

---

## **Complexity of Naive Solution**

### Time Complexity

* **O(N²)** using prefix sums
* **O(N³)** using direct summation

Too slow for very large arrays.

---

# **Optimized Kadane's Algorithm**

Kadane's Algorithm efficiently computes the maximum subarray sum in a single traversal.

---

# **Core Insight**

For every index:

* either extend previous subarray
* or start a new subarray from current element

---

# **Efficient Strategy**

Maintain:

| Variable     | Meaning                                  |
| ------------ | ---------------------------------------- |
| `currentSum` | Maximum subarray ending at current index |
| `maxSum`     | Best subarray sum found so far           |

For every element:

```text id="m4k8qa"
currentSum = max(arr[i], currentSum + arr[i])
```

Update:

```text id="v8m2zk"
maxSum = max(maxSum, currentSum)
```

---

# **Dynamic Programming Interpretation**

Define:

```text id="x1m9vx"
dp[i]
```

as:

```text id="z7m2qp"
maximum subarray sum ending at index i
```

Transition:

```text id="u4m8zk"
dp[i] = max(arr[i], dp[i-1] + arr[i])
```

Kadane's Algorithm optimizes this DP using constant space.

---

# **Recommended Data Structures**

| Structure          | Purpose              |
| ------------------ | -------------------- |
| `Variables`        | Running sum tracking |
| `Array (optional)` | DP formulation       |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* all negative numbers
* all positive numbers
* single-element arrays
* large negative prefixes
* zeros inside array
* mixed positive and negative values

---

# **Expected Complexity**

## Kadane's Algorithm

### Time Complexity

* **O(N)**

Single traversal of array.

---

### Space Complexity

* **O(1)**

Only constant extra variables are required.

---

# **Example Walkthrough**

Array:

```text id="k2m1qa"
[-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

| Index | Value | currentSum | maxSum |
| ----- | ----- | ---------- | ------ |
| 0     | -2    | -2         | -2     |
| 1     | 1     | 1          | 1      |
| 2     | -3    | -2         | 1      |
| 3     | 4     | 4          | 4      |
| 4     | -1    | 3          | 4      |
| 5     | 2     | 5          | 5      |
| 6     | 1     | 6          | 6      |
| 7     | -5    | 1          | 6      |
| 8     | 4     | 5          | 6      |

Final answer:

```text id="r7m2zk"
6
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Divide and Conquer solution
* Prefix Sum optimization
* Segment Tree approach

---

# **Follow-Up Variants**

Interviewers may ask:

* Return actual subarray indices
* Circular Maximum Subarray
* Maximum Product Subarray
* 2D Maximum Sum Rectangle
* K-Concatenation Maximum Sum

---

# **Execution Time Limit**

**5 seconds**