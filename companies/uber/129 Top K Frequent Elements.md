# Problem 129: Top K Frequent Elements

**Company:** Uber  

**Category:** Heaps / Hashing  

**Difficulty:** Medium  

---

# Problem Description

Modern ride-sharing platforms continuously analyze massive streams of operational data such as:

- frequently requested pickup zones  
- most searched destinations  
- commonly used promo codes  
- high-demand ride categories  
- repeated driver allocation patterns  

Backend analytics systems often need to identify the:

```text
Top K most frequent elements
```

from extremely large datasets in real time.

A brute-force frequency sorting approach becomes computationally expensive when the dataset grows to millions of entries.

Your task is to design an efficient algorithm that returns the:

```text
K most frequent elements
```

from a given integer array.

Efficient solutions require candidates to combine:

- frequency counting  
- heap-based optimization  
- bounded-memory processing  

This problem evaluates a candidate’s understanding of:

- hash maps  
- heap prioritization  
- frequency analysis  
- streaming-style optimizations  
- top-k extraction techniques  

Interviewers expect solutions with:



time complexity.

---

# Task

Given an integer array:

```text
nums
```

and an integer:

```text
K
```

return the:

```text
K most frequent elements
```

in the array.

The answer may be returned in any order unless otherwise specified.

---

# Frequency Definition

Frequency of an element equals:

```text
number of occurrences
```

of that element inside the array.

Example:

```text
nums = [1,1,1,2,2,3]
```

Frequencies:

| Element | Frequency |
|---|---|
| 1 | 3 |
| 2 | 2 |
| 3 | 1 |

If:

```text
K = 2
```

answer becomes:

```text
[1,2]
```

---

# Important Rules

- Duplicate values are allowed  
- Negative numbers are allowed  
- Array may contain large frequency distributions  
- Output order does not matter  
- Efficient heap optimization is expected  

---

# Input Format

First line contains integer:

```text
N
```

representing array size.

Second line contains:

```text
N
```

space-separated integers.

Third line contains integer:

```text
K
```

---

# Output Format

Print:

```text
K
```

most frequent elements separated by spaces.

If multiple valid answers exist:

- print any valid ordering

---

# Constraints

- **1 ≤ N ≤ 2 × 10^5**
- **-10^9 ≤ nums[i] ≤ 10^9**
- **1 ≤ K ≤ number of unique elements**

---

# Sample Input 1

```text
6
1 1 1 2 2 3
2
```

---

# Sample Output 1

```text
1 2
```

---

# Explanation

Frequencies:

| Element | Count |
|---|---|
| 1 | 3 |
| 2 | 2 |
| 3 | 1 |

Top:

```text
2
```

frequent elements are:

```text
1, 2
```

---

# Sample Input 2

```text
8
4 4 4 6 6 7 7 7
1
```

---

# Sample Output 2

```text
4
```

---

# Explanation

Frequencies:

| Element | Count |
|---|---|
| 4 | 3 |
| 6 | 2 |
| 7 | 3 |

Both:

```text
4
```

and:

```text
7
```

have maximum frequency.

Any valid answer is accepted.

---

# Sample Input 3

```text
7
5 5 -1 -1 -1 2 2
2
```

---

# Sample Output 3

```text
-1 5
```

---

# Explanation

Frequencies:

| Element | Count |
|---|---|
| -1 | 3 |
| 5 | 2 |
| 2 | 2 |

Top:

```text
2
```

frequent elements may include:

```text
-1
```

and either:

```text
5
```

or:

```text
2
```

because both have equal frequency.

---

# Why Naive Approaches Fail

A brute-force solution may:

- count frequencies  
- sort all unique elements by frequency  

Sorting entire frequency lists requires:



where:

```text
M
```

represents number of unique elements.

For large datasets, this becomes unnecessarily expensive when only:

```text
K
```

top elements are required.

---

# Key Observation

At any point, only the:

```text
K highest-frequency
```

elements matter.

There is no need to fully sort all frequencies.

This naturally suggests using a:

```text
bounded min-heap
```

to maintain only the best candidates.

---

# Optimized Frequency Map + Min-Heap Strategy

The optimal solution combines:

- Frequency Map  
- Min-Heap of size:
  
```text
K
```

---

# Core Design Idea

## Step 1 — Frequency Counting

Use hash map:

```text
element → frequency
```

This allows:

- O(1) average frequency updates  

---

## Step 2 — Maintain Min-Heap

Store pairs:

```text
(frequency, element)
```

inside a:

```text
Min-Heap
```

ordered by frequency.

Heap top always stores the:

```text
minimum frequency
```

among the current top-K candidates.

---

# Heap Invariant

Heap size should never exceed:

```text
K
```

If heap size becomes:

```text
K + 1
```

remove the minimum-frequency element.

Thus the heap always stores the:

```text
K most frequent elements
```

seen so far.

---

# Algorithm Overview

## Step 1 — Build Frequency Map

Traverse array once and compute frequencies.

---

## Step 2 — Process Unique Elements

For every:

```text
(element, frequency)
```

pair:

- insert into min-heap  
- if heap size exceeds:
  
```text
K
```

remove heap top

---

## Step 3 — Extract Final Answer

Remaining heap elements form the:

```text
Top K frequent elements
```

---

# Why This Works

The min-heap always preserves the:

```text
K highest frequencies
```

because smaller-frequency elements are discarded immediately.

This avoids unnecessary full sorting while maintaining correctness.

---

# Recommended Data Structures

| Structure | Purpose |
|---|---|
| `Hash Map` | Frequency counting |
| `Min-Heap` | Maintain top K elements |

---

# Important Edge Cases

Your implementation should correctly handle:

- duplicate-heavy arrays  
- all elements identical  
- negative numbers  
- multiple elements with same frequency  
- very large arrays  
-:
  
```text
K = 1
```

-:
  
```text
K = uniqueElements
```

---

# Expected Complexity

## Optimized Min-Heap Solution

### Frequency Counting

Traverse array once:



---

### Heap Operations

There are:

```text
M
```

unique elements.

Each heap insertion/removal costs:



Total heap complexity:



---

### Overall Time Complexity

Total complexity becomes:



Since:



overall complexity simplifies to:



---

### Space Complexity

-:
  
```text
O(M)
```

for frequency map

-:
  
```text
O(K)
```

for min-heap

Total:



---

# Example Walkthrough

Input:

```text
nums = [1,1,1,2,2,3]
K = 2
```

---

# Heap Representation Note

Heap contents shown below are conceptual logical contents, not actual internal heap-array ordering.

---

## Step 1 — Frequency Map

| Element | Frequency |
|---|---|
| 1 | 3 |
| 2 | 2 |
| 3 | 1 |

---

## Step 2 — Heap Processing

Insert:

```text
(3,1)
```

Heap:

```text
[(3,1)]
```

---

Insert:

```text
(2,2)
```

Heap:

```text
[(2,2),(3,1)]
```

---

Insert:

```text
(1,3)
```

Heap size becomes:

```text
3
```

Remove minimum frequency:

```text
(1,3)
```

---

## Final Heap

```text
[(2,2),(3,1)]
```

Answer:

```text
[1,2]
```

---

# Alternative Approaches

Interviewers may also discuss:

- bucket sort frequency grouping  
- quickselect partitioning  
- balanced BST frequency tracking  
- streaming top-k analytics  

---

# Follow-Up Variants

Interviewers may ask:

- Top K frequent words  
- Real-time streaming frequency tracker  
- Sliding window top-k frequencies  
- Distributed frequency aggregation  
- Approximate counting using sketches  

---

# Execution Time Limit

**5 seconds**