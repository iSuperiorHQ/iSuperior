# **Problem 110: Course Schedule I & II**

**Company:** Uber

**Category:** Graph / Cycle Detection in DAGs

**Difficulty:** Hard

---

# **Problem Description**

Uber’s internal learning platform offers thousands of technical courses for engineers.

Some courses require completing prerequisite courses before enrollment.

Given all course dependency relationships, your task is to:

1. Determine whether it is possible to finish all courses
2. Return one valid order of completion if possible

This problem is a classic:

```text id="m2v8zk"
Directed Graph + Topological Sorting
```

problem involving:

* cycle detection
* dependency resolution
* DAG traversal

Interviewers commonly expect solutions using:

* Kahn’s Algorithm (BFS Topological Sort)
* DFS-based cycle detection

---

# **Task**

You are given:

* total number of courses
* prerequisite relationships

Each prerequisite pair:

```text id="x7m1qa"
[a, b]
```

means:

```text id="u3m8qp"
to take course a,
you must first complete course b
```

Your tasks are:

---

## Part 1 — Course Schedule I

Determine whether all courses can be completed.

Return:

```text id="f9m1zk"
true
```

if possible, otherwise:

```text id="r2m8vx"
false
```

---

## Part 2 — Course Schedule II

If all courses can be completed:

return one valid course ordering.

Otherwise return:

```text id="n7m2qa"
IMPOSSIBLE
```

---

# **Graph Interpretation**

Represent courses as a directed graph:

| Entity       | Representation |
| ------------ | -------------- |
| Course       | Node           |
| Prerequisite | Directed Edge  |

Edge:

```text id="p4m9xp"
b → a
```

means:

```text id="v1m8zk"
b must be completed before a
```

---

# **Important Observation**

All courses can be completed:

```text id="g8m2vx"
IFF
```

the directed graph contains:

```text id="x2m1qa"
NO cycle
```

Thus the problem reduces to:

```text id="m9v2zk"
cycle detection in a directed graph
```

---

# **Input Format**

First line contains two integers:

```text id="k4m8qp"
V E
```

Where:

* `V` = total number of courses
* `E` = number of prerequisite relations

Next `E` lines contain two integers:

```text id="u7m1xp"
a b
```

meaning:

```text id="m4k8qa"
b → a
```

---

# **Output Format**

If all courses can be completed:

1. Print:

```text id="v8m2zk"
true
```

2. Print one valid course ordering as space-separated integers.

---

Otherwise:

1. Print:

```text id="x1m9vx"
false
```

2. Print:

```text id="z7m2qp"
IMPOSSIBLE
```

---

# **Constraints**

* **1 ≤ V ≤ 10⁵**
* **0 ≤ E ≤ 2 × 10⁵**
* **0 ≤ courseId < V**

---

# **Sample Input 1**

```text id="u4m8zk"
4 4
1 0
2 0
3 1
3 2
```

---

# **Sample Output 1**

```text id="k2m1qa"
true
0 1 2 3
```

---

# **Explanation**

Dependencies:

```text id="r7m2zk"
0 → 1
0 → 2
1 → 3
2 → 3
```

One valid ordering:

```text id="u1m8xp"
0 1 2 3
```

Another valid ordering could also be:

```text id="m4k8qa"
0 2 1 3
```

because multiple topological orders may exist.

---

# **Sample Input 2**

```text id="v8m2zk"
2 2
0 1
1 0
```

---

# **Sample Output 2**

```text id="x1m9vx"
false
IMPOSSIBLE
```

---

# **Explanation**

Dependencies form cycle:

```text id="z7m2qp"
0 → 1 → 0
```

Thus no valid ordering exists.

---

# **Sample Input 3**

```text id="u4m8zk"
5 0
```

---

# **Sample Output 3**

```text id="k2m1qa"
true
0 1 2 3 4
```

---

# **Explanation**

No prerequisites exist.

Any ordering is valid.

---

# **Sample Input 4**

```text id="r7m2zk"
6 6
1 0
2 1
3 2
4 2
5 3
3 5
```

---

# **Sample Output 4**

```text id="u1m8xp"
false
IMPOSSIBLE
```

---

# **Explanation**

Cycle exists:

```text id="m4k8qa"
3 → 5 → 3
```

Thus all courses cannot be completed.

---

# **Why Brute Force Fails**

Naively checking all possible course orders requires:

```text id="v8m2zk"
O(V!)
```

which is computationally impossible for large graphs.

---

# **Optimized Approach — Kahn’s Algorithm**

Use:

```text id="x1m9vx"
BFS Topological Sorting
```

with:

* adjacency list
* indegree tracking

---

# **Efficient Strategy**

---

## Step 1 — Build Graph

Create adjacency list:

```text id="z7m2qp"
b → a
```

for every prerequisite pair.

Use adjacency sets or ignore duplicate edges to prevent incorrect indegree increments.

---

## Step 2 — Compute Indegrees

For every node:

```text id="u4m8zk"
indegree[node]
```

stores number of prerequisites remaining.

---

## Step 3 — Initialize Queue

Push all nodes having:

```text id="k2m1qa"
indegree = 0
```

into queue.

These courses can be taken immediately.

---

## Step 4 — BFS Traversal

Repeatedly:

1. Pop course from queue
2. Add to topological order
3. Reduce indegree of neighbors
4. Push newly unlocked courses into queue

---

# **Cycle Detection**

After BFS:

If processed node count is smaller than:

```text id="r7m2zk"
V
```

then a cycle exists.

Thus:

```text id="u1m8xp"
all courses cannot be completed
```

---

# **Why Topological Sorting Works**

A topological ordering exists:

```text id="m4k8qa"
IFF
```

the graph is a:

```text id="v8m2zk"
Directed Acyclic Graph (DAG)
```

Thus cycle detection and course ordering are solved simultaneously.

---

# **Alternative DFS Solution**

Interviewers may also expect:

* DFS recursion stack cycle detection
* node coloring technique:

  * unvisited
  * visiting
  * visited

A back edge indicates a cycle.

---

# **Recommended Data Structures**

| Structure              | Purpose             |
| ---------------------- | ------------------- |
| `Adjacency List / Set` | Store graph         |
| `Indegree Array`       | Track prerequisites |
| `Queue`                | BFS traversal       |
| `Vector/List`          | Store ordering      |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* disconnected graphs
* multiple valid orders
* self-loops
* duplicate prerequisite edges
* graphs with zero edges
* isolated courses
* very large DAGs

---

# **Expected Complexity**

## Kahn’s Algorithm

### Time Complexity

* **O(V + E)**

Where:

* `V` = number of courses
* `E` = number of prerequisite relations

Each node and edge is processed at most once.

---

### Space Complexity

* **O(V + E)**

for adjacency list, indegree array, queue, and topological ordering.

---

# **Example Walkthrough**

Courses:

```text id="x1m9vx"
0 1 2 3
```

Dependencies:

```text id="z7m2qp"
0 → 1
0 → 2
1 → 3
2 → 3
```

---

## Initial Indegrees

| Course | Indegree |
| ------ | -------- |
| 0      | 0        |
| 1      | 1        |
| 2      | 1        |
| 3      | 2        |

Queue initially:

```text id="u4m8zk"
[0]
```

---

## BFS Processing

| Step | Course Taken | Queue |
| ---- | ------------ | ----- |
| 1    | 0            | [1,2] |
| 2    | 1            | [2]   |
| 3    | 2            | [3]   |
| 4    | 3            | []    |

Valid order:

```text id="k2m1qa"
0 1 2 3
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* DFS Topological Sort
* Tarjan’s SCC Algorithm
* Kosaraju’s Algorithm
* Dependency graph scheduling

---

# **Follow-Up Variants**

Interviewers may ask:

* Return all valid schedules
* Minimum semesters required
* Parallel course scheduling
* Dynamic prerequisite updates
* Weighted prerequisite graphs

---

# **Execution Time Limit**

**8 seconds**