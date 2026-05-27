````md
# Problem 7: Merge K Sorted Lists

**Company:** Google

**Difficulty:** Hard

---

# Category

- Heap / Priority Queue
- Linked List
- Divide and Conquer
- Data Structures
- Merge Techniques

---

# Problem Description

A large-scale search engine continuously receives sorted streams of data from multiple distributed servers.

Each server independently produces a sorted list of integers representing:

- search ranking scores
- event timestamps
- indexed document IDs
- analytics metrics

Before processing the final global result, the system must efficiently combine all sorted lists into a single globally sorted list.

Your task is to design and implement an optimized algorithm to merge:

```text
K Sorted Linked Lists
````

into one sorted linked list.

The solution should be highly efficient because the number of lists and total nodes can become extremely large in production systems.

---

# Business Requirement

Given:

```text
K sorted linked lists
```

merge them into:

```text
One fully sorted linked list
```

while preserving sorted order.

Example:

```text
Input:
1 → 4 → 5
1 → 3 → 4
2 → 6

Output:
1 → 1 → 2 → 3 → 4 → 4 → 5 → 6
```

---

# Functional Requirements

Your implementation must support:

* merging multiple sorted linked lists
* handling empty lists
* duplicate values
* negative numbers
* efficient large-scale merging
* optimized memory usage
* scalable design

---

# Recommended Approach

Preferred interview implementation:

```text
Min Heap (Priority Queue)
```

because it efficiently retrieves the smallest current element among all lists.

---

# Task

Design a system supporting the following operation:

| Operation            | Description                       |
| -------------------- | --------------------------------- |
| `mergeKLists(lists)` | Returns merged sorted linked list |

---

# Input Format

First line contains integer:

```text
K
```

representing number of linked lists.

For each list:

First line contains integer:

```text
N
```

representing size of the linked list.

Second line contains:

```text
N space-separated integers
```

representing nodes of the sorted linked list.

---

# Output Format

Print the merged sorted linked list.

---

# Constraints

* **1 ≤ K ≤ 10⁴**
* **0 ≤ N ≤ 10⁵**
* **-10⁹ ≤ Node Value ≤ 10⁹**
* Sum of all nodes ≤ **10⁵**

---

# Sample Input 1

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

# Sample Output 1

```text
1 1 2 3 4 4 5 6
```

---

# Explanation

Initially heads are:

```text
1, 1, 2
```

Smallest element:

```text
1
```

is selected first.

Then next node from that list is inserted into the heap.

The process continues until all lists become empty.

Final merged sorted list becomes:

```text
1 1 2 3 4 4 5 6
```

---

# Sample Input 2

```text
4
3
-5 2 8
0
2
1 7
3
3 4 9
```

---

# Sample Output 2

```text
-5 1 2 3 4 7 8 9
```

---

# Explanation

Second linked list is empty.

Remaining lists are merged while maintaining sorted order.

---

# Object-Oriented Design Expectations

Your solution should be modular and extensible.

Recommended classes:

| Class          | Responsibility                     |
| -------------- | ---------------------------------- |
| `ListNode`     | Represents linked list node        |
| `MergeService` | Handles merge logic                |
| `MinHeap`      | Maintains smallest current element |
| `InputParser`  | Parses input data                  |

---

# Follow-Up Optimization Questions

Interviewers may ask:

* Can you solve it without extra space?
* What if lists are extremely large?
* How would you merge distributed streams?
* How would you handle real-time incoming lists?
* Can divide-and-conquer improve performance?

---

# Alternative Approaches

| Approach            | Time Complexity | Space Complexity |
| ------------------- | --------------- | ---------------- |
| Brute Force Sorting | O(N log N)      | O(N)             |
| Sequential Merge    | O(NK)           | O(1)             |
| Divide & Conquer    | O(N log K)      | O(log K)         |
| Min Heap            | O(N log K)      | O(K)             |

Where:

* `N` = total number of nodes
* `K` = number of linked lists

---

# Optimal Strategy

## Min Heap Approach

Maintain a min heap containing the current head node of every linked list.

Algorithm:

1. Insert first node of every list into heap
2. Extract minimum node
3. Append it to result list
4. Insert next node of extracted node
5. Repeat until heap becomes empty

---

# Expected Complexity

## Min Heap Solution

### Time Complexity

```text
O(N log K)
```

because each insertion and removal from heap takes:

```text
O(log K)
```

and every node is processed exactly once.

---

### Auxiliary Space Complexity

```text
O(K)
```

because heap stores at most one node from each linked list at any time.

---

# Edge Cases

Your solution should correctly handle:

* empty input lists
* all lists empty
* duplicate values
* single list
* very large K
* negative integers
* varying list sizes

---

# Bonus Follow-Up Questions

Interviewers may ask:

* Why is heap better than sequential merge?
* Can this be parallelized?
* How does divide-and-conquer compare with heap?
* How would you optimize for memory?
* How would you merge infinite sorted streams?

---

# Execution Time Limit

```text
5 seconds
```

```
```