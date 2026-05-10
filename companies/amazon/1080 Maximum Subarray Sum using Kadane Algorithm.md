# **Problem 1080: Maximum Subarray Sum using Kadane Algorithm**

**Company:** Amazon

**Topic:** Arrays / Dynamic Programming

---

## **Problem Description**

A financial analytics platform tracks daily profit and loss values of a trading system.

Each integer in the array represents:

* Positive value → profit
* Negative value → loss

The company wants to identify the continuous time period that generated the highest overall profit.

Your task is to determine the maximum possible sum of any contiguous subarray.

A subarray must:

```text id="m2v8zk"
Contain consecutive elements only
```

---

## **Task**

Given an integer array, compute the maximum sum obtainable from any contiguous subarray.

---

## **Input Format**

* First line: integer **N** — size of array
* Second line: `N` space-separated integers representing array elements

---

## **Constraints**

* **1 ≤ N ≤ 10⁶**
* **-10⁹ ≤ arr[i] ≤ 10⁹**

---

## **Output Format**

Print a single integer — the maximum contiguous subarray sum.

---

## **Sample Input 1**

```text id="x7m1qa"
9
-2 1 -3 4 -1 2 1 -5 4
```

---

## **Sample Output 1**

```text id="u3m8qp"
6
```

---

## **Explanation**

Optimal contiguous subarray:

```text id="f9m1zk"
4 -1 2 1
```

Sum:

```text id="r2m8vx"
4 + (-1) + 2 + 1 = 6
```

No other contiguous segment produces a larger sum.

---

## **Sample Input 2**

```text id="n7m2qa"
5
1 2 3 4 5
```

---

## **Sample Output 2**

```text id="p4m9xp"
15
```

---

## **Explanation**

All elements are positive.

Hence the entire array forms the optimal subarray.

```text id="v1m8zk"
1 + 2 + 3 + 4 + 5 = 15
```

---

## **Sample Input 3**

```text id="g8m2vx"
4
-8 -3 -6 -2
```

---

## **Sample Output 3**

```text id="x2m1qa"
-2
```

---

## **Explanation**

When all elements are negative, the answer is the maximum individual element.

Optimal subarray:

```text id="m9v2zk"
[-2]
```

---

## **Sample Input 4**

```text id="k4m8qp"
6
5 -2 3 4 -1 2
```

---

## **Sample Output 4**

```text id="u7m1xp"
11
```

---

## **Explanation**

Optimal contiguous subarray:

```text id="m4k8qa"
5 -2 3 4 -1 2
```

Sum:

```text id="v8m2zk"
5 - 2 + 3 + 4 - 1 + 2 = 11
```

The optimal contiguous subarray spans the complete array.

---

## **Kadane’s Algorithm Insight**

The core idea:

At every index:

* Either extend the current subarray
* Or start a new subarray from the current element

Maintain:

```text id="x1m9vx"
currentSum
maxSum
```

Transition:

```text id="z7m2qp"
currentSum =
max(arr[i], currentSum + arr[i])
```

Update:

```text id="u4m8zk"
maxSum =
max(maxSum, currentSum)
```

---

## **Why Kadane’s Algorithm Works**

If the running sum becomes smaller than the current element itself, continuing the previous subarray is no longer beneficial.

Hence we restart the subarray from the current position.

---

## **Expected Complexity**

### Optimized Kadane Approach

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(1)`

---

## **Execution Time Limit**

**10 seconds**