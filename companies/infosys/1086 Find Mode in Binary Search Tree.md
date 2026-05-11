# **Problem 1086: Find Mode in Binary Search Tree**

**Company:** Infosys

**Topic:** BST / DFS

---

## **Problem Description**

A data analytics platform stores transaction identifiers inside a Binary Search Tree (BST) for efficient searching and aggregation.

Certain transaction values may appear multiple times due to repeated events.
To optimize reporting, the system needs to identify the value that appears most frequently inside the BST.

The most frequently occurring value in a dataset is called the:

```text id="m2v8zk"
Mode
```

Your task is to traverse the Binary Search Tree and determine the mode value(s).

If multiple values share the same highest frequency, print all such values in increasing order.

---

## **BST Properties**

A Binary Search Tree satisfies:

* Left subtree values `<` current node value
* Right subtree values `≥` current node value

Duplicate values may exist only in the right subtree.

---

## **Task**

Find all values that occur with maximum frequency in the BST.

---

## **Input Format**

* First line: integer **N** — total number of nodes

* Next `N` lines contain:

```text id="x7m1qa"
value leftChild rightChild
```

where:

* `value` → value of current node
* `leftChild` → index of left child (`-1` if absent)
* `rightChild` → index of right child (`-1` if absent)

The child references represent node indices in the input list.

Nodes are indexed from:

```text id="u3m8qp"
0 to N-1
```

Root node is always:

```text id="f9m1zk"
0
```

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **-10⁹ ≤ node values ≤ 10⁹**

---

## **Output Format**

Print all mode values in increasing order separated by spaces.

---

## **Sample Input 1**

```text id="r2m8vx"
5
2 1 2
1 -1 -1
2 3 4
2 -1 -1
3 -1 -1
```

---

## **Sample Output 1**

```text id="n7m2qa"
2
```

---

## **Explanation**

Tree structure:

```text id="p4m9xp"
        2
       / \
      1   2
         / \
        2   3
```

Frequencies:

```text id="v1m8zk"
1 → 1 time
2 → 3 times
3 → 1 time
```

Mode:

```text id="g8m2vx"
2
```

---

## **Sample Input 2**

```text id="x2m1qa"
7
5 1 2
3 3 4
7 5 6
3 -1 -1
4 -1 -1
7 -1 -1
8 -1 -1
```

---

## **Sample Output 2**

```text id="m9v2zk"
3 7
```

---

## **Explanation**

Frequencies:

```text id="k4m8qp"
3 → 2 times
4 → 1 time
5 → 1 time
7 → 2 times
8 → 1 time
```

Both:

```text id="u7m1xp"
3 and 7
```

share the highest frequency.

Hence both are printed in increasing order.

---

## **Sample Input 3**

```text id="m4k8qa"
1
10 -1 -1
```

---

## **Sample Output 3**

```text id="v8m2zk"
10
```

---

## **Explanation**

Only one node exists in the BST.

Hence that value itself becomes the mode.

---

## **Sample Input 4**

```text id="x1m9vx"
6
4 1 2
2 3 4
6 -1 5
2 -1 -1
3 -1 -1
6 -1 -1
```

---

## **Sample Output 4**

```text id="z7m2qp"
2 6
```

---

## **Explanation**

Tree structure:

```text id="u4m8zk"
        4
       / \
      2   6
     / \   \
    2   3   6
```

Frequencies:

```text id="k2m1qa"
2 → 2 times
3 → 1 time
4 → 1 time
6 → 2 times
```

Modes:

```text id="r7m2zk"
2 6
```

---

## **DFS Traversal Insight**

An inorder traversal of a BST produces values in sorted order.

This property allows efficient frequency counting while traversing.

---

## **Efficient Strategy**

During inorder traversal:

Maintain:

```text id="u1m8xp"
previousValue
currentFrequency
maximumFrequency
```

Whenever the current value changes:

* Reset frequency counter
* Compare with maximum frequency

Track all values having highest occurrence count.

---

## **Alternative Approach**

Use:

* DFS traversal
* HashMap frequency counting

Then extract all values with maximum frequency.

---

## **Expected Complexity**

### Inorder DFS Approach

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(H)`

Where:

* `N` = number of nodes
* `H` = height of BST

Worst case skewed BST:

```text id="m4k8qa"
O(N)
```

Balanced BST:

```text id="v8m2zk"
O(log N)
```

recursive stack space.

---

## **HashMap Alternative**

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(N)`

---

## **Execution Time Limit**

**10 seconds**