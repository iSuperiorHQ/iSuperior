# **Problem 114: Stock Buy and Sell for Maximum Profit**

**Company:** Deloitte

**Category:** Arrays / Greedy Algorithms

**Difficulty:** Easy-Medium

---

# **Problem Description**

A financial analytics platform records the daily market price of a stock over a period of time.

An investor is allowed to:

* buy the stock at most once
* sell the stock at most once

The selling operation must occur strictly after the buying operation.

Your task is to determine the:

```text id="m2v8zk"
maximum possible profit
```

that can be achieved from a single transaction.

If no profitable transaction is possible, return:

```text id="x7m1qa"
0
```

This problem evaluates a candidate’s understanding of:

* greedy optimization
* sequential state tracking
* running minimum maintenance
* single-pass array processing

---

# **Task**

Given an integer array:

```text id="u3m8qp"
prices
```

where:

```text id="f9m1zk"
prices[i]
```

represents the stock price on day:

```text id="r2m8vx"
i
```

return the maximum profit achievable from at most one buy and one sell operation.

---

# **Important Rules**

* You must buy before you sell
* Only one transaction is allowed
* Selling on the same day as buying is NOT allowed
* A valid transaction requires at least two different days
* If no profit is possible, return:

```text id="n7m2qa"
0
```

---

# **Input Format**

First line contains integer:

```text id="p4m9xp"
N
```

representing number of days.

Second line contains:

```text id="v1m8zk"
N space-separated integers
```

representing stock prices.

---

# **Output Format**

Print a single integer representing:

```text id="g8m2vx"
maximum achievable profit
```

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* **0 ≤ prices[i] ≤ 10⁹**

---

# **Sample Input 1**

```text id="x2m1qa"
6
7 1 5 3 6 4
```

---

# **Sample Output 1**

```text id="m9v2zk"
5
```

---

# **Explanation**

Best transaction:

| Operation | Day | Price |
| --------- | --- | ----- |
| Buy       | 1   | 1     |
| Sell      | 4   | 6     |

Profit:

```text id="k4m8qp"
6 - 1 = 5
```

---

# **Sample Input 2**

```text id="u7m1xp"
5
9 8 7 6 5
```

---

# **Sample Output 2**

```text id="m4k8qa"
0
```

---

# **Explanation**

Prices continuously decrease.

No profitable transaction exists.

---

# **Sample Input 3**

```text id="v8m2zk"
8
3 2 6 5 0 3 8 1
```

---

# **Sample Output 3**

```text id="x1m9vx"
8
```

---

# **Explanation**

Optimal transaction:

| Operation | Day | Price |
| --------- | --- | ----- |
| Buy       | 4   | 0     |
| Sell      | 6   | 8     |

Profit:

```text id="z7m2qp"
8 - 0 = 8
```

---

# **Sample Input 4**

```text id="u4m8zk"
1
10
```

---

# **Sample Output 4**

```text id="k2m1qa"
0
```

---

# **Explanation**

Only one day exists.

A valid buy-sell transaction is impossible.

---

# **Naive Brute Force Approach**

A straightforward solution may:

1. Try every possible buy day
2. Try every possible sell day after it
3. Compute all profits

This requires:

```text id="r7m2zk"
O(N²)
```

time complexity.

Too slow for large datasets.

---

# **Key Greedy Observation**

At every day:

```text id="u1m8xp"
maximum profit
=
current price - minimum price seen earlier
```

Thus while traversing the array:

* continuously track minimum stock price encountered so far
* compute profit if selling today
* update global maximum profit

---

# **Efficient Single-Pass Strategy**

Maintain two variables:

| Variable    | Purpose                         |
| ----------- | ------------------------------- |
| `minPrice`  | Minimum stock price seen so far |
| `maxProfit` | Best profit found so far        |

---

# **Efficient Algorithm**

Traverse array from left to right.

---

## Step 1 — Update Minimum Price

If current price is smaller than:

```text id="m4k8qa"
minPrice
```

update minimum.

---

## Step 2 — Compute Potential Profit

Potential profit if selling today:

```text id="v8m2zk"
currentPrice - minPrice
```

---

## Step 3 — Update Global Profit

If current profit exceeds:

```text id="x1m9vx"
maxProfit
```

update answer.

---

# **Why This Works**

For every day:

* the algorithm remembers the cheapest buying opportunity seen earlier
* evaluates the best possible sell on the current day

Thus every valid transaction is considered implicitly in a single traversal.

---

# **Recommended Data Structures**

| Structure           | Purpose                                |
| ------------------- | -------------------------------------- |
| `Array`             | Store prices                           |
| `Integer Variables` | Track minimum price and maximum profit |

No extra arrays are required.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* strictly decreasing prices
* single-element arrays
* repeated prices
* zero-valued prices
* very large price values
* maximum profit occurring late in array

---

# **Expected Complexity**

## Optimized Greedy Solution

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

```text id="z7m2qp"
[7,1,5,3,6,4]
```

---

## Traversal Process

| Day | Price | Minimum Price | Potential Profit | Maximum Profit |
| --- | ----- | ------------- | ---------------- | -------------- |
| 0   | 7     | 7             | 0                | 0              |
| 1   | 1     | 1             | 0                | 0              |
| 2   | 5     | 1             | 4                | 4              |
| 3   | 3     | 1             | 2                | 4              |
| 4   | 6     | 1             | 5                | 5              |
| 5   | 4     | 1             | 3                | 5              |

Final answer:

```text id="u4m8zk"
5
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Dynamic Programming interpretation
* Kadane’s Algorithm transformation
* Multiple transaction variants
* Sliding window misconceptions

---

# **Follow-Up Variants**

Interviewers may ask:

* Unlimited transactions allowed
* At most K transactions
* Transaction fee included
* Cooldown period after selling
* Return actual buy/sell indices

---

# **Execution Time Limit**

**3 seconds**