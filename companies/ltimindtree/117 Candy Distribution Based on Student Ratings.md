# **Problem 117: Candy Distribution Based on Student Ratings**

**Company:** LTIMindtree

**Category:** Arrays / Greedy Algorithms

**Difficulty:** Hard

---

# **Problem Description**

A kindergarten teacher, Alice, is distributing candies to students seated in a straight line.

Each student has received a performance rating represented by an integer array.

Alice must distribute candies according to the following rules:

1. Every student must receive at least one candy
2. Any student with a higher rating than an adjacent student must receive strictly more candies than that neighbor

Your task is to determine the:

```text id="m2v8zk"
minimum total number of candies
```

required to satisfy all constraints.

This problem evaluates a candidate’s understanding of:

* greedy optimization
* bidirectional constraint propagation
* local dependency handling
* optimal resource distribution

Interviewers commonly expect candidates to derive an efficient linear-time greedy solution instead of brute-force redistribution approaches.

---

# **Task**

Given an integer array:

```text id="x7m1qa"
ratings
```

where:

```text id="u3m8qp"
ratings[i]
```

represents the performance rating of the:

```text id="f9m1zk"
i-th
```

student, return the minimum number of candies required.

---

# **Important Rules**

* Every student must receive at least:

```text id="r2m8vx"
1
```

candy.

* If:

```text id="n7m2qa"
ratings[i] > ratings[i - 1]
```

then:

```text id="p4m9xp"
candies[i] > candies[i - 1]
```

* If:

```text id="v1m8zk"
ratings[i] > ratings[i + 1]
```

then:

```text id="g8m2vx"
candies[i] > candies[i + 1]
```

* Candy constraints apply only between adjacent students.
* Non-adjacent students do not affect each other.
* Students with equal ratings do not impose any additional candy ordering constraint.

---

# **Input Format**

First line contains integer:

```text id="x2m1qa"
N
```

representing number of students.

Second line contains:

```text id="m9v2zk"
N space-separated integers
```

representing student ratings.

---

# **Output Format**

Print a single integer representing:

```text id="k4m8qp"
minimum candies required
```

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* **0 ≤ ratings[i] ≤ 10⁹**

---

# **Sample Input 1**

```text id="u7m1xp"
3
1 0 2
```

---

# **Sample Output 1**

```text id="m4k8qa"
5
```

---

# **Explanation**

One optimal distribution:

| Rating | Candies |
| ------ | ------- |
| 1      | 2       |
| 0      | 1       |
| 2      | 2       |

Total candies:

```text id="v8m2zk"
2 + 1 + 2 = 5
```

---

# **Sample Input 2**

```text id="x1m9vx"
3
1 2 2
```

---

# **Sample Output 2**

```text id="z7m2qp"
4
```

---

# **Explanation**

One optimal distribution:

| Rating | Candies |
| ------ | ------- |
| 1      | 1       |
| 2      | 2       |
| 2      | 1       |

Total candies:

```text id="u4m8zk"
1 + 2 + 1 = 4
```

Equal ratings do not require additional candies.

---

# **Sample Input 3**

```text id="k2m1qa"
5
1 3 4 5 2
```

---

# **Sample Output 3**

```text id="r7m2zk"
11
```

---

# **Explanation**

One optimal distribution:

| Rating | Candies |
| ------ | ------- |
| 1      | 1       |
| 3      | 2       |
| 4      | 3       |
| 5      | 4       |
| 2      | 1       |

Total:

```text id="u1m8xp"
1 + 2 + 3 + 4 + 1 = 11
```

---

# **Sample Input 4**

```text id="m4k8qa"
4
1 2 3 4
```

---

# **Sample Output 4**

```text id="v8m2zk"
10
```

---

# **Explanation**

Strictly increasing ratings require:

```text id="x1m9vx"
1 2 3 4
```

candies respectively.

Total:

```text id="z7m2qp"
1 + 2 + 3 + 4 = 10
```

---

# **Why Naive Approaches Fail**

A brute-force redistribution strategy may repeatedly adjust neighboring students until constraints are satisfied.

Such repeated corrections may require:

```text id="u4m8zk"
O(N²)
```

time complexity in worst-case scenarios.

This becomes inefficient for very large arrays.

---

# **Key Greedy Observation**

The constraints are directional:

* left neighbor affects right neighbor
* right neighbor affects left neighbor

A single traversal cannot satisfy both simultaneously.

Thus interviewers expect a:

```text id="k2m1qa"
two-pass greedy approach
```

---

# **Optimized Bidirectional Greedy Strategy**

Maintain an array:

```text id="r7m2zk"
candies[]
```

initialized with:

```text id="u1m8xp"
1
```

for every student.

---

# **Step 1 — Left-to-Right Pass**

Traverse from left to right.

If:

```text id="m4k8qa"
ratings[i] > ratings[i - 1]
```

then assign:

```text id="v8m2zk"
candies[i] = candies[i - 1] + 1
```

This satisfies all increasing relationships toward the right.

---

# **Step 2 — Right-to-Left Pass**

Traverse from right to left.

If:

```text id="x1m9vx"
ratings[i] > ratings[i + 1]
```

then update:

```text id="z7m2qp"
candies[i]
```

using:

```text id="u4m8zk"
max(candies[i], candies[i + 1] + 1)
```

The:

```text id="k2m1qa"
max()
```

is necessary to preserve constraints already established during the first pass.

---

# **Why This Works**

The first traversal guarantees:

```text id="r7m2zk"
left neighbor constraints
```

The second traversal guarantees:

```text id="u1m8xp"
right neighbor constraints
```

Combining both ensures all local conditions are satisfied while minimizing total candies.

---

# **Recommended Data Structures**

| Structure       | Purpose                 |
| --------------- | ----------------------- |
| `Array`         | Store ratings           |
| `Candies Array` | Store candy allocations |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* strictly increasing ratings
* strictly decreasing ratings
* equal adjacent ratings
* single student arrays
* repeated peaks and valleys
* large input arrays

---

# **Expected Complexity**

## Optimized Greedy Solution

### Time Complexity

* **O(N)**

Two linear traversals are performed.

---

### Space Complexity

* **O(N)**

for maintaining the candies allocation array.

---

# **Example Walkthrough**

Input:

```text id="m4k8qa"
[1,0,2]
```

---

## Initial Candies

```text id="v8m2zk"
[1,1,1]
```

---

## Left-to-Right Pass

| Index | Condition   | Candies |
| ----- | ----------- | ------- |
| 1     | 0 > 1 → No  | [1,1,1] |
| 2     | 2 > 0 → Yes | [1,1,2] |

---

## Right-to-Left Pass

| Index | Condition   | Candies |
| ----- | ----------- | ------- |
| 1     | 0 > 2 → No  | [1,1,2] |
| 0     | 1 > 0 → Yes | [2,1,2] |

---

## Final Answer

```text id="x1m9vx"
2 + 1 + 2 = 5
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Constant-space greedy optimization
* Local minima and slope tracking
* Dynamic Programming interpretation
* Priority queue redistribution

---

# **Follow-Up Variants**

Interviewers may ask:

* Return actual candy distribution
* Circular seating arrangement
* Multiple neighbor dependency rules
* Weighted candy costs
* Online student insertion/removal

---

# **Execution Time Limit**

**5 seconds**