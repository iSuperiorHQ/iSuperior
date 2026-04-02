# **Problem 1018: Search in a Strictly Sorted 2D Matrix**

**Company:** Microsoft

**Topic:** Binary Search / Matrix

---

## **Problem Statement**

You are given a **2D matrix of size m × n** with the following properties:

1. Each **row is sorted in strictly increasing order**.
2. The **first element of each row is greater than the last element of the previous row**.

This means that if the matrix is flattened row-wise, it forms a **single strictly increasing sorted array**.

---

### **Task**

Given an integer **target**, determine whether the target exists in the matrix.

Return **true** if the target is found, otherwise return **false**.

---

## **Input Format**

* The **first line** contains two integers **m** and **n** (rows and columns).
* The next **m lines** contain **n integers each**, representing the matrix.
* The last line contains an integer **target**.

---

## **Constraints**

* **1 ≤ m, n ≤ 300**
* **-10⁹ ≤ matrix[i][j] ≤ 10⁹**
* Matrix elements are **strictly increasing row-wise and across rows**
* **-10⁹ ≤ target ≤ 10⁹**

---

## **Output Format**

Return:

* **true** → if target exists in the matrix
* **false** → otherwise

---

## **Sample Input 1**

```text
3 4
1 3 5 7
10 11 16 20
23 30 34 60
3
```

---

## **Sample Output 1**

```text
true
```

---

## **Explanation**

The matrix can be viewed as:

```text
[1, 3, 5, 7, 10, 11, 16, 20, 23, 30, 34, 60]
```

Since **3 exists**, the answer is **true**.

---

## **Sample Input 2**

```text
3 4
1 3 5 7
10 11 16 20
23 30 34 60
13
```

---

## **Sample Output 2**

```text
false
```

---

## **Explanation**

The number **13** does not exist in the matrix.

---

## **Key Insight**

Since the matrix behaves like a **sorted 1D array**, the problem can be solved efficiently using:

* **Binary Search on index range [0, m × n - 1]**
* Time Complexity: **O(log(m × n))**

---

## **Execution Time Limit**

**10 seconds**