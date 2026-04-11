# **Problem 1046: Manual Execution of Quick Sort Partition Logic**

**Company:** TCS

**Topic:** Sorting

---

## **Problem Description**

You are given an array of integers. Your task is to manually execute the **partition step of the Quick Sort algorithm** using a chosen pivot element.

In Quick Sort, partitioning rearranges the array such that:

* Elements **less than or equal to the pivot** are placed on the left
* Elements **greater than the pivot** are placed on the right

---

## **Task**

* Select the **last element of the array as the pivot**
* Rearrange the array using the **partition logic**
* Return the array after one complete partition operation
* Also output the **final position of the pivot element**

---

## **Input Format**

* The first line contains an integer **n** — number of elements
* The second line contains **n integers** representing the array

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **-10⁹ ≤ arr[i] ≤ 10⁹**

---

## **Output Format**

* First line: array after partition
* Second line: index of pivot after partition (0-based indexing)

---

## **Sample Input**

```text id="0k3mwp"
6
10 7 8 9 1 5
```

---

## **Sample Output**

```text id="3bqv7r"
1 5 8 9 10 7
1
```

---

## **Explanation**

Initial array:

```text id="b2y9xk"
[10, 7, 8, 9, 1, 5]
```

Pivot = **5**

After partition:

* Elements ≤ 5 → [1, 5]
* Elements > 5 → [8, 9, 10, 7]

Final array:

```text id="n8v2lx"
[1, 5, 8, 9, 10, 7]
```

Pivot index = **1**

---

## **What they check:**

* Understanding of **Quick Sort partition logic**
* Correct placement of pivot
* In-place swapping operations

---

## **Execution Time Limit**

**10 seconds**