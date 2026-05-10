# **Problem 1078: CPU Task Scheduler with Cooling Interval**

**Company:** Amazon

**Topic:** Greedy / Heap

---

## **Problem Description**

A cloud computing server processes multiple CPU tasks represented by uppercase English letters.

Each character represents a unique task type:

```text id="m2v8zk"
'A', 'B', 'C', ...
```

Every task requires exactly:

```text id="x7m1qa"
1 unit of CPU time
```

to execute.

However, identical tasks cannot be executed too close to each other because of processor thermal constraints.

A cooling interval `N` is provided such that:

> After executing a task, the same task cannot be executed again for the next `N` time units.

During cooling periods, the CPU may either:

* Execute a different available task
* Remain idle

Your task is to determine the minimum total CPU time required to execute all tasks while respecting the cooling interval constraint.

---

## **Task**

Given:

* A list of CPU tasks
* A cooling interval `N`

Compute the minimum number of CPU intervals required to finish all tasks.

---

## **Input Format**

* First line: integer **T** — total number of tasks
* Second line: `T` uppercase characters representing tasks
* Third line: integer **N** — cooling interval

---

## **Constraints**

* **1 ≤ T ≤ 10⁵**
* Tasks contain only uppercase English letters
* **0 ≤ N ≤ 10⁵**

---

## **Output Format**

Print a single integer — the minimum CPU intervals required to execute all tasks.

---

## **Sample Input 1**

```text id="k9m2vx"
6
A A A B B B
2
```

---

## **Sample Output 1**

```text id="u3m8qp"
8
```

---

## **Explanation**

One optimal scheduling sequence:

```text id="f9m1zk"
A → B → idle → A → B → idle → A → B
```

Total intervals used:

```text id="r2m8vx"
8
```

The cooling interval between identical tasks is maintained.

---

## **Sample Input 2**

```text id="n7m2qa"
7
A A A B B B C
2
```

---

## **Sample Output 2**

```text id="p4m9xp"
8
```

---

## **Explanation**

An optimized scheduling sequence:

```text id="v1m8zk"
A → B → C → A → B → idle → A → B
```

Total intervals:

```text id="g8m2vx"
8
```

The cooling interval constraint is satisfied for all identical tasks.

---

## **Sample Input 3**

```text id="x2m1qa"
6
A A A A B C
3
```

---

## **Sample Output 3**

```text id="m9v2zk"
13
```

---

## **Explanation**

One valid scheduling sequence:

```text id="k4m8qp"
A → B → C → idle → A → idle → idle → idle → A → idle → idle → idle → A
```

The large cooling interval forces multiple idle slots.

Total intervals:

```text id="u7m1xp"
13
```

---

## **Sample Input 4**

```text id="m4k8qa"
5
A B C D E
2
```

---

## **Sample Output 4**

```text id="v8m2zk"
5
```

---

## **Explanation**

All tasks are unique.

Hence no idle intervals are required.

---

## **Greedy Insight**

To minimize idle time:

* Always execute the task with highest remaining frequency first
* Use a max-heap / priority queue to repeatedly select the best candidate
* Store temporarily blocked tasks until their cooling interval expires

---

## **Optimized Strategy**

Key observations:

* Tasks with highest frequency dominate scheduling
* Idle intervals occur only when no valid task is available
* Greedy ordering minimizes wasted CPU cycles

---

## **Expected Complexity**

Using Heap + Frequency Map:

* **Time Complexity:** `O(T log U)`

Where:

* `T` = total number of tasks
* `U` = number of unique task types

Since tasks contain only uppercase English letters:

```text id="x1m9vx"
U ≤ 26
```

Hence the complexity is effectively near-linear.

* **Space Complexity:** `O(U)`

---

## **Execution Time Limit**

**10 seconds**