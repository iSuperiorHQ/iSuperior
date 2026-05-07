# **Problem 1068: Identical Binary Trees Validation**

**Company:** Wipro

**Topic:** Trees / Recursion

---

## **Problem Description**

Two binary trees are said to be **identical** if:

1. They have exactly the same structure
2. Corresponding nodes contain the same values

You are given two independently constructed binary trees. Your task is to determine whether both trees are completely identical.

This problem is commonly used in compiler design systems, hierarchical data comparison engines, and recursive structure validation.

---

## **Task**

Write a recursive algorithm to verify whether two binary trees are:

* Structurally identical
* Value-wise identical

Return:

```text id="ebwlnk"
Identical
```

if both conditions are satisfied.

Otherwise return:

```text id="pjlwm5"
Not Identical
```

---

## **Input Representation**

Each tree is represented using **level-order traversal**.

* `-1` represents a NULL node

---

## **Input Format**

* First line: integer **n1** — number of nodes in Tree 1

* Second line: level-order traversal of Tree 1

* Third line: integer **n2** — number of nodes in Tree 2

* Fourth line: level-order traversal of Tree 2

---

## **Constraints**

* **1 ≤ n1, n2 ≤ 10⁵**
* Node values range from:

```text id="xg1vqs"
-10⁹ to 10⁹
```

---

## **Output Format**

Print:

```text id="a0c7cf"
Identical
```

or

```text id="87d8yo"
Not Identical
```

---

## **Sample Input 1**

```text id="o8m3yn"
7
1 2 3 4 5 6 7
7
1 2 3 4 5 6 7
```

---

## **Sample Output 1**

```text id="lxd3qj"
Identical
```

---

## **Explanation**

Both trees:

```text id="jol29q"
        1
      /   \
     2     3
    / \   / \
   4   5 6   7
```

* Same structure
* Same node values

Hence both trees are identical.

---

## **Sample Input 2**

```text id="yw3d11"
7
1 2 3 4 5 -1 7
7
1 2 3 4 5 6 7
```

---

## **Sample Output 2**

```text id="3by8b9"
Not Identical
```

---

## **Explanation**

Tree 1:

```text id="7w5vbq"
        1
      /   \
     2     3
    / \     \
   4   5     7
```

Tree 2:

```text id="qjlwmk"
        1
      /   \
     2     3
    / \   / \
   4   5 6   7
```

Structures are different.

---

## **Sample Input 3**

```text id="ol9sh4"
3
1 2 3
3
1 3 2
```

---

## **Sample Output 3**

```text id="4f4f5t"
Not Identical
```

---

## **Explanation**

Structures are same, but node values differ.

---

## **Recursive Validation Logic**

Two trees are identical if:

```text id="ujstfm"
1. Both nodes are NULL
OR
2. Values are equal AND
   Left subtrees are identical AND
   Right subtrees are identical
```

---

## **Expected Complexity**

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(H)` recursive stack

  * `H` = height of tree

---

## **What they check:**

* Recursive tree traversal
* Structural comparison logic
* Base case handling
* Null node validation
* Large tree efficiency

---

## **Execution Time Limit**

**10 seconds**