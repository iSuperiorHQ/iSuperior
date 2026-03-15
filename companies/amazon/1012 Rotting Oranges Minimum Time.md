# **Problem 1012: Rotting Oranges Minimum Time**

**Company:** Amazon

**Topic:** Graph / Multi-source BFS

---

## **Problem Statement**

You are given a **grid representing a box of oranges**.

Each cell can have one of the following values:

* **0** → Empty cell
* **1** → Fresh orange
* **2** → Rotten orange

Every **minute**, any **fresh orange adjacent (up, down, left, right)** to a rotten orange becomes rotten.

Your task is to determine the **minimum number of minutes required for all fresh oranges to become rotten**.

If it is **impossible to rot all oranges**, return **-1**.

---

## **Input Format**

* The **first line** contains two integers **m** and **n** representing the grid size.
* The next **m lines** contain **n integers** representing the grid.

---

## **Constraints**

* **1 ≤ m, n ≤ 100**
* Grid values are **0, 1, or 2**

---

## **Output Format**

Return an integer representing the **minimum number of minutes required** for all oranges to rot.

---

## **Sample Input**

```
3 3
2 1 1
1 1 0
0 1 1
```

---

## **Sample Output**

```
4
```

---

## **Explanation**

The rotting spreads every minute until **all fresh oranges become rotten in 4 minutes**.

---

## **Execution Time Limit**

**10 seconds**