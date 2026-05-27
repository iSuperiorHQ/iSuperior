````md id="4mk8qp"
# Problem 26: Delete Target Leaf Nodes in a Tree

**Company:** Google

**Difficulty:** Medium-Hard

---

# Category

- Trees
- Binary Trees
- DFS
- Recursion
- Postorder Traversal
- Tree Pruning

---

# Problem Description

A distributed monitoring system stores its alert hierarchy as a binary tree.

Each node represents a monitoring service identified by an integer value.

Certain services become obsolete over time and must be removed from the hierarchy.

However, a service can only be safely removed if it is currently a:

```text
Leaf Node
````

meaning it has no children.

Additionally, deleting one leaf node may cause its parent to become a new leaf node, which may also need deletion.

Your task is to repeatedly delete all leaf nodes having a specified target value until no such nodes remain.

---

# Business Requirement

Given:

* the root of a binary tree
* an integer `target`

remove every leaf node whose value equals:

```text
target
```

Deletion must continue recursively because:

```text
removing child nodes can create new target-valued leaf nodes
```

Return the final tree after all valid deletions.

---

# Important Observation

Deletion must occur in:

```text
Postorder Traversal
```

because:

* child nodes must be processed before parent nodes
* parent leaf status depends on child deletions

---

# Task

Return the root of the modified binary tree after all target leaf nodes are deleted.

If the entire tree gets deleted, return:

```text
NULL
```

---

# Input Format

First line contains integer:

```text
N
```

representing total nodes in level-order traversal.

Second line contains:

```text
N space-separated values
```

representing the binary tree in level-order format.

Use:

```text
NULL
```

for missing nodes.

Third line contains integer:

```text
target
```

representing leaf value to delete.

---

# Output Format

Print the resulting binary tree in level-order traversal.

If tree becomes empty, print:

```text
NULL
```

Trailing `NULL` values should be omitted from final level-order output.

---

# Constraints

* **1 ≤ N ≤ 10⁵**
* **1 ≤ Node Value ≤ 10⁵**
* **1 ≤ target ≤ 10⁵**

---

# Sample Input 1

```text
7
1 2 3 2 NULL 2 4
2
```

---

# Sample Output 1

```text
1 NULL 3 NULL 4
```

---

# Explanation

Initial tree:

```text
        1
       / \
      2   3
         / \
        2   4
```

Leaf nodes with value:

```text
2
```

are deleted.

After deletion:

```text
        1
         \
          3
           \
            4
```

Final level-order traversal:

```text
1 NULL 3 NULL 4
```

---

# Sample Input 2

```text
12
1 3 3 3 2 NULL 3 NULL NULL NULL NULL 3
3
```

---

# Sample Output 2

```text
1 3 NULL NULL 2
```

---

# Explanation

Initial tree:

```text
            1
           / \
          3   3
         / \    \
        3   2    3
                 /
                3
```

Delete leaf nodes with value:

```text
3
```

Step-by-step:

1. Bottom-most leaf `3` deleted
2. Right child `3` becomes leaf → deleted
3. Left-most leaf `3` deleted
4. Parent `3` on left side is not deleted because it still has child `2`

Final tree:

```text
        1
       /
      3
       \
        2
```

Level-order traversal:

```text
1 3 NULL NULL 2
```

---

# Sample Input 3

```text
3
1 1 1
1
```

---

# Sample Output 3

```text
NULL
```

---

# Explanation

Initial tree:

```text
    1
   / \
  1   1
```

Both leaf nodes are deleted first.

Root becomes leaf with value:

```text
1
```

Hence root is also deleted.

Entire tree becomes empty.

---

# Recommended Approach

Efficient interview solution uses:

```text
Postorder Depth-First Search (DFS)
```

---

# Optimal Strategy

Process:

1. recursively process left subtree
2. recursively process right subtree
3. check whether current node became leaf
4. if current node value equals target:

```text
delete current node
```

This logic also applies to the root node after subtree processing.

---

# Key Insight

A node should only be evaluated for deletion:

```text
after its children are processed
```

This makes:

```text
Postorder Traversal
```

the optimal strategy.

---

# Expected Complexity

## DFS Tree Pruning Approach

### Time Complexity

```text
O(N)
```

because:

* every node is visited exactly once
* every node is evaluated once after child processing

even if deletions cascade upward.

---

### Space Complexity

```text
O(H)
```

where:

* `H` = height of tree

due to recursion stack.

Worst case:

```text
O(N)
```

for skewed trees.

Balanced tree:

```text
O(log N)
```

---

# Alternative Approaches

| Approach            | Time Complexity | Space Complexity |
| ------------------- | --------------- | ---------------- |
| Recursive DFS       | O(N)            | O(H)             |
| Iterative Postorder | O(N)            | O(N)             |

---

# Edge Cases

Your solution should correctly handle:

* root deletion
* all nodes deleted
* skewed trees
* duplicate values
* no target nodes
* target nodes that are not leaves
* chain reactions after deletion
* single-node trees

---

# Object-Oriented Design Expectations

Recommended classes:

| Class             | Responsibility               |
| ----------------- | ---------------------------- |
| `TreeNode`        | Represents binary tree node  |
| `TreePruner`      | Core deletion logic          |
| `TraversalHelper` | Handles DFS traversal        |
| `TreeSerializer`  | Converts tree to level-order |

---

# Follow-Up Interview Questions

Interviewers may ask:

* Why is preorder traversal incorrect?
* Can this be implemented iteratively?
* How would you serialize very large trees?
* Can this be generalized to N-ary trees?
* How would you avoid recursion stack overflow?

---

# Execution Time Limit

```text
2 seconds
```

```
```