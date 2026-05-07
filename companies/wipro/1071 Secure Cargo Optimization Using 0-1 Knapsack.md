# **Problem 1071: Secure Cargo Optimization Using 0/1 Knapsack**

**Company:** Wipro

**Topic:** Dynamic Programming / 0-1 Knapsack

---

## **Problem Description**

A logistics company operates a secure delivery drone with a limited carrying capacity.
Each package has:

* A specific **weight**
* A corresponding **profit value**

Due to safety restrictions, the drone can carry each package **at most once**.

The company wants to maximize the total profit earned from transported packages without exceeding the drone's weight capacity.

You are given:

* `N` packages
* Weight and profit value of each package
* Maximum carrying capacity `W`

Your task is to determine the **maximum achievable profit**.

---

## **Important Constraint**

Each item can be selected:

```text id="k9m2vx"
Either 0 times or 1 time only
```

This is a classic **0/1 Knapsack** optimization problem.

---

## **Task**

Select the optimal subset of packages such that:

* Total weight ≤ `W`
* Total profit is maximized

---

## **Input Format**

* First line: integers **N** and **W**

  * `N` → number of packages
  * `W` → maximum carrying capacity

* Second line: `N` integers representing package weights

* Third line: `N` integers representing package profit values

---

## **Constraints**

* **1 ≤ N ≤ 10³**
* **1 ≤ W ≤ 10⁵**
* **1 ≤ weight[i] ≤ 10³**
* **1 ≤ value[i] ≤ 10⁶**

---

## **Output Format**

Print a single integer — the maximum profit achievable.

---

## **Sample Input 1**

```text id="m2v8qp"
4 7
1 3 4 5
1 4 5 7
```

---

## **Sample Output 1**

```text id="n7m2zk"
9
```

---

## **Explanation**

Possible selections:

```text id="r4k1qp"
Item 2 + Item 3
Weight = 3 + 4 = 7
Profit = 4 + 5 = 9
```

This is the maximum achievable profit within capacity `7`.

---

## **Sample Input 2**

```text id="z1m8qx"
5 10
2 3 5 7 1
10 5 15 7 6
```

---

## **Sample Output 2**

```text id="p8m2va"
31
```

---

## **Explanation**

Optimal selection:

```text id="h3m9zk"
Items:
Weight → 2 + 5 + 1 = 8
Profit → 10 + 15 + 6 = 31
```

No other valid combination gives higher profit.

---

## **Sample Input 3**

```text id="x2k9vp"
3 2
3 4 5
30 40 50
```

---

## **Sample Output 3**

```text id="t1m8qx"
0
```

---

## **Explanation**

All package weights exceed the carrying capacity.

Hence no package can be selected.

---

## **Dynamic Programming Insight**

Define:

```text id="k7m3qa"
dp[i][w]
```

as:

> Maximum profit achievable using first `i` items with capacity `w`

Transition:

```text id="a2m9vx"
dp[i][w] =
max(
    dp[i-1][w], 
    value[i] + dp[i-1][w-weight[i]]
)
```

if current item can fit.

---

## **Expected Complexity**

### Standard DP

* **Time Complexity:** `O(N × W)`
* **Space Complexity:** `O(N × W)`

---

## **Optimization**

Space can be optimized using a **1D DP array**:

* Optimized Space Complexity: `O(W)`

---

## **Execution Time Limit**

**10 seconds**