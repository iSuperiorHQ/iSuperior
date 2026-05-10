# **Problem 1084: Course Schedule Feasibility**

**Company:** Amazon

**Topic:** Graph / Cycle Detection

---

## **Problem Description**

A university curriculum management system maintains prerequisite relationships between courses.

Certain advanced courses can only be taken after completing specific prerequisite courses.

You are given:

* `N` courses labeled from `0` to `N-1`
* A list of prerequisite relationships

Each prerequisite pair:

```text id="m2v8zk"
[a, b]
```

means:

> To enroll in course `a`, a student must first complete course `b`.

Your task is to determine whether a student can successfully complete all courses.

A course schedule becomes impossible if the prerequisite structure contains a:

```text id="x7m1qa"
Cycle
```

because cyclic dependencies create an infinite prerequisite chain.

---

## **Task**

Determine whether it is possible to complete all courses given the prerequisite dependencies.

Return:

```text id="u3m8qp"
Possible
```

if all courses can be completed.

Otherwise return:

```text id="f9m1zk"
Impossible
```

---

## **Graph Interpretation**

Treat courses as nodes of a directed graph.

For prerequisite:

```text id="r2m8vx"
[a, b]
```

create directed edge:

```text id="n7m2qa"
b → a
```

A cycle in this directed graph indicates invalid scheduling.

---

## **Input Format**

* First line: integers **N** and **P**

  * `N` → total number of courses
  * `P` → number of prerequisite relations

* Next `P` lines:

  * Two integers `a` and `b`

representing:

```text id="p4m9xp"
[a, b]
```

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **0 ≤ P ≤ 2 × 10⁵**
* **0 ≤ a, b < N**
* `a ≠ b`

---

## **Output Format**

Print:

```text id="v1m8zk"
Possible
```

or

```text id="g8m2vx"
Impossible
```

---

## **Sample Input 1**

```text id="x2m1qa"
4 4
1 0
2 1
3 2
3 1
```

---

## **Sample Output 1**

```text id="m9v2zk"
Possible
```

---

## **Explanation**

Dependency graph:

```text id="k4m8qp"
0 → 1 → 2 → 3
      ↘────→
```

No cycle exists.

A valid course order is:

```text id="u7m1xp"
0 → 1 → 2 → 3
```

Hence all courses can be completed.

---

## **Sample Input 2**

```text id="m4k8qa"
3 3
0 1
1 2
2 0
```

---

## **Sample Output 2**

```text id="v8m2zk"
Impossible
```

---

## **Explanation**

Dependency graph:

```text id="x1m9vx"
0 → 1 → 2 → 0
```

A cycle exists.

No valid ordering can satisfy all prerequisites.

---

## **Sample Input 3**

```text id="z7m2qp"
5 4
1 0
2 0
3 1
4 2
```

---

## **Sample Output 3**

```text id="u4m8zk"
Possible
```

---

## **Explanation**

The prerequisite graph is acyclic.

One valid ordering:

```text id="k2m1qa"
0 → 1 → 3 → 2 → 4
```

Multiple valid schedules may exist.

---

## **Sample Input 4**

```text id="r7m2zk"
2 2
0 1
1 0
```

---

## **Sample Output 4**

```text id="u1m8xp"
Impossible
```

---

## **Explanation**

Both courses depend on each other directly:

```text id="m4k8qa"
0 ↔ 1
```

Hence completion is impossible.

---

## **Cycle Detection Insight**

The problem reduces to detecting whether a directed graph contains a cycle.

If:

```text id="v8m2zk"
Cycle exists
```

→ course completion impossible.

If:

```text id="x1m9vx"
Graph is acyclic (DAG)
```

→ all courses can be completed.

---

## **Common Approaches**

### DFS Cycle Detection

Maintain three states:

```text id="z7m2qp"
0 → unvisited
1 → visiting
2 → visited
```

Encountering a node already in:

```text id="u4m8zk"
visiting state
```

indicates a cycle.

---

### Kahn’s Topological Sort

* Compute indegree of every node
* Continuously process nodes with indegree `0`
* If processed node count equals `N`, schedule is possible

Otherwise a cycle exists.

---

## **Expected Complexity**

### DFS or Kahn's Algorithm

* **Time Complexity:** `O(N + P)`
* **Space Complexity:** `O(N + P)`

Where:

* `N` = number of courses
* `P` = number of prerequisite relations

---

## **Execution Time Limit**

**10 seconds**