# **Problem 119: Self-Sufficient Book Buyer**

**Company:** LTIMindtree

**Category:** Greedy Algorithms / Sorting

**Difficulty:** Hard

---

# **Problem Description**

A student plans to purchase:

```text id="m2v8zk"
N
```

technical books.

For every book:

* completing a freelance job earns a certain amount of money
* purchasing the corresponding book costs a certain amount

The student may process the books in:

```text id="x7m1qa"
any order
```

For every transaction:

1. The student first completes the job and earns money
2. The student then purchases the corresponding book

Any remaining balance after a transaction can be used for future purchases.

Your task is to determine the:

```text id="u3m8qp"
minimum initial capital
```

required so that the student can complete all transactions successfully without the balance ever becoming negative.

This problem evaluates a candidate’s understanding of:

* greedy ordering strategies
* balance flow optimization
* deficit minimization
* sorting-based scheduling
* prefix deficit analysis

Interviewers expect candidates to identify how transaction ordering impacts the minimum required starting capital.

---

# **Task**

You are given two integer arrays:

```text id="f9m1zk"
EarnArray
```

and:

```text id="r2m8vx"
CostArray
```

where:

* `EarnArray[i]` = money earned from the `i-th` freelance job
* `CostArray[i]` = cost of the corresponding `i-th` book

For every transaction:

```text id="n7m2qa"
netChange[i] = EarnArray[i] - CostArray[i]
```

The student may reorder transactions arbitrarily.

Return the minimum initial capital required so that:

```text id="p4m9xp"
balance >= 0
```

at every step.

---

# **Important Rules**

* Transactions may be reordered in any permutation
* The student earns money before purchasing the book
* Balance must never become negative
* Surplus balance carries forward to future transactions
* Arrays always have equal length

---

# **Input Format**

First line contains integer:

```text id="v1m8zk"
N
```

representing number of books/jobs.

Second line contains:

```text id="g8m2vx"
N space-separated integers
```

representing:

```text id="x2m1qa"
EarnArray
```

Third line contains:

```text id="m9v2zk"
N space-separated integers
```

representing:

```text id="k4m8qp"
CostArray
```

---

# **Output Format**

Print a single integer representing:

```text id="u7m1xp"
minimum initial capital required
```

---

# **Constraints**

* **1 ≤ N ≤ 2 × 10⁵**
* **0 ≤ EarnArray[i], CostArray[i] ≤ 10⁹**

---

# **Sample Input 1**

```text id="m4k8qa"
3
3 1 2
5 2 2
```

---

# **Sample Output 1**

```text id="v8m2zk"
2
```

---

# **Explanation**

Transactions:

| Earn | Cost | Net Change |
| ---- | ---- | ---------- |
| 3    | 5    | -2         |
| 1    | 2    | -1         |
| 2    | 2    | 0          |

Optimal order:

```text id="x1m9vx"
(2,2) → (3,5) → (1,2)
```

Balance simulation with initial capital:

```text id="z7m2qp"
2
```

| Step  | Balance Before | Earn | Cost | Balance After |
| ----- | -------------- | ---- | ---- | ------------- |
| Start | 2              | -    | -    | 2             |
| 1     | 2              | +2   | -2   | 2             |
| 2     | 2              | +3   | -5   | 0             |
| 3     | 0              | +1   | -2   | -1            |

This fails.

Try another order:

```text id="u4m8zk"
(3,5) → (2,2) → (1,2)
```

| Step  | Balance Before | Earn | Cost | Balance After |
| ----- | -------------- | ---- | ---- | ------------- |
| Start | 2              | -    | -    | 2             |
| 1     | 2              | +3   | -5   | 0             |
| 2     | 0              | +2   | -2   | 0             |
| 3     | 0              | +1   | -2   | -1            |

Still insufficient.

Minimum valid initial capital:

```text id="k2m1qa"
3
```

---

# **Sample Input 2**

```text id="r7m2zk"
4
5 3 4 2
2 2 3 1
```

---

# **Sample Output 2**

```text id="u1m8xp"
0
```

---

# **Explanation**

Every transaction has non-negative net change.

Thus no initial capital is required.

---

# **Sample Input 3**

```text id="m4k8qa"
3
1 1 1
4 4 4
```

---

# **Sample Output 3**

```text id="v8m2zk"
9
```

---

# **Explanation**

Every transaction loses:

```text id="x1m9vx"
3
```

units.

Total cumulative deficit:

```text id="z7m2qp"
9
```

Thus minimum starting capital required is:

```text id="u4m8zk"
9
```

---

# **Sample Input 4**

```text id="k2m1qa"
5
4 2 7 1 3
5 2 4 6 3
```

---

# **Sample Output 4**

```text id="r7m2zk"
1
```

---

# **Explanation**

An optimal ordering minimizes the largest temporary deficit.

The minimum required starting capital is:

```text id="u1m8xp"
1
```

---

# **Why Naive Approaches Fail**

Trying every permutation of transactions requires:

```text id="m4k8qa"
O(N!)
```

time complexity.

This becomes computationally infeasible even for moderate values of:

```text id="v8m2zk"
N
```

---

# **Key Greedy Observation**

Each transaction contributes a balance change:

```text id="x1m9vx"
netChange[i] = EarnArray[i] - CostArray[i]
```

Transactions with larger profits improve future purchasing power.

To minimize the required initial capital:

* process highly profitable transactions earlier
* postpone larger losses until sufficient balance has accumulated

---

# **Greedy Sorting Strategy**

Construct transaction pairs:

```text id="z7m2qp"
(EarnArray[i], CostArray[i])
```

Sort transactions by:

```text id="u4m8zk"
netChange[i]
```

in descending order.

This prioritizes:

* profitable transactions first
* smaller losses before larger losses

---

# **Efficient Algorithm**

---

## Step 1 — Compute Net Changes

For every transaction:

```text id="k2m1qa"
netChange[i] = EarnArray[i] - CostArray[i]
```

---

## Step 2 — Sort Transactions

Sort transactions in descending order of:

```text id="r7m2zk"
netChange[i]
```

---

## Step 3 — Simulate Balance Flow

Maintain:

| Variable         | Purpose                           |
| ---------------- | --------------------------------- |
| `runningBalance` | Cumulative balance change         |
| `minimumBalance` | Lowest cumulative balance reached |

For every transaction:

```text id="u1m8xp"
runningBalance += netChange[i]
```

Track the minimum balance encountered.

---

## Step 4 — Compute Minimum Initial Capital

Suppose the lowest cumulative balance becomes:

```text id="m4k8qa"
-X
```

Then initial capital required is:

```text id="v8m2zk"
X
```

Otherwise answer is:

```text id="x1m9vx"
0
```

---

# **Balance Invariant**

At every step:

```text id="z7m2qp"
currentBalance =
initialCapital + cumulative(netChange)
```

The goal is to ensure:

```text id="u4m8zk"
currentBalance >= 0
```

throughout the entire process.

---

# **Why This Works**

By maximizing balance gains early:

* future deficits become easier to absorb
* the minimum cumulative balance is optimized

Thus the required initial capital is minimized.

---

# **Recommended Data Structures**

| Structure               | Purpose                   |
| ----------------------- | ------------------------- |
| `Array of Transactions` | Store earn/cost pairs     |
| `Sorting`               | Determine greedy ordering |
| `Integer Variables`     | Track balances            |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* all profitable transactions
* all loss-making transactions
* zero-cost books
* zero-earning jobs
* mixed profit/loss transactions
* large monetary values

---

# **Expected Complexity**

## Optimized Greedy Solution

### Time Complexity

* **O(N log N)**

due to sorting.

---

### Space Complexity

* **O(N)**

for storing transaction information.

---

# **Example Walkthrough**

Input:

```text id="k2m1qa"
EarnArray = [3,1,2]
CostArray = [5,2,2]
```

---

## Compute Net Changes

| Earn | Cost | Net Change |
| ---- | ---- | ---------- |
| 3    | 5    | -2         |
| 1    | 2    | -1         |
| 2    | 2    | 0          |

---

## Sort by Net Change Descending

Order:

```text id="r7m2zk"
(2,2) → (1,2) → (3,5)
```

Net changes:

```text id="u1m8xp"
0, -1, -2
```

---

## Cumulative Balances

| Step | Running Balance |
| ---- | --------------- |
| 1    | 0               |
| 2    | -1              |
| 3    | -3              |

Lowest balance:

```text id="m4k8qa"
-3
```

Thus minimum initial capital required:

```text id="v8m2zk"
3
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Priority queue scheduling
* Prefix deficit minimization
* Job sequencing analogies
* Dynamic programming variants

---

# **Follow-Up Variants**

Interviewers may ask:

* Return optimal transaction ordering
* Restrict allowed reorderings
* Minimize maximum temporary debt
* Multiple books per job
* Online transaction insertion

---

# **Execution Time Limit**

**5 seconds**