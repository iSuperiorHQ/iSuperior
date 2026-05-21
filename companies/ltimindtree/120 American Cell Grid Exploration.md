# **Problem 120: American Cell Grid Exploration**

**Company:** LTIMindtree

**Category:** Dynamic Programming / Combinatorics

**Difficulty:** Medium-Hard

---

# **Problem Description**

Christopher Columbus is exploring a massive:

```text id="m2v8zk"
N × M
```

rectangular American cell grid.

He starts at the top-left coordinate:

```text id="x7m1qa"
(1,1)
```

and wants to reach a destination cell:

```text id="u3m8qp"
(x,y)
```

From any cell, Columbus may move only:

* one step to the right
* one step downward

Your task is to determine the total number of:

```text id="f9m1zk"
unique valid paths
```

from the origin to the target coordinate.

This problem evaluates a candidate’s understanding of:

* dynamic programming
* combinatorial mathematics
* state transitions
* grid traversal optimization
* mathematical reduction of DP problems

Interviewers often expect candidates to first derive the classical dynamic programming solution and then optimize further using combinatorics.

---

# **Task**

Given integers:

```text id="r2m8vx"
N, M, x, y
```

representing grid dimensions and target coordinates, return the number of unique paths from:

```text id="n7m2qa"
(1,1)
```

to:

```text id="p4m9xp"
(x,y)
```

using only:

* right moves
* downward moves

---

# **Important Rules**

* Coordinates use:

```text id="v1m8zk"
1-based indexing
```

* Only the following moves are allowed:

```text id="g8m2vx"
Right  →  (i, j+1)
Down   ↓  (i+1, j)
```

* Moving outside the grid is not allowed
* All paths must remain entirely within the grid
* The grid dimensions ensure that the destination coordinate lies within valid bounds

---

# **Input Format**

Single line contains four integers:

```text id="x2m1qa"
N M x y
```

where:

* `N` = number of rows
* `M` = number of columns
* `(x,y)` = destination coordinate

---

# **Output Format**

Print a single integer representing:

```text id="m9v2zk"
total number of unique valid paths
```

---

# **Constraints**

* **1 ≤ N, M ≤ 2000**
* **1 ≤ x ≤ N**
* **1 ≤ y ≤ M**
* Final answer fits within 64-bit signed integer range

---

# **Sample Input 1**

```text id="k4m8qp"
3 3 3 3
```

---

# **Sample Output 1**

```text id="u7m1xp"
6
```

---

# **Explanation**

To reach:

```text id="m4k8qa"
(3,3)
```

Columbus must perform:

* `2` downward moves
* `2` rightward moves

Total unique permutations:

---

# **Sample Input 2**

```text id="v8m2zk"
4 5 2 3
```

---

# **Sample Output 2**

```text id="x1m9vx"
3
```

---

# **Explanation**

To reach:

```text id="z7m2qp"
(2,3)
```

required moves:

* `1` downward move
* `2` rightward moves

Total paths:

---

# **Sample Input 3**

```text id="u4m8zk"
5 5 1 1
```

---

# **Sample Output 3**

```text id="k2m1qa"
1
```

---

# **Explanation**

Starting point already equals destination.

Only one valid path exists:

```text id="r7m2zk"
stay at current position
```

---

# **Sample Input 4**

```text id="u1m8xp"
2 7 2 7
```

---

# **Sample Output 4**

```text id="m4k8qa"
7
```

---

# **Explanation**

Required moves:

* `1` downward move
* `6` rightward moves

Total unique paths:

---

# **Why Brute Force Fails**

A recursive traversal exploring all possible paths generates exponential complexity:

```text id="v8m2zk"
O(2^(x+y))
```

This becomes infeasible for large grids.

Interviewers expect optimized solutions.

---

# **Dynamic Programming Insight**

Define:

```text id="x1m9vx"
DP[i][j]
```

as the number of unique ways to reach cell:

```text id="z7m2qp"
(i,j)
```

A cell can only be reached from:

* top neighbor

```text id="u4m8zk"
(i-1,j)
```

* left neighbor

```text id="k2m1qa"
(i,j-1)
```

Thus recurrence relation becomes:

---

# **Dynamic Programming Algorithm**

---

## Step 1 — Initialize Base Cases

First row and first column each have exactly:

```text id="r7m2zk"
1
```

path because movement is restricted to a single direction.

---

## Step 2 — Fill DP Table

For every remaining cell:

```text id="u1m8xp"
DP[i][j] = DP[i-1][j] + DP[i][j-1]
```

---

## Step 3 — Return Final Answer

Answer is stored at:

```text id="m4k8qa"
DP[x][y]
```

---

# **Why This Works**

Every valid path to a cell must originate from:

* above
* left

The recurrence accumulates all possible path combinations exactly once.

---

# **Combinatorial Optimization**

To reach coordinate:

```text id="v8m2zk"
(x,y)
```

Columbus must make exactly:

* `x-1` downward moves
* `y-1` rightward moves

Total moves:

```text id="x1m9vx"
(x+y-2)
```

Thus the problem reduces to choosing positions for either move type.

Number of unique paths:

The binomial coefficient should be computed iteratively to avoid intermediate factorial overflow.

This computes the result in:

```text id="z7m2qp"
O(x+y)
```

time.

---

# **Recommended Data Structures**

| Structure           | Purpose                   |
| ------------------- | ------------------------- |
| `2D Array`          | DP tabulation             |
| `Integer Variables` | Combinatorial calculation |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* destination equal to origin
* single-row grids
* single-column grids
* very large grids
* asymmetric dimensions
* maximum constraint values

---

# **Expected Complexity**

## Dynamic Programming Solution

### Time Complexity

* **O(x × y)**

Every reachable state up to coordinate:

```text id="u4m8zk"
(x,y)
```

is processed exactly once.

---

### Space Complexity

* **O(x × y)**

for DP table storage.

---

# **Optimized Combinatorial Solution**

### Time Complexity

* **O(x + y)**

---

### Space Complexity

* **O(1)**

excluding arithmetic storage.

---

# **Example Walkthrough**

Input:

```text id="k2m1qa"
N = 3
M = 3
x = 3
y = 3
```

---

## Required Moves

| Move Type | Count |
| --------- | ----- |
| Down      | 2     |
| Right     | 2     |

Total moves:

```text id="r7m2zk"
4
```

---

## Count Unique Arrangements

Possible sequences:

* RRDD
* RDRD
* RDDR
* DRRD
* DRDR
* DDRR

Total:

```text id="u1m8xp"
6
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Recursive memoization
* Space-optimized DP
* Pascal triangle interpretation
* Matrix exponentiation extensions

---

# **Follow-Up Variants**

Interviewers may ask:

* Grid with obstacles
* Diagonal movement allowed
* Minimum-cost path variants
* Count paths modulo large prime
* K-step restricted movement

---

# **Execution Time Limit**

**4 seconds**