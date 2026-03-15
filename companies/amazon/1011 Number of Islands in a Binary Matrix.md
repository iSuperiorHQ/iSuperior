# **Problem 1011: Number of Islands in a Binary Matrix**

**Company:** Amazon

**Topic:** Graph / BFS / DFS

---

## **Problem Statement**

You are given an **m × n binary matrix** where:

* **1** represents land
* **0** represents water

An **island** is a group of connected **1s** that are connected **horizontally or vertically**.

Your task is to determine the **number of islands** present in the grid.

---

## **Input Format**

* The **first line** contains two integers **m** and **n**.
* The next **m lines** contain **n integers (0 or 1)** representing the grid.

---

## **Constraints**

* **1 ≤ m, n ≤ 300**
* Grid values are **0 or 1**

---

## **Output Format**

Return an integer representing the **number of islands**.

---

## **Sample Input**

```
4 5
1 1 0 0 0
1 1 0 0 0
0 0 1 0 0
0 0 0 1 1
```

---

## **Sample Output**

```
3
```

---

## **Explanation**

There are **3 separate islands** in the matrix.

---

## **Execution Time Limit**

**10 seconds**