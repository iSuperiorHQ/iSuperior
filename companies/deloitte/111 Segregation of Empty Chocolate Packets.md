# **Problem 111: Segregation of Empty Chocolate Packets (Push Zeros to End)**

**Company:** Deloitte

**Category:** Arrays / Two Pointers

**Difficulty:** Easy-Medium

---

# **Problem Description**

A chocolate manufacturing company uses an automated conveyor belt system to transport chocolate packets for packaging.

During quality inspection:

* valid chocolate packets are represented by non-zero integers
* empty or defective packets are represented by:

```text id="m2v8zk"
0
```

The conveyor system must reorganize the packets so that:

1. All empty packets move to the end of the conveyor belt
2. The relative order of all valid packets remains unchanged

Your task is to perform this transformation efficiently:

* in-place
* without using extra arrays
* in linear time complexity

This problem tests a candidate’s understanding of:

* in-place array manipulation
* two-pointer optimization
* stable rearrangement techniques

---

# **Task**

Given an integer array:

```text id="x7m1qa"
packets
```

move all:

```text id="u3m8qp"
0s
```

to the end while maintaining the relative order of non-zero elements.

---

# **Important Rules**

* The operation must be performed:

```text id="f9m1zk"
in-place
```

* Relative ordering of non-zero elements must remain unchanged
* Extra auxiliary arrays are NOT allowed
* All elements must remain inside the same array

---

# **Input Format**

First line contains integer:

```text id="r2m8vx"
N
```

representing size of array.

Second line contains:

```text id="n7m2qa"
N space-separated integers
```

representing chocolate packets.

---

# **Output Format**

Print the modified array after pushing all zeros to the end.

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* **-10⁹ ≤ packets[i] ≤ 10⁹**

---

# **Sample Input 1**

```text id="p4m9xp"
8
0 1 0 3 12 0 5 8
```

---

# **Sample Output 1**

```text id="v1m8zk"
1 3 12 5 8 0 0 0
```

---

# **Explanation**

Non-zero elements in original order:

```text id="g8m2vx"
1 3 12 5 8
```

All zeros are moved to the end while preserving sequence order.

---

# **Sample Input 2**

```text id="x2m1qa"
5
1 2 3 4 5
```

---

# **Sample Output 2**

```text id="m9v2zk"
1 2 3 4 5
```

---

# **Explanation**

No zeros exist.

Array remains unchanged.

---

# **Sample Input 3**

```text id="k4m8qp"
6
0 0 0 0 0 0
```

---

# **Sample Output 3**

```text id="u7m1xp"
0 0 0 0 0 0
```

---

# **Explanation**

All elements are zeros.

No rearrangement needed.

---

# **Sample Input 4**

```text id="m4k8qa"
7
4 0 5 0 0 3 2
```

---

# **Sample Output 4**

```text id="v8m2zk"
4 5 3 2 0 0 0
```

---

# **Explanation**

Non-zero sequence:

```text id="x1m9vx"
4 5 3 2
```

is preserved while all zeros shift to the end.

---

# **Why Naive Approaches Are Suboptimal**

A straightforward solution may:

1. Create an auxiliary array
2. Copy all non-zero elements
3. Fill remaining positions with zeros

This requires:

```text id="z7m2qp"
O(N)
```

extra space.

Interviewers typically expect:

```text id="u4m8zk"
O(1)
```

auxiliary space.

---

# **Optimized Two-Pointer Strategy**

Maintain:

| Pointer        | Purpose                                 |
| -------------- | --------------------------------------- |
| `i`            | Traverses array                         |
| `nonZeroIndex` | Position to place next non-zero element |

---

# **Efficient Algorithm**

Traverse array from left to right.

---

## If Current Element is Non-Zero

Place the non-zero element at:

```text id="k2m1qa"
packets[nonZeroIndex]
```

If indices differ, perform an in-place swap or overwrite.

Then increment:

```text id="r7m2zk"
nonZeroIndex
```

---

## If Current Element is Zero

Do nothing and continue traversal.

---

# **Why This Works**

All non-zero elements are compacted toward the beginning of the array in their original order.

Because non-zero elements are processed from left to right and placed sequentially:

```text id="u1m8xp"
their relative ordering remains preserved
```

Zeros automatically occupy the remaining positions toward the end.

---

# **In-Place Stability Property**

Example:

```text id="m4k8qa"
0 1 0 3 12
```

Processing sequence:

| Step    | Array State |
| ------- | ----------- |
| Move 1  | 1 0 0 3 12  |
| Move 3  | 1 3 0 0 12  |
| Move 12 | 1 3 12 0 0  |

Final result preserves:

```text id="v8m2zk"
1 → 3 → 12
```

ordering.

---

# **Recommended Data Structures**

| Structure           | Purpose          |
| ------------------- | ---------------- |
| `Array`             | Store packets    |
| `Integer Variables` | Pointer tracking |

No additional arrays are required.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* arrays with no zeros
* arrays with all zeros
* zeros at beginning
* zeros at end
* consecutive zeros
* negative integers
* duplicate values

---

# **Expected Complexity**

## Optimized Two-Pointer Solution

### Time Complexity

* **O(N)**

Each element is processed exactly once.

---

### Space Complexity

* **O(1)**

Only constant extra variables are used.

---

# **Example Walkthrough**

Input:

```text id="x1m9vx"
[0, 1, 0, 3, 12]
```

---

## Initial State

```text id="z7m2qp"
nonZeroIndex = 0
```

---

## Traversal

| Current Element | Action           | Array        |
| --------------- | ---------------- | ------------ |
| 0               | Skip             | [0,1,0,3,12] |
| 1               | Place at index 0 | [1,0,0,3,12] |
| 0               | Skip             | [1,0,0,3,12] |
| 3               | Place at index 1 | [1,3,0,0,12] |
| 12              | Place at index 2 | [1,3,12,0,0] |

Final array:

```text id="u4m8zk"
[1,3,12,0,0]
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Stable partitioning
* Auxiliary array solution
* Stream compaction techniques
* Functional array transformations

---

# **Follow-Up Variants**

Interviewers may ask:

* Move negatives to one side
* Segregate even and odd numbers
* Stable partition by condition
* Push specific values to end
* Minimize swap count

---

# **Execution Time Limit**

**3 seconds**