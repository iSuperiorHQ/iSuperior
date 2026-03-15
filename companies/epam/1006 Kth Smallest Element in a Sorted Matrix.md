# **Problem 1006: Kth Smallest Element in a Sorted Matrix**

**Company:** EPAM

---

## **Problem Statement**

You are given an **n × n matrix** where:

* Each **row** is sorted in **ascending order**.
* Each **column** is also sorted in **ascending order**.

Your task is to find the **kth smallest element** in the matrix.

Note that it is the **kth smallest element in the sorted order of all elements in the matrix**, not the kth distinct element.

---

## **Input Format**

* The **first line** contains an integer **n**, the size of the matrix.
* The **next n lines** each contain **n integers** representing the matrix.
* The **last line** contains an integer **k**.

---

## **Constraints**

* **1 ≤ n ≤ 300**
* **1 ≤ k ≤ n²**
* **-10⁹ ≤ matrix[i][j] ≤ 10⁹**
* Each **row and column is sorted in ascending order**.

---

## **Output Format**

Return the **kth smallest element** in the matrix.

---

## **Sample Input**

```
3
1 5 9
10 11 13
12 13 15
8
```

---

## **Sample Output**

```
13
```

---

## **Explanation**

All elements in sorted order:

```
1, 5, 9, 10, 11, 12, 13, 13, 15
```

The **8th smallest element** is:

```
13
```

---

## **Execution Time Limit**

**10 seconds**