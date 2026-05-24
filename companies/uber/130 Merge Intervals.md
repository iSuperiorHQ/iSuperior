# Problem 130: Merge Intervals

**Company:** Uber  

**Category:** Arrays / Greedy Algorithms  

**Difficulty:** Medium  

---

# Problem Description

Large-scale ride-sharing systems continuously manage millions of dynamic time intervals such as:

- driver availability windows  
- ride booking schedules  
- traffic congestion periods  
- surge pricing durations  
- maintenance reservation slots  

Backend scheduling systems must frequently combine overlapping intervals to:

- reduce redundancy  
- optimize memory usage  
- simplify schedule visualization  
- improve real-time querying efficiency  

A naive pairwise overlap comparison becomes computationally expensive for large datasets.

Your task is to design an efficient algorithm that merges all overlapping intervals and returns the minimal set of non-overlapping intervals.

Efficient solutions require candidates to combine:

- interval sorting  
- greedy merging logic  
- sequential overlap processing  

This problem evaluates a candidate’s understanding of:

- interval scheduling  
- greedy algorithms  
- sorting optimizations  
- range merging  
- ordered traversal techniques  

Interviewers expect solutions with:



time complexity.

---

# Task

Given an array of intervals:

```text
[start, end]
```

merge all overlapping intervals and return the resulting non-overlapping intervals.

---

# Interval Overlap Definition

Two intervals overlap if:



Example:

```text
[1,3] and [2,6]
```

overlap because:



Merged interval becomes:

```text
[1,6]
```

---

# Important Rules

- Intervals may appear in arbitrary order  
- Intervals sharing boundary endpoints are considered overlapping  
- Adjacent intervals merge if:
  


- Negative interval values are allowed  
- Fully contained intervals must also merge correctly  
- Final output intervals must be sorted by starting time  

Because traversal follows sorted intervals, merged output remains automatically sorted.

---

# Input Format

First line contains integer:

```text
N
```

representing number of intervals.

Next:

```text
N
```

lines contain two space-separated integers:

```text
start end
```

representing interval boundaries.

---

# Output Format

Print merged non-overlapping intervals in sorted order.

Each interval should appear as:

```text
start end
```

on a separate line.

---

# Constraints

- **1 ≤ N ≤ 2 × 10^5**
- **-10^9 ≤ start ≤ end ≤ 10^9**

---

# Sample Input 1

```text
4
1 3
2 6
8 10
15 18
```

---

# Sample Output 1

```text
1 6
8 10
15 18
```

---

# Explanation

Intervals:

```text
[1,3]
```

and:

```text
[2,6]
```

overlap.

Merged interval:

```text
[1,6]
```

Remaining intervals do not overlap.

---

# Sample Input 2

```text
5
1 4
4 5
6 8
7 10
12 15
```

---

# Sample Output 2

```text
1 5
6 10
12 15
```

---

# Explanation

Because:



intervals:

```text
[1,4]
```

and:

```text
[4,5]
```

share a boundary and are considered overlapping.

Merged interval:

```text
[1,5]
```

Similarly:

```text
[6,8]
```

and:

```text
[7,10]
```

merge into:

```text
[6,10]
```

---

# Sample Input 3

```text
4
-5 -1
-3 2
4 6
5 8
```

---

# Sample Output 3

```text
-5 2
4 8
```

---

# Explanation

Negative intervals follow the same overlap rules.

---

# Why Naive Approaches Fail

A brute-force solution compares every interval pair repeatedly.

This results in:



time complexity.

For large interval collections, repeated overlap checking becomes inefficient.

---

# Key Observation

If intervals are sorted by starting time:

- overlapping intervals appear consecutively  
- merging can be performed greedily in one linear scan  

Thus sorting transforms the problem into sequential interval consolidation.

---

# Optimized Sorting + Greedy Strategy

The optimal solution combines:

- interval sorting  
- greedy interval expansion  

---

# Core Design Idea

## Step 1 — Sort Intervals

Sort intervals based on:

```text
start
```

value in ascending order.

This guarantees potential overlaps appear next to each other.

---

# Greedy Merge Invariant

Maintain a current merged interval:

```text
[currentStart, currentEnd]
```

For every next interval:

---

## Case 1 — Overlapping Interval

If:



merge intervals by updating:



The:

```text
currentStart
```

never changes because intervals are processed in sorted order.

Contained intervals also merge naturally.

Example:

```text
[1,10]
```

already fully contains:

```text
[2,5]
```

---

## Case 2 — Non-Overlapping Interval

If:



store current merged interval and begin a new merge window.

---

# Algorithm Overview

## Step 1 — Sort Intervals

Sort by starting time.

---

## Step 2 — Initialize Merge Window

Start with first interval.

---

## Step 3 — Traverse Remaining Intervals

For every interval:

- merge overlapping ranges  
OR
- finalize previous merged interval and start new one

---

## Step 4 — Store Final Interval

After traversal ends:

- append final merged interval to answer

---

# Why This Works

Sorting ensures all overlapping intervals become adjacent.

The greedy merge process guarantees:

- every overlap is merged exactly once  
- no interval is processed repeatedly  
- final intervals remain non-overlapping and sorted  

---

# Recommended Data Structures

| Structure | Purpose |
|---|---|
| `Array / Vector` | Store intervals |
| `Sorting Algorithm` | Order intervals |
| `Result Array` | Store merged intervals |

---

# Important Edge Cases

Your implementation should correctly handle:

- fully overlapping intervals  
- fully contained intervals  
- non-overlapping intervals  
- single interval input  
- intervals already sorted  
- intervals in reverse order  
- negative intervals  
- duplicate intervals  
- touching boundary intervals  

---

# Expected Complexity

## Optimized Sorting + Greedy Solution

### Sorting Complexity

Sorting intervals requires:



---

### Merge Traversal Complexity

Single linear traversal requires:



---

### Overall Time Complexity

Sorting dominates traversal cost.

Overall complexity:



---

### Space Complexity

Additional merged output storage requires:

```text
O(N)
```

Sorting auxiliary memory depends on implementation and programming language runtime.

---

# Example Walkthrough

Input intervals:

```text
[1,3]
[2,6]
[8,10]
[15,18]
```

---

## Step 1 — Sort Intervals

Already sorted.

---

## Step 2 — Start Merge Window

Current interval:

```text
[1,3]
```

---

## Step 3 — Process [2,6]

Because:



merge intervals.

Updated interval:

```text
[1,6]
```

---

## Step 4 — Process [8,10]

Because:



no overlap exists.

Store:

```text
[1,6]
```

Start new interval:

```text
[8,10]
```

---

## Step 5 — Process [15,18]

No overlap exists.

Final merged intervals:

```text
[1,6]
[8,10]
[15,18]
```

---

# Alternative Approaches

Interviewers may also discuss:

- line sweep algorithms  
- interval trees  
- balanced BST interval merging  
- distributed interval consolidation  

---

# Follow-Up Variants

Interviewers may ask:

- Insert Interval  
- Meeting Rooms scheduling  
- Minimum interval removals  
- Employee free time  
- Interval intersections  

---

# Execution Time Limit

**5 seconds**