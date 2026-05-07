# **Problem 1069: Maximum Depth of a Binary Tree**

**Company:** Wipro

**Topic:** Trees / Recursion / DFS

---

## **Problem Description**

A distributed storage engine organizes hierarchical metadata using binary tree structures.
To optimize query execution and memory allocation, the system must determine the **maximum traversal depth** of the tree.

You are given the root of a binary tree. Your task is to calculate the **maximum depth** (also called the **height**) of the tree.

The maximum depth is defined as:

> The total number of nodes present in the longest path from the root node to any leaf node.

---

## **Task**

Traverse the binary tree and return its maximum root-to-leaf depth.

---

## **Input Representation**

The binary tree is represented using **level-order traversal**.

* `-1` represents a NULL node

---

## **Input Format**

* First line: integer **n** — total number of entries in level-order traversal
* Second line: **n integers** representing the binary tree

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* Node values range between:

```text id="a8nq1k"
-10⁹ to 10⁹
```

---

## **Output Format**

Print a single integer — the maximum depth of the binary tree.

---

## **Sample Input 1**

```text id="wdjlwm"
7
1 2 3 4 5 -1 6
```

---

## **Sample Output 1**

```text id="5mjlwm"
3
```

---

## **Explanation**

Tree structure:

```text id="k4j3xp"
        1
      /   \
     2     3
    / \     \
   4   5     6
```

Longest root-to-leaf paths:

```text id="3x9nvp"
1 → 2 → 4
1 → 2 → 5
1 → 3 → 6
```

Maximum depth = **3**

---

## **Sample Input 2**

```text id="pm0k8m"
5
1 2 -1 3 -1
```

---

## **Sample Output 2**

```text id="2jlwm0"
3
```

---

## **Explanation**

Tree structure:

```text id="v7m2xp"
      1
     /
    2
   /
  3
```

Longest path:

```text id="c2m9zk"
1 → 2 → 3
```

Depth = **3**

---

## **Sample Input 3**

```text id="x2m1qv"
1
10
```

---

## **Sample Output 3**

```text id="m9q2xa"
1
```

---

## **Explanation**

A single-node tree has depth **1**.

---

## **Recursive DFS Logic**

For every node:

```text id="z1k7qp"
depth(node) =
1 + max(depth(left_subtree),
        depth(right_subtree))
```

Base condition:

```text id="k9v2mx"
depth(NULL) = 0
```

---

## **Expected Complexity**

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(H)` recursive stack

  * `H` = height of the tree

---

## **Alternative Approach**

The problem can also be solved iteratively using:

* **Level Order Traversal (BFS)**
* Queue-based processing

---

## **What they check:**

* Recursive traversal understanding
* Tree depth computation
* Base case handling
* DFS vs BFS knowledge
* Large skewed-tree handling

---

## **Execution Time Limit**

**10 seconds**