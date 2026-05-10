# **Problem 1083: Serialize and Deserialize Binary Tree**

**Company:** Amazon

**Topic:** Trees / DFS

---

## **Problem Description**

A distributed cloud storage system transfers binary tree structures between multiple servers over a network.

Since raw pointer-based tree structures cannot be transmitted directly, the system converts the tree into a compact string representation before transmission.

This process is called:

```text id="m2v8zk"
Serialization
```

Once the data reaches another server, the original tree structure must be reconstructed exactly from the serialized string.

This reconstruction process is called:

```text id="x7m1qa"
Deserialization
```

Your task is to design a system that can:

1. Convert a binary tree into a string format
2. Rebuild the exact same binary tree from that string

The reconstructed tree must preserve:

* Node values
* Tree structure
* Null child positions

---

## **Task**

Implement two operations:

### Serialize

Convert the binary tree into a string.

### Deserialize

Reconstruct the original binary tree from the serialized string.

After deserialization, serialize the reconstructed tree again and print the resulting serialized string.

---

## **Serialization Rules**

Use:

```text id="u3m8qp"
Preorder Traversal
```

with:

```text id="f9m1zk"
#
```

representing null nodes.

Nodes must be separated using:

```text id="r2m8vx"
,
```

---

## **Example Serialization**

Tree:

```text id="n7m2qa"
       1
      / \
     2   3
        / \
       4   5
```

Serialized form:

```text id="p4m9xp"
1,2,#,#,3,4,#,#,5,#,#
```

---

## **Input Format**

* First line: serialized string representing the binary tree

---

## **Constraints**

* **0 ≤ Number of Nodes ≤ 10⁵**
* **-10⁹ ≤ Node Value ≤ 10⁹**

---

## **Output Format**

Print the serialized string obtained after deserializing and reconstructing the binary tree.

---

## **Sample Input 1**

```text id="v1m8zk"
1,2,#,#,3,4,#,#,5,#,#
```

---

## **Sample Output 1**

```text id="g8m2vx"
1,2,#,#,3,4,#,#,5,#,#
```

---

## **Explanation**

Original tree:

```text id="x2m1qa"
       1
      / \
     2   3
        / \
       4   5
```

After deserialization and reconstruction:

* Tree structure remains identical
* Node values remain unchanged

Hence re-serialization produces the same string.

---

## **Sample Input 2**

```text id="m9v2zk"
10,5,#,#,15,12,#,#,20,#,#
```

---

## **Sample Output 2**

```text id="k4m8qp"
10,5,#,#,15,12,#,#,20,#,#
```

---

## **Explanation**

The binary tree is reconstructed successfully from preorder encoding.

---

## **Sample Input 3**

```text id="u7m1xp"
1,#,2,#,3,#,#
```

---

## **Sample Output 3**

```text id="m4k8qa"
1,#,2,#,3,#,#
```

---

## **Explanation**

The serialized string represents a right-skewed tree:

```text id="v8m2zk"
1
 \
  2
   \
    3
```

The structure is restored correctly.

---

## **Sample Input 4**

```text id="x1m9vx"
#
```

---

## **Sample Output 4**

```text id="z7m2qp"
#
```

---

## **Explanation**

The tree is empty.

Serialization and deserialization both preserve the null structure.

---

## **DFS Reconstruction Insight**

Serialization uses:

```text id="u4m8zk"
Root → Left → Right
```

ordering.

During deserialization:

1. Read current node
2. Recursively construct left subtree
3. Recursively construct right subtree

Whenever:

```text id="k2m1qa"
#
```

is encountered:

```text id="r7m2zk"
NULL
```

node is returned.

---

## **Recursive Reconstruction Rule**

For every token:

* Numeric value → create node
* `#` → return null

Advance through serialized tokens sequentially.

---

## **Expected Complexity**

### DFS Serialization + Deserialization

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(N)`

Where:

* `N` = total number of nodes

Additional recursive stack space:

* Worst case skewed tree → `O(N)`
* Balanced tree → `O(log N)`

---

## **Execution Time Limit**

**10 seconds**