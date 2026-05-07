# **Problem 1070: Graph Breadth-First Search (BFS) Traversal**

**Company:** Wipro

**Topic:** Graphs / BFS / Queue

---

## **Problem Description**

A network monitoring system models connected servers as a graph.
To analyze communication layers and shortest-hop reachability, the system performs a **Breadth-First Search (BFS)** traversal starting from a specific source node.

You are given an undirected graph consisting of `N` nodes and `M` edges. Your task is to perform a BFS traversal starting from the given source node and print the order in which nodes are visited.

The traversal must correctly manage:

* Visited nodes
* Queue operations
* Cyclic graph structures

to avoid revisiting nodes and entering infinite loops.

---

## **Task**

Implement BFS traversal for the given graph and print the sequence of visited nodes.

---

## **Important Rules**

1. Start traversal from the given source node
2. Visit adjacent nodes in the order they appear in the input
3. A node must be visited only once
4. The graph may contain:

   * Cycles
   * Disconnected components
   * Self-loops

---

## **Input Format**

* First line: integers **N** and **M**

  * `N` → number of nodes
  * `M` → number of edges

* Next `M` lines:

```text id="n4v8qp"
u v
```

representing an undirected edge between `u` and `v`

* Last line: integer **S**

  * Starting node for BFS traversal

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **0 ≤ M ≤ 2 × 10⁵**
* **1 ≤ u, v, S ≤ N**

---

## **Output Format**

Print the BFS traversal order separated by spaces.

---

## **Sample Input 1**

```text id="j3m8zx"
5 5
1 2
1 3
2 4
3 5
4 5
1
```

---

## **Sample Output 1**

```text id="m8q2xp"
1 2 3 4 5
```

---

## **Explanation**

Graph structure:

```text id="v1m9zk"
1 → 2, 3
2 → 4
3 → 5
4 → 5
```

BFS traversal starting from node `1`:

```text id="x2k7qa"
1
→ 2, 3
→ 4, 5
```

Traversal order:

```text id="k7m2vr"
1 2 3 4 5
```

---

## **Sample Input 2**

```text id="b4m9xp"
6 7
1 2
1 3
2 4
2 5
3 6
5 6
4 6
2
```

---

## **Sample Output 2**

```text id="u2m8qa"
2 1 4 5 3 6
```

---

## **Explanation**

Starting BFS from node `2`:

```text id="y8m1qp"
Visit 2
Queue neighbors → 1, 4, 5
Then process:
1 → 3
4 → 6
```

Nodes are visited level-by-level while maintaining input adjacency order.

---

## **Sample Input 3**

```text id="g7m2vk"
4 2
1 2
3 4
1
```

---

## **Sample Output 3**

```text id="z1m8qp"
1 2
```

---

## **Explanation**

The graph contains disconnected components.

Starting BFS from node `1` only visits:

```text id="f2k9mz"
1 → 2
```

Nodes `3` and `4` are unreachable from the source node.

---

## **Core BFS Algorithm**

1. Mark source node as visited
2. Push source node into queue
3. While queue is not empty:

   * Remove front node
   * Visit all unvisited adjacent nodes
   * Mark them visited
   * Push them into queue

---

## **Expected Complexity**

* **Time Complexity:** `O(N + M)`
* **Space Complexity:** `O(N)`

Efficient adjacency-list representation is expected for large graphs.

---

## **Execution Time Limit**

**10 seconds**