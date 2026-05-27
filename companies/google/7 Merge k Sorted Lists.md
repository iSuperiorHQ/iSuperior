# **Problem 7: Merge k Sorted Lists**

**Company:** Google

**Category:** Heap / Linked List / Divide and Conquer

**Difficulty:** Hard

---

# **Problem Description**

You are given `k` sorted linked lists containing integers in non-decreasing order.

Your task is to merge all the linked lists into a single sorted linked list and return its head.

The merged linked list must also remain sorted.

This problem commonly appears in distributed systems, external sorting systems, and large-scale stream processing applications where multiple sorted datasets must be merged efficiently.

---

# **Business Requirement**

A search engine stores sorted logs across multiple machines.

Each machine continuously generates logs sorted by timestamp.

To generate a unified analytics report, the system must efficiently merge all sorted streams into one globally sorted stream.

---

# **Task**

Design and implement an efficient algorithm to merge all sorted linked lists into one sorted linked list.

---

# **Function Signature**

```cpp
ListNode* mergeKLists(vector<ListNode*>& lists)
```

---

# **Class Definition**

```cpp
class ListNode {
public:
    int val;
    ListNode* next;

    ListNode(int x) {
        val = x;
        next = nullptr;
    }
};
```

---

# **Input Format**

First line contains integer:

```text
k
```

representing number of linked lists.

For each linked list:

* First line contains integer:

```text
n
```

representing size of the linked list.

* Second line contains `n` space-separated integers representing elements of the linked list in sorted order.

---

# **Output Format**

Return the head of the merged sorted linked list.

For driver-based implementations, print all elements of the merged linked list.

---

# **Constraints**

* **1 ≤ k ≤ 10⁴**
* **0 ≤ n ≤ 10⁴**
* **-10⁴ ≤ Node.val ≤ 10⁴**
* Sum of all nodes will not exceed **10⁵**

---

# **Sample Input 1**

```text
3
3
1 4 5
3
1 3 4
2
2 6
```

---

# **Sample Output 1**

```text
1 1 2 3 4 4 5 6
```

---

# **Explanation**

The linked lists are:

```text
1 → 4 → 5
1 → 3 → 4
2 → 6
```

After merging all lists:

```text
1 → 1 → 2 → 3 → 4 → 4 → 5 → 6
```

---

# **Sample Input 2**

```text
2
0

3
2 2 2
```

---

# **Sample Output 2**

```text
2 2 2
```

---

# **Explanation**

First linked list is empty.

Second linked list:

```text
2 → 2 → 2
```

Merged result remains unchanged.

---

# **Sample Input 3**

```text
4
1
1
1
0
1
5
0
```

---

# **Sample Output 3**

```text
1 5
```

---

# **Approaches**

| Approach | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| Brute Force Collection + Sort | O(N log N) | O(N) |
| Sequential Merge | O(kN) | O(1) |
| Min Heap (Priority Queue) | O(N log k) | O(k) |
| Divide and Conquer | O(N log k) | O(log k) |

Where:

* `N` = total number of nodes
* `k` = number of linked lists

---

# **Recommended Interview Approach**

Preferred interview implementation:

```text
Min Heap (Priority Queue)
```

because it efficiently selects the minimum element among all active linked lists.

---

# **Min Heap Strategy**

1. Insert the head node of every non-empty linked list into a min heap.
2. Extract the smallest node from the heap.
3. Add the extracted node to the result linked list.
4. If extracted node contains a next node:

   * insert the next node into heap
5. Repeat until heap becomes empty.

---

# **Example Walkthrough**

Input:

```text
1→4→5
1→3→4
2→6
```

Initial Heap:

```text
1, 1, 2
```

Processing order:

```text
Take 1
Take 1
Take 2
Take 3
Take 4
Take 4
Take 5
Take 6
```

Final merged linked list:

```text
1→1→2→3→4→4→5→6
```

---

# **Expected Complexity**

## Min Heap Approach

### Time Complexity

* **O(N log k)**

because every insertion and removal from heap requires:

```text
O(log k)
```

and each node is processed exactly once.

---

### Space Complexity

* **O(k)**

for storing at most one node from each linked list in the heap.

---

# **Edge Cases**

Your solution should correctly handle:

* empty linked lists
* all linked lists empty
* duplicate values
* negative numbers
* single linked list
* very large number of linked lists
* unequal sized linked lists

---

# **Follow-Up Questions**

Interviewers may ask:

* Can you solve this without extra heap space?
* Why is heap more efficient than sequential merging?
* How would you merge sorted streams from distributed systems?
* Can this be optimized for external memory sorting?
* How would you merge infinitely large sorted streams?

---

# **Execution Time Limit**

```text
2 seconds
```