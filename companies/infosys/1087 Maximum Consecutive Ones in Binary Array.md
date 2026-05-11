# **Problem 1087: Maximum Consecutive Ones in Binary Array**

**Company:** Infosys

**Topic:** Arrays

---

## **Problem Description**

A network monitoring system continuously records server availability status every second.

The monitoring data is stored as a binary array where:

* `1` → server was active
* `0` → server was inactive

System engineers want to identify the longest continuous uptime streak recorded in the monitoring log.

Your task is to determine the maximum number of consecutive `1`s present in the binary array.

---

## **Task**

Given a binary array, compute the length of the longest contiguous sequence containing only:

```text id="m2v8zk"
1
```

---

## **Important Notes**

* The sequence must contain consecutive elements only
* A single `1` is also considered a valid sequence
* If the array contains no `1`, return `0`

---

## **Input Format**

* First line: integer **N** — size of the binary array
* Second line: `N` space-separated integers containing only `0` and `1`

---

## **Constraints**

* **1 ≤ N ≤ 10⁶**
* Array elements are either `0` or `1`

---

## **Output Format**

Print a single integer — the maximum number of consecutive ones.

---

## **Sample Input 1**

```text id="x7m1qa"
10
1 1 0 1 1 1 0 1 1 0
```

---

## **Sample Output 1**

```text id="u3m8qp"
3
```

---

## **Explanation**

Consecutive groups of ones:

```text id="f9m1zk"
1 1
1 1 1
1 1
```

Longest streak:

```text id="r2m8vx"
1 1 1
```

Length:

```text id="n7m2qa"
3
```

---

## **Sample Input 2**

```text id="p4m9xp"
7
1 1 1 1 1 1 1
```

---

## **Sample Output 2**

```text id="v1m8zk"
7
```

---

## **Explanation**

Entire array contains only ones.

Hence maximum consecutive count equals array size.

---

## **Sample Input 3**

```text id="g8m2vx"
8
0 0 0 0 0 0 0 0
```

---

## **Sample Output 3**

```text id="x2m1qa"
0
```

---

## **Explanation**

The array contains no active streaks.

Hence result is:

```text id="m9v2zk"
0
```

---

## **Sample Input 4**

```text id="k4m8qp"
12
1 0 1 1 0 1 1 1 1 0 1 1
```

---

## **Sample Output 4**

```text id="u7m1xp"
4
```

---

## **Explanation**

Longest contiguous block of ones:

```text id="m4k8qa"
1 1 1 1
```

Length:

```text id="v8m2zk"
4
```

---

## **Efficient Traversal Insight**

Maintain:

```text id="x1m9vx"
currentCount
maximumCount
```

Traverse the array:

* If current element is `1`

  * increment current streak
* If current element is `0`

  * reset current streak

Continuously update the maximum streak length.

---

## **Optimized Strategy**

This problem can be solved using a single linear traversal without additional data structures.

---

## **Expected Complexity**

### Single Pass Traversal

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(1)`

Where:

* `N` = size of the array

---

## **Execution Time Limit**

**10 seconds**