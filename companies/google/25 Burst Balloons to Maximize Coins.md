# **Problem 25: Burst Balloons to Maximize Coins**

**Company:** Google

**Category:** Dynamic Programming / Interval DP

**Difficulty:** Hard

---

# **Problem Description**

You are given `n` balloons arranged in a row.

Each balloon contains a positive integer represented by an array:

```text
nums[i]
```

When you burst the `i-th` balloon, you gain coins equal to:

```text
nums[left] × nums[i] × nums[right]
```

where:

* `left` is the nearest unburst balloon to the left of index `i`
* `right` is the nearest unburst balloon to the right of index `i`

After bursting balloon `i`, the balloon disappears from the row.

If there is no balloon on either side, assume its value is:

```text
1
```

Your task is to determine the maximum number of coins obtainable by bursting all balloons in an optimal order.

---

# **Business Requirement**

A gaming platform rewards users based on strategic elimination of targets.

Each target contributes reward points depending on neighboring active targets.

The system must determine the optimal elimination sequence maximizing total reward.

---

# **Task**

Find the maximum coins obtainable after bursting all balloons optimally.

---

# **Function Signature**

```cpp
int maxCoins(vector<int>& nums)
```

---

# **Input Format**

First line contains integer:

```text
n
```

representing number of balloons.

Second line contains `n` space-separated integers:

```text
nums[i]
```

representing balloon values.

---

# **Output Format**

Print a single integer representing maximum coins obtainable.

---

# **Constraints**

* **1 ≤ n ≤ 300**
* **1 ≤ nums[i] ≤ 100**

---

# **Sample Input 1**

```text
4
3 1 5 8
```

---

# **Sample Output 1**

```text
167
```

---

# **Explanation**

One optimal bursting order is:

```text
1 → 5 → 3 → 8
```

Burst balloon:

```text
1
```

Coins earned:

```text
3 × 1 × 5 = 15
```

Remaining balloons:

```text
3 5 8
```

Burst balloon:

```text
5
```

Coins earned:

```text
3 × 5 × 8 = 120
```

Remaining balloons:

```text
3 8
```

Burst balloon:

```text
3
```

Coins earned:

```text
1 × 3 × 8 = 24
```

Burst balloon:

```text
8
```

Coins earned:

```text
1 × 8 × 1 = 8
```

Total coins:

```text
15 + 120 + 24 + 8 = 167
```

---

# **Sample Input 2**

```text
3
1 5 1
```

---

# **Sample Output 2**

```text
15
```

---

# **Explanation**

One optimal bursting order is:

```text
1 → 1 → 5
```

First burst:

```text
1 × 1 × 5 = 5
```

Second burst:

```text
1 × 1 × 5 = 5
```

Final burst:

```text
1 × 5 × 1 = 5
```

Total coins:

```text
15
```

---

# **Sample Input 3**

```text
1
7
```

---

# **Sample Output 3**

```text
7
```

---

# **Explanation**

Only one balloon exists.

Coins earned:

```text
1 × 7 × 1 = 7
```

---

# **Key Observation**

Choosing the first balloon to burst is difficult because neighboring balloons continuously change after every operation.

Instead, think in reverse:

```text
Which balloon is burst last inside an interval?
```

If balloon `k` is the last balloon burst between indices:

```text
left and right
```

then its neighboring balloons become fixed:

```text
nums[left]
nums[right]
```

This removes dependency issues and enables interval dynamic programming.

---

# **Approaches**

| Approach | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| Recursive Brute Force | O(n!) | O(n) |
| Memoized Recursion | O(n³) | O(n²) |
| Bottom-Up Interval DP | O(n³) | O(n²) |

---

# **Recommended Interview Approach**

Preferred interview solution:

```text
Bottom-Up Interval Dynamic Programming
```

because it efficiently handles overlapping subproblems.

---

# **Efficient Strategy**

1. Add virtual balloons having value:

```text
1
```

at both ends of the array.

2. Define:

```text
dp[left][right]
```

as maximum coins obtainable by bursting all balloons strictly inside interval:

```text
(left, right)
```

3. For every interval, try every balloon `k` as the last balloon burst.

4. Transition:

```text
dp[left][right] =
max(
    dp[left][k]
    + dp[k][right]
    + nums[left] × nums[k] × nums[right]
)
```

5. Final answer becomes:

```text
dp[0][n+1]
```

after padding the array.

---

# **Example Walkthrough**

Input:

```text
3 1 5 8
```

After adding virtual balloons:

```text
1 3 1 5 8 1
```

Suppose balloon:

```text
5
```

is chosen as the last balloon burst inside some interval.

Its neighboring balloons become fixed, allowing independent computation of left and right subintervals.

Dynamic programming computes the best possible partition.

Final answer:

```text
167
```

---

# **Expected Complexity**

## Bottom-Up Interval DP

### Time Complexity

* **O(n³)**

because:

* interval length → `O(n)`
* interval start index → `O(n)`
* every possible last balloon → `O(n)`

---

### Space Complexity

* **O(n²)**

for storing DP states.

---

# **Edge Cases**

Your solution should correctly handle:

* single balloon
* all balloons equal
* strictly increasing values
* strictly decreasing values
* maximum constraints
* multiple optimal bursting orders

---

# **Follow-Up Questions**

Interviewers may ask:

* Why does greedy fail?
* Why is "burst last" easier than "burst first"?
* Can the bursting order be reconstructed?
* Can interval DP solve matrix-chain multiplication?
* Can memory usage be optimized?

---

# **Execution Time Limit**

```text
2 seconds
```