# **Problem 1077: Minimum Path with Exactly K Jumps**

**Company:** Capgemini

**Topic:** Dynamic Programming / Graph Traversal

---

## **Problem Description**

A robotic delivery system operates on a linear transportation grid represented as an array.
Each position in the array contains a cost associated with landing on that location.

The robot starts at index `0` and must reach index `N-1`.

However, the robot has a restricted movement engine:

* In one move, it may jump forward by:

  * `1 step`
  * `2 steps`
  * `3 steps`

Additionally, the robot must reach the destination using:

```text id="k7m2qa"
Exactly K jumps
```

Your task is to calculate the minimum possible total traversal cost required to reach the destination under this constraint.

---

## **Cost Rules**

* The cost of a path equals the sum of:

  * Starting position cost
  * Costs of all visited landing positions
  * Destination cost

* Every jump must remain within array bounds.

---

## **Task**

Determine the minimum achievable cost to reach index:

```text id="m2v9xp"
N - 1
```

using exactly:

```text id="x8m1zk"
K jumps
```

If reaching the destination using exactly `K` jumps is impossible, print:

```text id="p4m2vx"
-1
```

---

## **Input Format**

* First line: integers **N** and **K**

  * `N` → size of array
  * `K` → exact number of jumps required

* Second line: `N` integers representing traversal costs

---

## **Constraints**

* **1 ≤ N ≤ 10³**
* **1 ≤ K ≤ 10³**
* **1 ≤ cost[i] ≤ 10⁶**

---

## **Output Format**

Print a single integer — the minimum traversal cost using exactly `K` jumps.

If no valid path exists, print:

```text id="r9m8qa"
-1
```

---

## **Sample Input 1**

```text id="u3m1zk"
5 2
1 2 3 4 5
```

---

## **Sample Output 1**

```text id="f8m2xp"
8
```

---

## **Explanation**

Possible valid paths with exactly 2 jumps:

```text id="n7m9qa"
0 → 1 → 4
0 → 2 → 4
```

Path costs:

```text id="z2m8vx"
0 → 1 → 4 = 1 + 2 + 5 = 8
0 → 2 → 4 = 1 + 3 + 5 = 9
```

Minimum traversal cost:

```text id="q1m2zk"
8
```

---

## **Sample Input 2**

```text id="m8v1qa"
6 3
5 1 2 10 6 2
```

---

## **Sample Output 2**

```text id="x2m9xp"
10
```

---

## **Explanation**

Optimal valid traversal:

```text id="k4m8qa"
0 → 1 → 2 → 5
```

Jump sizes:

```text id="v7m2zk"
1, 1, 3
```

Exactly 3 jumps used.

Total cost:

```text id="a1m8vx"
5 + 1 + 2 + 2 = 10
```

---

## **Sample Input 3**

```text id="t8m1qa"
4 1
3 7 2 8
```

---

## **Sample Output 3**

```text id="g2m8zk"
11
```

---

## **Explanation**

Direct jump:

```text id="h9m2vx"
0 → 3
```

Jump length:

```text id="k2m1qa"
3
```

Allowed because maximum jump length is `3`.

Cost:

```text id="r7m2zk"
3 + 8 = 11
```

---

## **Sample Input 4**

```text id="u1m8xp"
5 1
1 2 3 4 5
```

---

## **Sample Output 4**

```text id="m4k8qa"
-1
```

---

## **Explanation**

Destination index:

```text id="v8m2zk"
4
```

Cannot be reached in a single jump because:

```text id="x1m9vx"
Maximum jump size = 3
```

Hence no valid path exists.

---

## **Dynamic Programming Insight**

Define:

```text id="z7m2qp"
dp[i][j]
```

where:

> `dp[i][j]` = minimum cost to reach index `i` using exactly `j` jumps.

Transition:

```text id="u4m8zk"
dp[i][j] =
cost[i] +
min(
    dp[i-1][j-1],
    dp[i-2][j-1],
    dp[i-3][j-1]
)
```

if previous positions exist.

---

## **Expected Complexity**

* **Time Complexity:** `O(N × K)`
* **Space Complexity:** `O(N × K)`

---

## **Optimization**

Space optimization is possible using rolling DP states.

---

## **Execution Time Limit**

**10 seconds**
