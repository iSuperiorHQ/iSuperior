# **Problem 1082: Validate Binary Search Tree**

**Company:** Amazon

**Topic:** Binary Search Tree / Trees

---

## **Problem Description**

A cloud database indexing engine stores records using a hierarchical binary tree structure for faster querying.

To maintain efficient search performance, the tree must satisfy the strict properties of a:

```text id="m2v8zk"
Binary Search Tree (BST)
```

A binary tree is considered a valid BST if:

1. Every node in the left subtree contains a value strictly smaller than the current node
2. Every node in the right subtree contains a value strictly greater than the current node
3. Both left and right subtrees must also independently satisfy BST properties

Your task is to determine whether the given binary tree is a valid Binary Search Tree.

---

## **Task**

Return:

```text id="x7m1qa"
Valid BST
```

if the given binary tree satisfies all BST conditions.

Otherwise return:

```text id="u3m8qp"
Invalid BST
```

---

## **Important Notes**

* Duplicate values are not allowed
* BST validation must hold for the entire subtree, not only immediate children

---

## **Input Format**

* First line: integer **N** — total number of nodes

* Next `N` lines contain three integers:

```text id="f9m1zk"
value leftChild rightChild
```

where:

* `value` → value of current node
* `leftChild` → index of left child (`-1` if absent)
* `rightChild` → index of right child (`-1` if absent)

The values:

```text id="r2m8vx"
leftChild and rightChild
```

represent the index positions of child nodes in the input list.

Nodes are indexed from:

```text id="n7m2qa"
0 to N-1
```

Root node is always:

```text id="p4m9xp"
0
```

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **-10⁹ ≤ node values ≤ 10⁹**

---

## **Output Format**

Print:

```text id="v1m8zk"
Valid BST
```

or

```text id="g8m2vx"
Invalid BST
```

---

## **Sample Input 1**

```text id="x2m1qa"
3
2 1 2
1 -1 -1
3 -1 -1
```

---

## **Sample Output 1**

```text id="m9v2zk"
Valid BST
```

---

## **Explanation**

Tree structure:

```text id="k4m8qp"
      2
     / \
    1   3
```

All BST properties are satisfied.

---

## **Sample Input 2**

```text id="u7m1xp"
3
5 1 2
1 -1 -1
4 -1 -1
```

---

## **Sample Output 2**

```text id="m4k8qa"
Invalid BST
```

---

## **Explanation**

Tree structure:

```text id="v8m2zk"
      5
     / \
    1   4
```

Right child:

```text id="x1m9vx"
4 < 5
```

which violates BST rules.

---

## **Sample Input 3**

```text id="z7m2qp"
5
10 1 2
5 3 4
15 -1 -1
2 -1 -1
12 -1 -1
```

---

## **Sample Output 3**

```text id="u4m8zk"
Invalid BST
```

---

## **Explanation**

Tree structure:

```text id="k2m1qa"
         10
        /  \
       5    15
      / \
     2  12
```

Node:

```text id="r7m2zk"
12
```

exists inside the left subtree of `10` but:

```text id="u1m8xp"
12 > 10
```

Hence BST property is violated globally.

---

## **Sample Input 4**

```text id="m4k8qa"
1
7 -1 -1
```

---

## **Sample Output 4**

```text id="v8m2zk"
Valid BST
```

---

## **Explanation**

A single-node tree is always a valid BST.

---

## **Efficient Validation Strategy**

A correct BST validation cannot rely only on comparing parent-child nodes.

Instead, maintain:

```text id="x1m9vx"
minimum allowed value
maximum allowed value
```

for every subtree.

---

## **Recursive Validation Rule**

For every node:

```text id="z7m2qp"
minValue < nodeValue < maxValue
```

Recursive ranges:

* Left subtree:

```text id="u4m8zk"
(minValue, currentNodeValue)
```

* Right subtree:

```text id="k2m1qa"
(currentNodeValue, maxValue)
```

---

## **Alternative Insight**

An inorder traversal of a valid BST always produces:

```text id="r7m2zk"
Strictly increasing order
```

Any violation indicates the tree is not a BST.

---

## **Expected Complexity**

### Recursive DFS Validation

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(H)`

Where:

* `N` = number of nodes
* `H` = height of tree

Worst case:

```text id="u1m8xp"
O(N)
```

for a skewed tree.

Balanced BST:

```text id="m4k8qa"
O(log N)
```

recursive stack space.

---

## **Execution Time Limit**

**10 seconds**