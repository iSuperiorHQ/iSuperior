# **Problem 1010: Trapping Rain Water Over Elevation Map**

**Company:** Amazon

**Topic:** Arrays / Two Pointers

---

## **Problem Statement**

You are given an array **height[]** representing an elevation map where the width of each bar is **1**.

Your task is to compute how much **rainwater can be trapped** after rainfall.

Water can be trapped between bars if there are **taller bars on both sides**.

---

## **Input Format**

* The **first line** contains an integer **n** representing the number of bars.
* The **second line** contains **n integers** representing the height of each bar.

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **0 ≤ height[i] ≤ 10⁴**

---

## **Output Format**

Return a single integer representing the **total amount of water trapped**.

---

## **Sample Input**

```
12
0 1 0 2 1 0 1 3 2 1 2 1
```

---

## **Sample Output**

```
6
```

---

## **Explanation**

Water trapped at different indices accumulates to **6 units**.

---

## **Execution Time Limit**

**10 seconds**