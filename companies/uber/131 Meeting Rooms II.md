# Problem 131: Meeting Rooms II

**Company:** Uber  

**Category:** Heaps / Interval Scheduling  

**Difficulty:** Medium  

---

# Problem Description

Large-scale ride-sharing platforms continuously manage overlapping operational schedules such as:

- driver onboarding sessions  
- regional dispatch meetings  
- vehicle maintenance windows  
- surge monitoring reviews  
- customer support escalations  

Backend scheduling systems must determine the:

```text
minimum number of meeting rooms
```

required so that all meetings can occur without time conflicts.

A naive pairwise overlap simulation becomes inefficient for large scheduling datasets.

Your task is to design an efficient algorithm that calculates the minimum number of meeting rooms required to schedule all meetings successfully.

Efficient solutions require candidates to combine:

- interval sorting  
- overlap tracking  
- greedy allocation strategies  

This problem evaluates a candidate’s understanding of:

- interval scheduling  
- min-heaps  
- sweep-line processing  
- greedy optimization  
- resource allocation problems  

Interviewers expect solutions with:



time complexity.

---

# Task

Given an array of meeting intervals:

```text
[start, end]
```

determine the minimum number of meeting rooms required so that all meetings can be scheduled without overlap conflicts.

---

# Meeting Conflict Definition

Two meetings conflict if:



This means:

- a new room is required when a meeting starts before another meeting ends  

Meetings ending at time:

```text
t
```

release the room immediately.

Therefore, meetings starting exactly at:

```text
t
```

can reuse the same room.

Example:

```text
[1,5]
[5,10]
```

do NOT overlap.

---

# Important Rules

- Meetings may appear in arbitrary order  
- Fully overlapping meetings require separate rooms  
- Negative timestamps are allowed  
- Final answer must represent the minimum rooms required simultaneously  

---

# Input Format

First line contains integer:

```text
N
```

representing number of meetings.

Next:

```text
N
```

lines contain two space-separated integers:

```text
start end
```

representing meeting start and end times.

---

# Output Format

Print one integer representing:

```text
minimum meeting rooms required
```

---

# Constraints

- **1 ≤ N ≤ 2 × 10^5**
- **-10^9 ≤ start < end ≤ 10^9**

---

# Sample Input 1

```text
3
0 30
5 10
15 20
```

---

# Sample Output 1

```text
2
```

---

# Explanation

Meetings:

```text
[0,30]
```

and:

```text
[5,10]
```

overlap.

Therefore:

- room 1 → [0,30]
- room 2 → [5,10]

Meeting:

```text
[15,20]
```

can reuse room 2 after:

```text
[5,10]
```

ends.

Minimum rooms required:

```text
2
```

---

# Sample Input 2

```text
4
7 10
2 4
12 15
16 20
```

---

# Sample Output 2

```text
1
```

---

# Explanation

No meetings overlap.

All meetings can reuse the same room sequentially.

---

# Sample Input 3

```text
5
1 5
2 6
3 7
4 8
5 9
```

---

# Sample Output 3

```text
4
```

---

# Explanation

Maximum simultaneous overlaps occur around time:

```text
4
```

Active meetings:

```text
[1,5]
[2,6]
[3,7]
[4,8]
```

Thus:

```text
4
```

rooms are required.

Meeting:

```text
[5,9]
```

can reuse the room freed by:

```text
[1,5]
```

because meetings ending at:

```text
5
```

do not conflict with meetings starting at:

```text
5
```

---

# Why Naive Approaches Fail

A brute-force solution compares every meeting with every other meeting repeatedly.

This results in:



time complexity.

For very large meeting schedules, repeated overlap checks become inefficient.

---

# Key Observation

At any point:

- only currently active meetings matter  
- the earliest ending meeting determines room availability  

Thus efficiently tracking the:

```text
minimum ending time
```

becomes the core optimization.

---

# Optimized Min-Heap Strategy

The optimal solution combines:

- interval sorting  
- min-heap tracking of active meeting end times  

---

# Core Design Idea

## Step 1 — Sort Meetings

Sort meetings by:

```text
start time
```

in ascending order.

This ensures meetings are processed chronologically.

---

## Step 2 — Maintain Active Rooms

Use a:

```text
Min-Heap
```

to store active meeting end times.

Heap top always stores the:

```text
earliest ending meeting
```

currently occupying a room.

---

# Heap Invariant

After removing reusable meetings:

- heap size equals currently active occupied rooms  

Maximum heap size during traversal equals:

```text
minimum rooms required
```

---

# Greedy Allocation Logic

For every meeting:

---

## Case 1 — Room Reusable

If:



reuse existing room by removing earliest ending meeting from heap.

---

## Case 2 — Overlapping Meeting

If:



allocate new room.

---

## Step 3 — Insert Current Meeting End Time

Insert:

```text
currentEnd
```

into heap.

---

# Algorithm Overview

## Step 1 — Sort Meetings

Sort intervals by start time.

---

## Step 2 — Initialize Min-Heap

Insert first meeting end time.

---

## Step 3 — Process Remaining Meetings

For every meeting:

- compare start time with minimum ending meeting  
- reuse room if possible  
- otherwise allocate new room  

---

## Step 4 — Track Maximum Heap Size

Maximum heap size equals minimum rooms required.

---

# Why This Works

Sorting guarantees chronological processing.

The min-heap efficiently tracks:

- earliest room availability  
- currently active meetings  

The greedy strategy always reuses rooms whenever possible, minimizing total room allocation.

---

# Alternative Prefix Array / Sweep-Line Strategy

Another valid solution uses:

- separate sorted start-time array  
- separate sorted end-time array  

By scanning both arrays simultaneously:

- increment active rooms when meeting starts  
- decrement active rooms when meeting ends  

This also achieves:



time complexity because both arrays must be sorted.

---

# Recommended Data Structures

| Structure | Purpose |
|---|---|
| `Array / Vector` | Store meetings |
| `Sorting Algorithm` | Chronological ordering |
| `Min-Heap` | Track earliest ending room |

---

# Important Edge Cases

Your implementation should correctly handle:

- fully overlapping meetings  
- non-overlapping meetings  
- meetings sharing endpoints  
- single meeting input  
- meetings already sorted  
- meetings in reverse order  
- duplicate meetings  
- very large timestamps  

---

# Expected Complexity

## Optimized Min-Heap Solution

### Sorting Complexity

Sorting meetings requires:



---

### Heap Processing Complexity

Each meeting performs:

- at most one heap insertion  
- at most one heap removal  

Each heap operation costs:



Total heap processing:



---

### Overall Time Complexity

Sorting and heap operations together require:



---

### Space Complexity

Min-heap may store at most:

```text
N
```

meeting end times.

Heap storage requires:



Sorting auxiliary memory depends on implementation and programming language runtime.

---

# Example Walkthrough

Meetings:

```text
[0,30]
[5,10]
[15,20]
```

---

# Heap Representation Note

Heap contents shown below are conceptual logical contents, not actual internal heap-array representation.

---

## Step 1 — Sort Meetings

Already sorted.

---

## Step 2 — Insert First Meeting

Heap:

```text
[30]
```

Rooms occupied:

```text
1
```

---

## Step 3 — Process [5,10]

Because:



meeting overlaps.

Allocate new room.

Heap:

```text
[10,30]
```

Rooms occupied:

```text
2
```

---

## Step 4 — Process [15,20]

Earliest ending meeting ends at:

```text
10
```

Because:



reuse room.

Remove:

```text
10
```

Insert:

```text
20
```

Heap:

```text
[20,30]
```

Maximum rooms used:

```text
2
```

---

# Alternative Approaches

Interviewers may also discuss:

- sweep-line event counting  
- coordinate compression  
- interval graph coloring  
- balanced BST room tracking  

---

# Follow-Up Variants

Interviewers may ask:

- Meeting Rooms I  
- Employee free time  
- Maximum overlap intervals  
- Calendar booking systems  
- CPU task scheduling  

---

# Execution Time Limit

**5 seconds**