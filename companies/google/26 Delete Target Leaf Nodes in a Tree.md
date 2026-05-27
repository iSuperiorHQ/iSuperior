# **Problem 26: Delete Target Leaf Nodes in a Tree**

**Company:** Google

**Category:** Trees / DFS / Postorder Traversal

**Difficulty:** Medium

---

# **Problem Description**

You are given the root of a binary tree and an integer:

```text
target
```

Delete all leaf nodes having value equal to:

```text
target
```

After deleting such leaf nodes, new leaf nodes may be formed.

If any newly formed leaf node also has value equal to:

```text
target
```

it must also be deleted.

Continue this process until no target-valued leaf node remains in the tree.

Return the root of the final modified tree.

---

# **Business Requirement**

A distributed file-cleanup system removes temporary nodes from a hierarchical storage structure.

When a temporary node is removed, its parent may become an unnecessary leaf node and must also be deleted recursively.

The system must repeatedly clean the hierarchy until no invalid terminal nodes remain.

---

# **Task**

Delete all target-valued leaf nodes recursively and return the updated binary tree.

---

# **Function Signature**

```cpp
TreeNode* removeLeafNodes(TreeNode* root, int target)
```

---

# **Class Definition**

```cpp
class TreeNode {
public:
    int val;
    TreeNode* left;
    TreeNode* right;

    TreeNode(int x) {
        val = x;
        left = nullptr;
        right = nullptr;
    }
};
```

---

# **Input Format**

First line contains integer:

```text
n
```

representing total entries in level-order representation of the tree.

Second line contains `n` space-separated values representing the binary tree in level-order traversal:

```text
tree[i]
```

Null nodes are represented using:

```text
N
```

Third line contains integer:

```text
target
```

representing target leaf value to delete.

---

# **Output Format**

Print the level-order traversal of the modified tree.

If the tree becomes empty, print:

```text
EMPTY
```

---

# **Constraints**

* **1 ≤ Number of Nodes ≤ 10⁵**
* **1 ≤ Node.val ≤ 10³**
* **1 ≤ target ≤ 10³**

---

# **Sample Input 1**

```text
7
1 2 3 2 N 2 4
2
```

---

# **Sample Output 1**

```text
1 N 3 N 4
```

---

# **Explanation**

Initial tree:

```text
        1
       / \
      2   3
         / \
        2   4
```

Leaf nodes having value:

```text
2
```

are deleted.

Remaining tree:

```text
        1
         \
          3
           \
            4
```

---

# **Sample Input 2**

```text
7
1 3 3 3 2 N 3
3
```

---

# **Sample Output 2**

```text
1 3 N N 2
```

---

# **Explanation**

Initial tree:

```text
        1
       / \
      3   3
     / \   \
    3   2   3
```

Delete leaf nodes having value:

```text
3
```

After deleting bottom leaf nodes:

```text
        1
       /
      3
       \
        2
```

The remaining node:

```text
3
```

is not deleted because it is no longer a leaf node.

---

# **Sample Input 3**

```text
3
1 1 1
1
```

---

# **Sample Output 3**

```text
EMPTY
```

---

# **Explanation**

Initial tree:

```text
      1
     / \
    1   1
```

Delete leaf nodes having value:

```text
1
```

After deleting children, root also becomes a target-valued leaf node.

Entire tree gets deleted.

---

# **Key Observation**

Deleting target-valued leaf nodes may create new target-valued leaf nodes higher in the tree.

Therefore:

```text
Parent nodes must be processed after children
```

This naturally leads to:

```text
Postorder Traversal
```

because children are processed before the parent node.

---

# **Approaches**

| Approach | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| Repeated BFS Deletion | O(n²) | O(n) |
| Recursive DFS Postorder | O(n) | O(h) |
| Iterative Postorder Traversal | O(n) | O(h) |

Where:

* `n` = number of nodes
* `h` = height of tree

---

# **Recommended Interview Approach**

Preferred interview solution:

```text
Recursive DFS Postorder Traversal
```

because node validity depends on already-processed children.

---

# **Efficient Strategy**

1. Recursively process left subtree.
2. Recursively process right subtree.
3. After processing children:

   * check whether current node becomes a leaf node
   * check whether current node value equals target

4. If both conditions are true:

```text
delete current node
return nullptr
```

5. Otherwise return current node.

---

# **Example Walkthrough**

Input tree:

```text
        1
       / \
      2   3
         / \
        2   4
```

Target:

```text
2
```

Delete left leaf node:

```text
2
```

Delete leaf node:

```text
2
```

under node:

```text
3
```

Remaining tree:

```text
        1
         \
          3
           \
            4
```

---

# **Expected Complexity**

## Recursive DFS Postorder

### Time Complexity

* **O(n)**

because every node is visited exactly once.

---

### Space Complexity

* **O(h)**

due to recursion stack space.

Where:

* `h` = height of tree

Worst case:

```text
O(n)
```

for skewed trees.

Best case:

```text
O(log n)
```

for balanced trees.

---

# **Edge Cases**

Your solution should correctly handle:

* single-node tree
* all nodes equal to target
* no node equal to target
* skewed trees
* balanced trees
* root deletion
* cascading deletions

---

# **Follow-Up Questions**

Interviewers may ask:

* Why is preorder traversal incorrect?
* Can this be solved iteratively?
* How would you delete nodes based on subtree properties?
* Can you generalize this for n-ary trees?
* How would recursion depth affect memory usage?

---

# **Execution Time Limit**

```text
2 seconds
```