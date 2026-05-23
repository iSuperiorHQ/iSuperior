# **Problem 124: Palindrome Linked List Verification**

**Company:** Tech Mahindra

**Category:** Linked List / Two Pointers

**Difficulty:** Medium-Hard

---

# **Problem Description**

A frequently asked advanced linked list interview problem involves determining whether a singly linked list forms a:

```text id="m2v8zk"
palindrome
```

A linked list is considered palindromic if the sequence of node values reads identically:

* from left to right
* from right to left

The challenge is to solve the problem efficiently using:

* fast and slow pointer traversal
* in-place linked list reversal
* constant auxiliary memory

Efficient solutions require candidates to:

* locate the midpoint of the linked list using the fast and slow pointer technique
* reverse the second half of the list entirely in-place
* compare both halves node-by-node
* restore the linked list to its original structure before returning

This problem evaluates a candidate’s understanding of:

* linked list traversal
* pointer manipulation
* in-place reversal
* midpoint detection
* memory optimization

Interviewers typically expect an:

```text id="x7m1qa"
O(N)
```

time solution using:

```text id="u3m8qp"
O(1)
```

extra space.

---

# **Task**

Given the head of a singly linked list, determine whether the linked list forms a palindrome.

Return:

```text id="f9m1zk"
YES
```

if the linked list is palindromic, otherwise return:

```text id="r2m8vx"
NO
```

---

# **Important Rules**

* Nodes must NOT be copied into arrays or stacks
* Only pointer manipulation is allowed
* The solution must use constant auxiliary space
* The linked list should be restored to its original structure before returning
* Both odd-length and even-length linked lists must be handled correctly
* An empty linked list is considered a valid palindrome

---

# **Input Format**

First line contains integer:

```text id="n7m2qa"
N
```

representing number of nodes.

Second line contains:

```text id="p4m9xp"
N space-separated integers
```

representing linked list values.

For:

```text id="v1m8zk"
N = 0
```

the linked list is empty and the second line is omitted.

---

# **Output Format**

Print:

```text id="g8m2vx"
YES
```

if the linked list is a palindrome.

Otherwise print:

```text id="x2m1qa"
NO
```

---

# **Constraints**

* **0 ≤ N ≤ 10⁵**
* **0 ≤ Node Value ≤ 10⁹**

---

# **Sample Input 1**

```text id="m9v2zk"
5
1 2 3 2 1
```

---

# **Sample Output 1**

```text id="k4m8qp"
YES
```

---

# **Explanation**

Original linked list:

```text id="u7m1xp"
1 → 2 → 3 → 2 → 1
```

Forward traversal:

```text id="m4k8qa"
1 2 3 2 1
```

Reverse traversal:

```text id="v8m2zk"
1 2 3 2 1
```

Both sequences are identical.

Hence the linked list is a palindrome.

---

# **Sample Input 2**

```text id="x1m9vx"
4
1 2 2 1
```

---

# **Sample Output 2**

```text id="z7m2qp"
YES
```

---

# **Explanation**

The linked list remains identical when traversed in reverse order.

---

# **Sample Input 3**

```text id="u4m8zk"
4
1 2 3 4
```

---

# **Sample Output 3**

```text id="k2m1qa"
NO
```

---

# **Explanation**

Forward traversal:

```text id="r7m2zk"
1 2 3 4
```

Reverse traversal:

```text id="u1m8xp"
4 3 2 1
```

The sequences differ.

Thus the linked list is not palindromic.

---

# **Sample Input 4**

```text id="m4k8qa"
0
```

---

# **Sample Output 4**

```text id="v8m2zk"
YES
```

---

# **Explanation**

An empty linked list is considered a palindrome.

---

# **Why Naive Approaches Are Discouraged**

A common beginner solution involves:

* copying node values into an array
* reversing the array
* comparing values

While functionally correct, this requires:

```text id="x1m9vx"
O(N)
```

extra memory.

Interviewers usually expect an in-place linked list solution.

---

# **Key Observation**

To compare the first half and second half efficiently:

* locate the midpoint
* reverse the second half
* compare corresponding nodes

This avoids auxiliary storage.

---

# **Optimized Two-Pointer Strategy**

The optimal approach uses:

* fast and slow pointer traversal
* in-place linked list reversal
* sequential comparison

---

# **Algorithm Overview**

---

## Step 1 — Find Midpoint

Use two pointers:

| Pointer | Movement        |
| ------- | --------------- |
| `slow`  | moves one step  |
| `fast`  | moves two steps |

When:

```text id="z7m2qp"
fast
```

reaches the end:

```text id="u4m8zk"
slow
```

points to the midpoint.

This works for both odd-length and even-length linked lists.

---

# **Midpoint Visualization**

For list:

```text id="k2m1qa"
1 → 2 → 3 → 2 → 1
```

Pointers move as:

| Iteration | slow | fast |
| --------- | ---- | ---- |
| Start     | 1    | 1    |
| 1         | 2    | 3    |
| 2         | 3    | 1    |

Midpoint located at:

```text id="r7m2zk"
3
```

---

## Step 2 — Handle Odd-Length Lists

For odd-length linked lists, the middle node does NOT participate in comparison.

Comparison begins from the node after the midpoint.

Example:

```text id="u1m8xp"
1 → 2 → 3 → 2 → 1
```

Middle node:

```text id="m4k8qa"
3
```

is skipped during comparison.

---

## Step 3 — Reverse Second Half

Reverse all nodes after the midpoint entirely in-place.

Example:

Before reversal:

```text id="v8m2zk"
1 → 2 → 3 → 2 → 1
```

Second half:

```text id="x1m9vx"
2 → 1
```

After reversal:

```text id="z7m2qp"
1 → 2
```

---

## Step 4 — Compare Both Halves

Traverse simultaneously:

* first half from original head
* second half from reversed section

Compare values node-by-node.

If any mismatch occurs:

```text id="u4m8zk"
NOT PALINDROME
```

---

## Step 5 — Restore Original List

Reverse the second half again to restore the original linked list structure.

This prevents unintended data corruption.

---

# **Why This Works**

Reversing the second half transforms the palindrome verification problem into a straightforward sequential comparison.

The algorithm guarantees:

* linear traversal
* constant auxiliary space
* no redundant storage

---

# **Recommended Data Structures**

| Structure            | Purpose                |
| -------------------- | ---------------------- |
| `Singly Linked List` | Input storage          |
| `Pointers`           | Traversal and reversal |

No auxiliary arrays or stacks are allowed.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* empty linked lists
* single-node lists
* odd-length lists
* even-length lists
* repeated values
* large linked lists

---

# **Expected Complexity**

## Optimized In-Place Solution

### Time Complexity

* **O(N)**

The linked list is traversed a constant number of times:

* midpoint detection
* second-half reversal
* comparison
* restoration

---

### Space Complexity

* **O(1)**

Only pointer variables are used.

---

# **Example Walkthrough**

Input:

```text id="k2m1qa"
1 → 2 → 3 → 2 → 1
```

---

## Find Midpoint

Middle node:

```text id="r7m2zk"
3
```

---

## Skip Middle Node

Since the list length is odd:

```text id="u1m8xp"
3
```

does not participate in comparison.

---

## Reverse Second Half

Original second half:

```text id="m4k8qa"
2 → 1
```

Reversed:

```text id="v8m2zk"
1 → 2
```

---

## Compare Halves

| First Half | Reversed Second Half |
| ---------- | -------------------- |
| 1          | 1                    |
| 2          | 2                    |

All nodes match.

Result:

```text id="x1m9vx"
YES
```

---

## Restore List

Second half is reversed again.

Final restored list:

```text id="z7m2qp"
1 → 2 → 3 → 2 → 1
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* stack-based palindrome verification
* recursive comparison
* doubly linked list optimization
* rolling hash techniques

---

# **Follow-Up Variants**

Interviewers may ask:

* Check palindrome in doubly linked list
* Ignore specific values during comparison
* Reverse nodes in groups
* Detect cyclic palindromic structures
* Longest palindromic linked segment

---

# **Execution Time Limit**

**3 seconds**