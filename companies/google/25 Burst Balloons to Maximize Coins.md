````md id="6rk2vz"
# Problem 25: Burst Balloons to Maximize Coins

**Company:** Google

**Difficulty:** Hard

---

# Category

- Dynamic Programming
- Interval DP
- Recursion
- Memoization
- Game Strategy
- Optimization

---

# Problem Description

A gaming company has designed a reward system involving a sequence of magical balloons.

Each balloon contains a positive integer value.

When a balloon is burst, the player earns coins equal to the product of:

```text
leftBalloon × currentBalloon × rightBalloon
````

where:

* `leftBalloon` → nearest unburst balloon on the left
* `rightBalloon` → nearest unburst balloon on the right

After bursting a balloon:

* the balloon disappears permanently
* neighboring balloons become adjacent

The goal is to determine the maximum number of coins obtainable by bursting all balloons in an optimal order.

---

# Business Requirement

Given an array:

```text
nums
```

representing balloon values, determine the maximum coins that can be collected.

For every burst operation:

```text
coins = left × current × right
```

If there is no balloon on either side, assume:

```text
1
```

exists outside the array boundary.

---

# Important Observation

Bursting order significantly changes the final answer.

Greedy strategies do NOT work because:

```text
bursting a balloon changes future neighbors
```

Thus:

* local optimal choices may produce globally suboptimal answers
* interval-based dynamic programming is required

---

# Task

Return the maximum coins obtainable after bursting all balloons.

---

# Input Format

First line contains integer:

```text
N
```

representing number of balloons.

Second line contains:

```text
N space-separated integers
```

representing balloon values.

---

# Output Format

Print the maximum obtainable coins.

---

# Constraints

* **1 ≤ N ≤ 500**
* **0 ≤ nums[i] ≤ 100**

---

# Important Note

Use:

```text
64-bit integer types
```

because total coins may exceed 32-bit integer range.

---

# Sample Input 1

```text
4
3 1 5 8
```

---

# Sample Output 1

```text
167
```

---

# Explanation

Array:

```text
[3, 1, 5, 8]
```

Optimal bursting order:

```text
1 → 5 → 3 → 8
```

Step-by-step:

```text
Burst 1:
3 × 1 × 5 = 15

Remaining:
[3, 5, 8]

Burst 5:
3 × 5 × 8 = 120

Remaining:
[3, 8]

Burst 3:
1 × 3 × 8 = 24

Remaining:
[8]

Burst 8:
1 × 8 × 1 = 8
```

Total:

```text
15 + 120 + 24 + 8 = 167
```

---

# Sample Input 2

```text
3
1 5 10
```

---

# Sample Output 2

```text
70
```

---

# Explanation

Optimal order:

```text
5 → 1 → 10
```

Coins:

```text
1 × 5 × 10 = 50
1 × 1 × 10 = 10
1 × 10 × 1 = 10
```

Total:

```text
70
```

---

# Sample Input 3

```text
5
7 9 8 0 7
```

---

# Sample Output 3

```text
623
```

---

# Explanation

Bursting balloons in an optimal interval order produces:

```text
623
```

coins.

Zero-valued balloons can significantly affect future neighbor multiplications.

Dynamic programming explores all interval partitions efficiently.

---

# Recommended Approach

Efficient interview solution uses:

```text
Interval Dynamic Programming
```

---

# Key Insight

Instead of deciding:

```text
which balloon to burst first
```

think in reverse:

```text
which balloon is burst last in an interval
```

This removes dependency issues and enables interval partitioning.

---

# Optimal Strategy

Add virtual balloons:

```text
1
```

at both ends.

Transform array:

```text
nums = [1] + originalNums + [1]
```

Define:

```text
dp[l][r]
```

as the maximum coins obtainable by bursting balloons strictly between:

```text
l and r
```

For every interval:

```text
(l, r)
```

try every balloon:

```text
k
```

as the last balloon burst.

Transition:

```text
dp[l][r] =
max(
    dp[l][k]
    + dp[k][r]
    + nums[l] × nums[k] × nums[r]
)
```

where:

```text
l < k < r
```

---

# Expected Complexity

## Interval DP Approach

### Time Complexity

```text
O(N³)
```

because:

* there are `O(N²)` intervals
* each interval tries `O(N)` partition points

---

### Space Complexity

```text
O(N²)
```

for DP table storage.

---

# Alternative Approaches

| Approach              | Time Complexity | Space Complexity |
| --------------------- | --------------- | ---------------- |
| Pure Recursion        | Exponential     | O(N)             |
| Memoized Recursion    | O(N³)           | O(N²)            |
| Bottom-Up Interval DP | O(N³)           | O(N²)            |

---

# Edge Cases

Your solution should correctly handle:

* single balloon
* all zero balloons
* duplicate values
* increasing sequences
* decreasing sequences
* sparse zeros
* very large multiplications
* optimal non-greedy bursting orders

---

# Object-Oriented Design Expectations

Recommended classes:

| Class              | Responsibility               |
| ------------------ | ---------------------------- |
| `BalloonGame`      | Core DP optimization logic   |
| `IntervalSolver`   | Handles interval transitions |
| `MemoizationCache` | Stores computed DP states    |
| `InputProcessor`   | Parses input data            |

---

# Follow-Up Interview Questions

Interviewers may ask:

* Why does greedy fail?
* Why is "burst last" easier than "burst first"?
* Can space be optimized?
* How would you reconstruct the bursting order?
* Can this be parallelized?

---

# Execution Time Limit

```text
2 seconds
```

```
```