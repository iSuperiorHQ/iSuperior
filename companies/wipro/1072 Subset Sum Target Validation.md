# **Problem 1072: Subset Sum Target Validation**

**Company:** Wipro

**Topic:** Dynamic Programming / Backtracking

---

## **Problem Description**

A financial auditing system analyzes transaction batches to determine whether a specific target amount can be formed using a subset of recorded transactions.

You are given:

* An array of positive integers
* A target sum `T`

Your task is to determine whether there exists at least one subset of the array whose elements add up exactly to the target value.

Each element may be used:

```text id="n1m8zk"
At most once
```

---

## **Task**

Determine whether a valid subset exists whose sum equals the target value.

Return:

```text id="x7m2qa"
Possible
```

if such a subset exists.

Otherwise return:

```text id="m9k1xp"
Not Possible
```

---

## **Important Notes**

* Elements do not need to be contiguous
* A subset may contain:

  * One element
  * Multiple elements
  * No element (only when target = 0)
* An empty subset is considered valid only when the target sum is `0`

---

## **Input Format**

* First line: integer **N** — size of array
* Second line: `N` integers representing array elements
* Third line: integer **T** — target sum

---

## **Constraints**

* **1 ≤ N ≤ 200**
* **1 ≤ arr[i] ≤ 10⁴**
* **0 ≤ T ≤ 10⁵**

---

## **Output Format**

Print:

```text id="v2m8qp"
Possible
```

or

```text id="r4m1zk"
Not Possible
```

---

## **Sample Input 1**

```text id="b8m2vx"
6
3 34 4 12 5 2
9
```

---

## **Sample Output 1**

```text id="t1m9qa"
Possible
```

---

## **Explanation**

Subset:

```text id="j7m2xp"
4 + 5 = 9
```

Hence the target sum can be formed.

---

## **Sample Input 2**

```text id="m3v8zk"
5
1 2 6 8 10
7
```

---

## **Sample Output 2**

```text id="k8m2qa"
Possible
```

---

## **Explanation**

Subset:

```text id="x2m9vx"
1 + 6 = 7
```

Hence the target sum exists.

---

## **Sample Input 3**

```text id="v1m8qp"
4
2 4 6 8
5
```

---

## **Sample Output 3**

```text id="p7m2zk"
Not Possible
```

---

## **Explanation**

No subset produces the target sum `5`.

---

## **Sample Input 4**

```text id="g9m1qa"
3
5 10 15
0
```

---

## **Sample Output 4**

```text id="u3m8xp"
Possible
```

---

## **Explanation**

The empty subset:

```text id="a8m2vx"
{}
```

produces sum `0`.

Hence the target sum is achievable.

---

## **Dynamic Programming Insight**

Define:

```text id="k2m9zk"
dp[i][s]
```

where:

> `dp[i][s] = true` if sum `s` can be formed using the first `i` elements.

Transition:

```text id="m7v2qa"
dp[i][s] =
dp[i-1][s]
OR
dp[i-1][s-arr[i]]
```

if the current element can contribute to the sum.

---

## **Expected Complexity**

### Standard DP Approach

* **Time Complexity:** `O(N × T)`
* **Space Complexity:** `O(N × T)`

---

## **Optimization**

Using a 1D DP array:

* Optimized Space Complexity: `O(T)`

---

## **Execution Time Limit**

**10 seconds**