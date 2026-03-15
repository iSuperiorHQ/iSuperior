# **Problem 1005: Maximum Profit in Job Scheduling**

**Company:** EPAM

---

## **Problem Statement**

You are given **n jobs**, where each job has a **start time**, **end time**, and **profit**.

Your task is to select a subset of jobs such that:

* No two selected jobs **overlap in time**.
* The **total profit is maximized**.

Two jobs are considered **non-overlapping** if the **start time of the next job is greater than or equal to the end time of the previous job**.

Return the **maximum profit** that can be obtained by scheduling the jobs.

---

## **Input Format**

* The **first line** contains an integer **n**, representing the number of jobs.
* The **next n lines** contain **three integers each**:

```
startTime endTime profit
```

---

## **Constraints**

* **1 ≤ n ≤ 10⁴**
* **1 ≤ startTime < endTime ≤ 10⁹**
* **1 ≤ profit ≤ 10⁴**

---

## **Output Format**

Return a single integer representing the **maximum profit that can be achieved** without overlapping jobs.

---

## **Sample Input**

```
4
1 3 50
2 5 20
3 10 100
6 9 70
```

---

## **Sample Output**

```
150
```

---

## **Explanation**

The optimal job selection is:

* Job 1 → **(1,3,50)**
* Job 3 → **(3,10,100)**

These jobs **do not overlap**.

Total profit:

```
50 + 100 = 150
```

---

## **Execution Time Limit**

**10 seconds**