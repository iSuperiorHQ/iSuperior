# **Problem 1048: Count Valid Arrays with Constraints**

**Company:** TCS

**Topic:** Dynamic Programming / Combinatorics

---

## **Problem Description**

You are given three integers:

* **n** → length of the array
* **r** → maximum value (each element lies between 1 and r)
* **e** → required value of the last element

Your task is to construct arrays of length **n** that satisfy the given conditions.

---

## **Conditions**

* **arr[0] = 1** (first element is fixed)
* **arr[n - 1] = e** (last element is fixed)
* **1 ≤ arr[i] ≤ r**
* **arr[i] ≠ arr[i - 1]** for all **i > 0** (no two adjacent elements are equal)

---

## **Task**

Return the **total number of valid arrays** satisfying all the above conditions.

---

## **Input Format**

* Three integers **n, r, e**

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **1 ≤ r ≤ 10⁵**
* **1 ≤ e ≤ r**

---

## **Output Format**

* Print a single integer — the number of valid arrays

---

## **Sample Input 1**

```text
n = 4, r = 4, e = 3
```

---

## **Sample Output 1**

```text
7
```

---

## **Explanation**

Valid arrays:

```text
1 2 1 3
1 2 4 3
1 3 1 3
1 3 2 3
1 3 4 3
1 4 1 3
1 4 2 3
```

---

## **Sample Input 2**

```text
n = 3, r = 2, e = 2
```

---

## **Sample Output 2**

```text
0
```

---

## **Explanation**

No valid array exists that satisfies all constraints.

---

## **Sample Input 3**

```text
n = 2, r = 5, e = 4
```

---

## **Sample Output 3**

```text
1
```

---

## **Explanation**

Only one valid array:

```text
1 4
```

---

## **Key Insight**

* This is a **state transition / DP problem**
* At each position:

  * You can choose any value except the previous one
* Track:

  * Ways to end with value **e**
  * Ways to end with values **≠ e**

Efficient solution requires **Dynamic Programming with optimization**.

---

## **What they check:**

* Understanding of **constraints handling**
* Proper **state transitions (DP thinking)**
* Edge cases like:

  * n = 1
  * r = 1
  * e = 1

---

## **Execution Time Limit**

**10 seconds**