# Problem 128: Median from Data Stream

**Company:** Uber  

**Category:** Heaps / Streaming Data Structures  

**Difficulty:** Hard  

---

# Problem Description

Modern ride-sharing systems continuously process massive real-time streams of dynamic numerical data such as:

- trip fares  
- surge multipliers  
- ETA predictions  
- driver response times  
- traffic latency metrics  

Backend analytics services frequently require the:

```text
median
```

of the incoming stream to monitor system stability and detect anomalies.

However, recomputing the median from scratch after every insertion becomes computationally expensive for large-scale streaming systems.

Your task is to design a data structure that efficiently supports:

- continuous insertion of numbers  
- real-time median retrieval  

Efficient solutions require candidates to maintain:

- balanced partitions of streamed data  
- efficient insertion ordering  
- fast access to middle elements  

This problem evaluates a candidate’s understanding of:

- heap-based balancing  
- streaming algorithms  
- online processing  
- dynamic median maintenance  
- priority queue optimization  

Interviewers expect:

- **O(log N)** insertion complexity  
- **O(1)** median retrieval complexity  

---

# Task

Design a data structure:

```text
MedianFinder
```

supporting the following operations:

| Operation | Description |
|---|---|
| `addNum(num)` | Insert number into data stream |
| `findMedian()` | Return current median |

---

# Median Definition

For a sorted sequence:

## Odd Number of Elements

Median is the middle element.

Example:

```text
[1, 3, 5]
```

Median:

```text
3
```

---

## Even Number of Elements

Median is the average of the two middle elements.

Example:

```text
[1, 2, 3, 4]
```

Median:



---

# Important Rules

- Numbers may arrive in arbitrary order  
- Duplicate values are allowed  
- Negative numbers are allowed  
- Median must be retrievable at any time  
- Data stream grows dynamically over time  
- Operations must remain efficient for very large streams  

---

# Required Operations

## addNum(num)

Insert integer:

```text
num
```

into the data stream.

---

## findMedian()

Return current median of all inserted numbers.

For even-sized streams:

- return floating-point median  

If the median is an integer:

- print it without decimal places

---

# Input Format

First line contains integer:

```text
Q
```

representing number of operations.

Next:

```text
Q
```

lines contain operations in one of the following formats:

## Insert Operation

```text
ADD number
```

## Median Query

```text
MEDIAN
```

---

# Output Format

For every:

```text
MEDIAN
```

operation print the current median.

If the median is fractional:

- print decimal value

If the median is an integer:

- print integer without trailing decimal zeros

---

# Constraints

- **1 ≤ Q ≤ 2 × 10^5**
- **-10^9 ≤ num ≤ 10^9**

---

# Sample Input 1

```text
7
ADD 1
ADD 2
MEDIAN
ADD 3
MEDIAN
ADD 10
MEDIAN
```

---

# Sample Output 1

```text
1.5
2
2.5
```

---

# Explanation

---

## Operation 1

```text
ADD 1
```

Stream:

```text
[1]
```

---

## Operation 2

```text
ADD 2
```

Sorted stream:

```text
[1, 2]
```

Median:



---

## Operation 3

```text
MEDIAN
```

Return:

```text
1.5
```

---

## Operation 4

```text
ADD 3
```

Sorted stream:

```text
[1, 2, 3]
```

Median:

```text
2
```

---

## Operation 5

```text
MEDIAN
```

Return:

```text
2
```

---

## Operation 6

```text
ADD 10
```

Sorted stream:

```text
[1, 2, 3, 10]
```

Median:



---

## Operation 7

```text
MEDIAN
```

Return:

```text
2.5
```

---

# Why Naive Approaches Fail

A brute-force solution may:

- insert elements into arrays  
- sort entire dataset after every insertion  

This results in:

- repeated sorting overhead  
- poor scalability  
- excessive processing costs  

Worst-case insertion complexity becomes:

- **O(N log N)**

which fails real-time streaming requirements.

---

# Key Observation

The median divides numbers into two balanced halves:

| Half | Property |
|---|---|
| Left Half | Smaller numbers |
| Right Half | Larger numbers |

Efficient median retrieval requires quick access to:

- largest element of left half  
- smallest element of right half  

---

# Optimized Two-Heap Strategy

The optimal solution uses:

- Max-Heap  
- Min-Heap  

---

# Core Design Idea

## Max-Heap (Left Half)

Stores smaller half of numbers.

Properties:

- largest element accessible at top  
- represents left partition maximum  

---

## Min-Heap (Right Half)

Stores larger half of numbers.

Properties:

- smallest element accessible at top  
- represents right partition minimum  

---

# Heap Balance Invariant

Maintain:



This guarantees:

- balanced partitions  
- constant-time median access  

---

# Median Rules

## Case 1 — Equal Heap Sizes

Median:



---

## Case 2 — Unequal Heap Sizes

Median equals top of larger heap.

---

# Algorithm Overview

## addNum(num)

### Step 1 — Insert into Appropriate Heap

If:

```text
num <= maxHeap.top()
```

insert into:

```text
maxHeap
```

Otherwise insert into:

```text
minHeap
```

If:

```text
maxHeap
```

is empty, insert directly into:

```text
maxHeap
```

---

## Step 2 — Rebalance Heaps

If:

```text
maxHeap
```

size exceeds:

```text
minHeap
```

size by more than:

```text
1
```

move top element from:

```text
maxHeap → minHeap
```

---

If:

```text
minHeap
```

size exceeds:

```text
maxHeap
```

size by more than:

```text
1
```

move top element from:

```text
minHeap → maxHeap
```

---

## findMedian()

### Equal Sizes

Return average of both heap tops.

---

### Unequal Sizes

Return top of larger heap.

---

# Why This Works

The heaps maintain:

- ordered partitions  
- balanced sizes  
- direct middle-element access  

Each insertion performs:

- at most one heap insertion  
- at most one rebalance transfer  

This preserves heap invariants while enabling:

- logarithmic insertion  
- constant-time median retrieval  

---

# Recommended Data Structures

| Structure | Purpose |
|---|---|
| `Max-Heap` | Store smaller half |
| `Min-Heap` | Store larger half |

---

# Important Edge Cases

Your implementation should correctly handle:

- duplicate numbers  
- negative values  
- single-element streams  
- very large streams  
- alternating large/small insertions  
- even-sized streams  
- odd-sized streams  

---

# Expected Complexity

## Optimized Two-Heap Solution

### Time Complexity

| Operation | Complexity |
|---|---|
| `addNum()` | **O(log N)** |
| `findMedian()` | **O(1)** |

Heap insertion and rebalancing require logarithmic time.

Median retrieval uses heap tops directly.

---

### Space Complexity

- **O(N)**

Both heaps together store all inserted elements.

---

# Example Walkthrough

Operations:

```text
ADD 5
ADD 2
ADD 8
ADD 1
MEDIAN
```

---

# Heap Representation Note

Heap contents shown below are conceptual logical contents, not actual internal heap-array representation.

---

## After First Two Insertions

MaxHeap:

```text
[2]
```

MinHeap:

```text
[5]
```

---

## Insert 8

MaxHeap:

```text
[2]
```

MinHeap:

```text
[5, 8]
```

Median:

```text
5
```

---

## Insert 1

MaxHeap:

```text
[2, 1]
```

MinHeap:

```text
[5, 8]
```

Median:



---

# Alternative Approaches

Interviewers may also discuss:

- balanced binary search trees  
- ordered multiset implementations  
- Fenwick tree median tracking  
- segment tree frequency compression  

---

# Follow-Up Variants

Interviewers may ask:

- Sliding window median  
- Weighted median streams  
- Distributed median aggregation  
- Real-time percentile tracking  
- Median removal support  

---

# Execution Time Limit

**5 seconds**