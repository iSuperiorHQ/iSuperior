# **Problem 1035: Calculate the Absolute Minimum Processing Time for Tasks on Quad-Cores**

**Company:** Infosys

**Topic:** Greedy / Arrays

---

## **Problem Statement**

You are given a system with **quad-core processors**, meaning each processor can execute **up to 4 tasks simultaneously (in parallel)**.

There are **N tasks**, where each task has a **processing time**.

Your goal is to assign tasks to processors such that the **total time required to complete all tasks is minimized**.

---

## **Important Details**

* Each processor can handle **at most 4 tasks at a time**
* Tasks assigned to the same processor will run **in parallel**
* The **time taken by a processor** is determined by the **maximum processing time among its assigned tasks**
* You can use **multiple processors**
* Each task must be assigned to **exactly one processor**

---

## **Objective**

Minimize the **overall completion time**, defined as:

> The **maximum time taken by any processor**

---

## **Input Format**

* The **first line** contains an integer **N** (number of tasks)
* The **second line** contains **N integers** representing the processing time of each task

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **1 ≤ task[i] ≤ 10⁹**

---

## **Output Format**

Return a single integer representing the **minimum total processing time** required.

---

## **Sample Input**

```text
8
8 1 7 3 9 2 6 4
```

---

## **Sample Output**

```text
9
```

---

## **Explanation**

Sort tasks:

```text
1 2 3 4 6 7 8 9
```

Group into processors (max 4 tasks each):

* Processor 1 → [9, 1, 2, 3] → time = **9**
* Processor 2 → [8, 4, 6, 7] → time = **8**

Overall time = **max(9, 8) = 9**

---

## **Key Insight**

* To minimize total time:

  * Assign the **largest tasks first**
  * Pair them with smaller tasks
* Use a **greedy strategy**:

  * Sort tasks
  * Group largest with smallest

Time Complexity: **O(N log N)**

---

## **Execution Time Limit**

**10 seconds**