# **Problem 1015: Merge Overlapping Intervals**

**Company:** Amazon

**Topic:** Arrays / Sorting

---

## **Problem Statement**

You are given a list of **intervals**, where each interval is represented as:

```
[start, end]
```

Your task is to **merge all overlapping intervals** and return the resulting list of **non-overlapping intervals**.

---

## **Input Format**

* The **first line** contains an integer **n** representing the number of intervals.
* The next **n lines** contain two integers:

```
start end
```

---

## **Constraints**

* **1 ≤ n ≤ 10⁴**
* **0 ≤ start ≤ end ≤ 10⁹**

---

## **Output Format**

Print the **merged intervals** in ascending order.

---

## **Sample Input**

```
4
1 3
2 6
8 10
15 18
```

---

## **Sample Output**

```
1 6
8 10
15 18
```

---

## **Explanation**

Intervals **[1,3]** and **[2,6]** overlap, so they merge into **[1,6]**.

---

## **Execution Time Limit**

**10 seconds**