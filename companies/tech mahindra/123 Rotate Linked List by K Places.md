# **Problem 123: Rotate Linked List by K Places**

**Company:** Tech Mahindra

**Category:** Linked List

**Difficulty:** Medium

---

# **Problem Description**

A frequently asked linked list interview problem involves rotating a singly linked list by:

```text id="m2v8zk"
K
```

positions.

Given the head of a linked list, rotate the list toward the right by:

```text id="x7m1qa"
K
```

places.

The rotation operation shifts the last nodes of the list to the front while preserving their relative order.

Efficient solutions require candidates to:

* compute the actual list length
* handle large values of:

```text id="u3m8qp"
K
```

using modulo arithmetic

* temporarily transform the list into a circular linked list
* mathematically identify the new tail and new head nodes

This problem evaluates a candidate’s understanding of:

* linked list traversal
* pointer manipulation
* cycle formation and breaking
* modular arithmetic
* in-place list restructuring

Interviewers typically expect an:

```text id="f9m1zk"
O(N)
```

time solution without using auxiliary arrays.

---

# **Task**

Given:

* head of a singly linked list
* integer:

```text id="r2m8vx"
K
```

rotate the linked list to the right by:

```text id="n7m2qa"
K
```

positions and return the new head.

---

# **Important Rules**

* Rotation is performed toward the:

```text id="p4m9xp"
right
```

* Nodes must NOT be recreated
* Only pointer manipulation is allowed
* The relative order of rotated nodes must remain preserved
* Rotation by:

```text id="v1m8zk"
0
```

places leaves the list unchanged

* If:

```text id="g8m2vx"
K ≥ length
```

use modulo reduction

---

# **Input Format**

First line contains integer:

```text id="x2m1qa"
N
```

representing number of nodes.

Second line contains:

```text id="m9v2zk"
N space-separated integers
```

representing linked list values.

Third line contains integer:

```text id="k4m8qp"
K
```

representing rotation count.

For:

```text id="u7m1xp"
N = 0
```

the linked list is empty and the second line is omitted.

---

# **Output Format**

Print the rotated linked list.

If the linked list is empty, print nothing.

---

# **Constraints**

* **0 ≤ N ≤ 10⁵**
* **0 ≤ Node Value ≤ 10⁹**
* **0 ≤ K ≤ 10⁹**

---

# **Sample Input 1**

```text id="m4k8qa"
5
1 2 3 4 5
2
```

---

# **Sample Output 1**

```text id="v8m2zk"
4 5 1 2 3
```

---

# **Explanation**

Original list:

```text id="x1m9vx"
1 → 2 → 3 → 4 → 5
```

After rotating right by:

```text id="z7m2qp"
2
```

positions:

```text id="u4m8zk"
4 → 5 → 1 → 2 → 3
```

---

# **Sample Input 2**

```text id="k2m1qa"
4
10 20 30 40
1
```

---

# **Sample Output 2**

```text id="r7m2zk"
40 10 20 30
```

---

# **Explanation**

Last node becomes the new head after one rotation.

---

# **Sample Input 3**

```text id="u1m8xp"
3
1 2 3
4
```

---

# **Sample Output 3**

```text id="m4k8qa"
3 1 2
```

---

# **Explanation**

Length of list:

```text id="v8m2zk"
3
```

Effective rotation:

Thus rotate right by:

```text id="x1m9vx"
1
```

position.

Result:

```text id="z7m2qp"
3 → 1 → 2
```

---

# **Sample Input 4**

```text id="u4m8zk"
0
3
```

---

# **Sample Output 4**

```text id="k2m1qa"
```

---

# **Explanation**

The linked list is empty.

Rotation does not modify the list.

---

# **Why Naive Approaches Fail**

Repeatedly moving the last node to the front:

```text id="r7m2zk"
K
```

times requires:

```text id="u1m8xp"
O(N × K)
```

time complexity.

This becomes inefficient for very large:

```text id="m4k8qa"
K
```

values.

Interviewers expect a single-pass restructuring approach.

---

# **Key Observation**

Suppose list length is:

```text id="v8m2zk"
L
```

Rotating by:

```text id="x1m9vx"
K
```

positions is equivalent to rotating by:

This eliminates unnecessary full rotations.

---

# **Optimized Circular Linked List Strategy**

The optimal approach uses:

* length calculation
* temporary cycle creation
* mathematical breakpoint detection

---

# **Algorithm Overview**

---

## Step 1 — Compute Length

Traverse the linked list to determine:

* total number of nodes:

```text id="z7m2qp"
L
```

* current tail node

---

## Step 2 — Reduce Rotations

Compute effective rotation:

If:

```text id="u4m8zk"
K = 0
```

return original list.

---

## Step 3 — Create Circular Linked List

Connect:

```text id="k2m1qa"
tail.next = head
```

forming a cycle.

---

## Step 4 — Find New Tail

After modulo reduction, the new tail is located at index:

from the original head.

---

## Step 5 — Identify New Head

The node after the new tail becomes:

```text id="r7m2zk"
newHead
```

---

## Step 6 — Break the Cycle

Set:

```text id="u1m8xp"
newTail.next = NULL
```

to restore the singly linked list structure.

---

# **Why This Works**

By converting the linked list into a temporary cycle:

* rotations become pointer shifts
* no node movement is required
* restructuring occurs in constant extra space

The mathematical breakpoint guarantees the correct rotated order.

---

# **Recommended Data Structures**

| Structure            | Purpose                     |
| -------------------- | --------------------------- |
| `Singly Linked List` | Input storage               |
| `Pointers`           | Traversal and restructuring |

No auxiliary arrays are required.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* empty linked lists
* single-node lists
* very large:

```text id="m4k8qa"
K
```

values

* rotation by:

```text id="v8m2zk"
0
```

* rotation equal to list length
* rotation greater than list length

---

# **Expected Complexity**

## Optimized Circular Rotation Solution

### Time Complexity

* **O(N)**

Length calculation, breakpoint traversal, and cycle breaking together require linear traversal of the linked list.

---

### Space Complexity

* **O(1)**

Only pointer variables are used.

---

# **Example Walkthrough**

Input:

```text id="x1m9vx"
1 → 2 → 3 → 4 → 5
K = 2
```

---

## Compute Length

Length:

```text id="z7m2qp"
5
```

---

## Effective Rotation

---

## Create Cycle

```text id="u4m8zk"
1 → 2 → 3 → 4 → 5
↑                 ↓
└─────────────────┘
```

---

## Find New Tail

New tail index:

Node:

```text id="k2m1qa"
3
```

becomes new tail.

---

## Break Cycle

New head:

```text id="r7m2zk"
4
```

Final list:

```text id="u1m8xp"
4 → 5 → 1 → 2 → 3
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* deque-based rotation
* repeated node movement
* doubly linked list optimization
* recursive rotation

---

# **Follow-Up Variants**

Interviewers may ask:

* Rotate left by:

```text id="m4k8qa"
K
```

places

* Rotate doubly linked list
* Rotate circular linked list
* Reverse nodes in groups
* Split and merge rotations

---

# **Execution Time Limit**

**3 seconds**