````md id="9pq2xr"
# Problem 23: Maximum Mathematical Distance Between Good Triplets

**Company:** Google

**Difficulty:** Hard

---

# Category

- Arrays
- Dynamic Programming
- Prefix & Suffix Optimization
- Greedy
- Mathematical Optimization

---

# Problem Description

A distributed analytics platform stores millions of numerical observations generated from different sensors across a large-scale infrastructure system.

To detect highly significant patterns, the platform defines a:

```text
Good Triplet
````

as a triplet of indices:

```text
(i, j, k)
```

such that:

```text
0 ≤ i < j < k < N
```

and:

```text
A[i] < A[j] < A[k]
```

The system defines the:

```text
Mathematical Distance
```

of a good triplet as:

```text
|A[i] - A[j]| + |A[j] - A[k]| + |A[i] - A[k]|
```

Your task is to determine the maximum possible mathematical distance among all valid good triplets.

If no valid good triplet exists, return:

```text
-1
```

---

# Business Requirement

Given an integer array:

```text
A
```

find three indices:

```text
(i, j, k)
```

such that:

* `i < j < k`
* `A[i] < A[j] < A[k]`

and the following expression is maximized:

```text
|A[i] - A[j]| + |A[j] - A[k]| + |A[i] - A[k]|
```

---

# Important Mathematical Observation

For strictly increasing triplets:

```text
A[i] < A[j] < A[k]
```

absolute values simplify as:

```text
|A[i] - A[j]| = A[j] - A[i]
|A[j] - A[k]| = A[k] - A[j]
|A[i] - A[k]| = A[k] - A[i]
```

Therefore:

```text
(A[j] - A[i])
+ (A[k] - A[j])
+ (A[k] - A[i])

= 2 × (A[k] - A[i])
```

Hence the problem reduces to maximizing:

```text
2 × (A[k] - A[i])
```

for all valid increasing triplets.

---

# Task

Return the maximum mathematical distance among all valid good triplets.

If no valid triplet exists, return:

```text
-1
```

---

# Input Format

First line contains integer:

```text
N
```

representing size of array.

Second line contains:

```text
N space-separated integers
```

representing array elements.

---

# Output Format

Print the maximum mathematical distance.

---

# Constraints

* **3 ≤ N ≤ 2 × 10⁵**
* **-10⁹ ≤ A[i] ≤ 10⁹**

---

# Sample Input 1

```text
6
2 5 3 7 11 8
```

---

# Sample Output 1

```text
18
```

---

# Explanation

Valid good triplets include:

```text
(2, 5, 7)
(2, 5, 11)
(2, 7, 11)
(3, 7, 11)
```

Optimal triplet:

```text
(2, 7, 11)
```

Distance:

```text
|2 - 7| + |7 - 11| + |2 - 11|
= 5 + 4 + 9
= 18
```

---

# Sample Input 2

```text
5
9 8 7 6 5
```

---

# Sample Output 2

```text
-1
```

---

# Explanation

No strictly increasing triplet exists.

Hence answer is:

```text
-1
```

---

# Sample Input 3

```text
7
1 9 2 10 3 11 20
```

---

# Sample Output 3

```text
38
```

---

# Explanation

Optimal triplets include:

```text
(1, 10, 20)
(1, 11, 20)
```

Both produce the maximum mathematical distance.

Distance:

```text
|1 - 10| + |10 - 20| + |1 - 20|
= 9 + 10 + 19
= 38
```

---

# Recommended Approach

Efficient interview solution uses:

```text
Prefix Minimum + Suffix Maximum
```

---

# Optimal Strategy

For every middle index:

```text
j
```

find:

* minimum value on left side smaller than `A[j]`
* maximum value on right side greater than `A[j]`

such that:

```text
leftMin < A[j] < rightMax
```

Then compute:

```text
2 × (rightMax - leftMin)
```

and maximize the answer.

---

# Expected Complexity

## Optimized Approach

### Time Complexity

```text
O(N)
```

because:

* prefix minimum computation takes `O(N)`
* suffix maximum computation takes `O(N)`
* final traversal takes `O(N)`

---

### Space Complexity

```text
O(N)
```

for auxiliary prefix and suffix arrays.

---

# Alternative Approaches

| Approach                | Time Complexity | Space Complexity |
| ----------------------- | --------------- | ---------------- |
| Brute Force Triplets    | O(N³)           | O(1)             |
| Improved Enumeration    | O(N²)           | O(1)             |
| Prefix-Suffix Optimized | O(N)            | O(N)             |

---

# Edge Cases

Your solution should correctly handle:

* duplicate values
* negative numbers
* no increasing triplets
* multiple optimal answers
* strictly increasing arrays
* strictly decreasing arrays
* large input constraints

---

# Object-Oriented Design Expectations

Recommended classes:

| Class             | Responsibility                  |
| ----------------- | ------------------------------- |
| `TripletAnalyzer` | Core optimization logic         |
| `PrefixProcessor` | Maintains prefix minimum values |
| `SuffixProcessor` | Maintains suffix maximum values |
| `InputHandler`    | Parses input data               |

---

# Follow-Up Interview Questions

Interviewers may ask:

* Can this be solved in constant space?
* How would you return actual triplet indices?
* How would you handle streaming data?
* Can this be generalized for K-tuples?
* How would you optimize for distributed systems?

---

# Execution Time Limit

```text
2 seconds
```

```
```