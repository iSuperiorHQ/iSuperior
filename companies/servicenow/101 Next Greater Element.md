# **Problem 101: Next Greater Element**

**Company:** ServiceNow

**Category:** Stack / Monotonic Stack

**Difficulty:** Medium

---

# **Problem Description**

A monitoring platform processes millions of system metrics every second.

For every metric value, engineers want to identify the next future metric that is strictly greater than the current one.

This helps in:

* anomaly detection
* trend analysis
* performance forecasting
* alert generation

Your task is to efficiently determine the:

```text id="m2v8zk"
Next Greater Element (NGE)
```

for every element in a given array.

The next greater element of an element:

```text id="x7m1qa"
arr[i]
```

is the first element appearing to its right that is strictly greater than:

```text id="u3m8qp"
arr[i]
```

If no such element exists, return:

```text id="f9m1zk"
-1
```

for that position.

Equal values are:

```text id="r2m8vx"
NOT considered greater
```

elements.

---

# **Task**

Given an integer array:

```text id="n7m2qa"
arr
```

find the next greater element for every array element.

---

# **Input Format**

First line contains integer:

```text id="p4m9xp"
N
```

representing array size.

Second line contains:

```text id="v1m8zk"
N space-separated integers
```

representing array elements.

---

# **Output Format**

Print:

```text id="g8m2vx"
N space-separated integers
```

where:

```text id="x2m1qa"
result[i]
```

denotes the next greater element of:

```text id="m9v2zk"
arr[i]
```

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* **-10⁹ ≤ arr[i] ≤ 10⁹**

---

# **Sample Input 1**

```text id="k4m8qp"
4
4 5 2 10
```

---

# **Sample Output 1**

```text id="u7m1xp"
5 10 10 -1
```

---

# **Explanation**

For:

```text id="m4k8qa"
4
```

next greater element is:

```text id="v8m2zk"
5
```

For:

```text id="x1m9vx"
5
```

next greater element is:

```text id="z7m2qp"
10
```

For:

```text id="u4m8zk"
2
```

next greater element is:

```text id="k2m1qa"
10
```

For:

```text id="r7m2zk"
10
```

no greater element exists on the right.

---

# **Sample Input 2**

```text id="u1m8xp"
5
13 7 6 12 10
```

---

# **Sample Output 2**

```text id="m4k8qa"
-1 12 12 -1 -1
```

---

# **Explanation**

For:

```text id="v8m2zk"
13
```

no greater element exists on the right.

For:

```text id="x1m9vx"
7
```

next greater element is:

```text id="z7m2qp"
12
```

For:

```text id="u4m8zk"
6
```

next greater element is also:

```text id="k2m1qa"
12
```

---

# **Sample Input 3**

```text id="r7m2zk"
6
1 2 3 4 5 6
```

---

# **Sample Output 3**

```text id="u1m8xp"
2 3 4 5 6 -1
```

---

# **Explanation**

Every element's next greater element is the immediately adjacent element on the right except the last element.

---

# **Sample Input 4**

```text id="m4k8qa"
5
9 8 7 6 5
```

---

# **Sample Output 4**

```text id="v8m2zk"
-1 -1 -1 -1 -1
```

---

# **Explanation**

Array is strictly decreasing.

No element has a greater element on its right side.

---

# **Sample Input 5**

```text id="x1m9vx"
5
2 2 2 2 2
```

---

# **Sample Output 5**

```text id="z7m2qp"
-1 -1 -1 -1 -1
```

---

# **Explanation**

Equal elements are not considered greater.

Thus no element has a valid next greater element.

---

# **Naive Approach**

For every element:

1. Traverse all elements to the right
2. Find first greater element

---

## **Complexity of Naive Solution**

### Time Complexity

* **O(N²)**

This becomes inefficient for large arrays.

---

# **Optimized Monotonic Stack Approach**

Use a decreasing stack to efficiently track unresolved elements.

---

# **Efficient Strategy**

Traverse array from right to left.

For every element:

1. Remove all smaller or equal elements from stack
2. Top of stack becomes next greater element
3. Push current element into stack

---

# **Monotonic Stack Insight**

The stack always maintains elements in:

```text id="u4m8zk"
strictly decreasing order
```

from bottom to top.

This guarantees:

* efficient lookup
* single-pass processing
* linear complexity

---

# **Recommended Data Structures**

| Structure | Purpose                          |
| --------- | -------------------------------- |
| `Stack`   | Store candidate greater elements |
| `Array`   | Store final answers              |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* duplicate values
* negative numbers
* strictly increasing arrays
* strictly decreasing arrays
* single-element arrays
* very large inputs

---

# **Expected Complexity**

## Monotonic Stack Solution

### Time Complexity

* **O(N)**

Each element is pushed and popped at most once.

---

### Space Complexity

* **O(N)**

for maintaining the stack and output array.

---

# **Example Walkthrough**

Array:

```text id="k2m1qa"
[4, 5, 2, 10]
```

Process from right to left:

| Current | Stack Before | Next Greater | Stack After |
| ------- | ------------ | ------------ | ----------- |
| 10      | empty        | -1           | [10]        |
| 2       | [10]         | 10           | [10,2]      |
| 5       | [10,2]       | 10           | [10,5]      |
| 4       | [10,5]       | 5            | [10,5,4]    |

Final answer:

```text id="r7m2zk"
[5,10,10,-1]
```

---

# **Follow-Up Variants**

Interviewers may ask:

* Next Smaller Element
* Circular Next Greater Element
* Stock Span Problem
* Daily Temperatures
* Previous Greater Element

---

# **Execution Time Limit**

**5 seconds**