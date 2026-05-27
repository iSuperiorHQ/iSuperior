````md id="3n8vqx"
# Problem 24: Split Bottles Between Two Boxes Maintaining Ratio

**Company:** Amazon

**Difficulty:** Hard

---

# Category

- Greedy
- Binary Search
- Number Theory
- Mathematical Optimization
- Arrays
- Meet-in-the-Middle

---

# Problem Description

A beverage distribution company stores thousands of bottles in a warehouse.

Each bottle contains a certain volume of liquid.

For shipping optimization, the company wants to divide all bottles into:

```text
Two Storage Boxes
````

while maintaining a strict volume ratio between the two boxes.

The company defines a valid split as:

```text
sum(BoxA) : sum(BoxB) = P : Q
```

where:

* `P`
* `Q`

are given positive integers.

Your task is to determine whether it is possible to split the bottles into two non-empty groups satisfying the required ratio.

If multiple valid partitions exist, return the partition with:

```text
Minimum absolute difference in number of bottles between the two boxes
```

If no valid partition exists, return:

```text
IMPOSSIBLE
```

---

# Business Requirement

Given:

* an array representing bottle volumes
* two integers `P` and `Q`

split all bottles into exactly two non-empty boxes such that:

```text
sum(BoxA) / sum(BoxB) = P / Q
```

Every bottle must belong to exactly one box.

Both boxes must contain at least one bottle.

---

# Important Mathematical Observation

Let:

```text
totalSum = sum(all bottles)
```

If a valid partition exists, then:

```text
sum(BoxA) = (P × totalSum) / (P + Q)
sum(BoxB) = (Q × totalSum) / (P + Q)
```

Thus:

* required sums become fixed
* subset selection becomes the core problem

---

# Task

Determine whether a valid partition exists.

If multiple partitions are possible:

```text
choose the partition minimizing:
|size(BoxA) - size(BoxB)|
```

---

# Input Format

First line contains integer:

```text
N
```

representing number of bottles.

Second line contains:

```text
N space-separated integers
```

representing bottle volumes.

Third line contains:

```text
P Q
```

representing required ratio.

---

# Output Format

If partition is possible, print:

```text
POSSIBLE
```

Then print:

```text
countA elements_of_BoxA
```

Then print:

```text
countB elements_of_BoxB
```

If partition is impossible, print:

```text
IMPOSSIBLE
```

---

# Constraints

* **1 ≤ N ≤ 40**
* **1 ≤ bottleVolume ≤ 10⁹**
* **1 ≤ P, Q ≤ 10⁹**

---

# Sample Input 1

```text
5
1 2 3 4 5
2 1
```

---

# Sample Output 1

```text
POSSIBLE
3 2 3 5
2 1 4
```

---

# Explanation

Total sum:

```text
1 + 2 + 3 + 4 + 5 = 15
```

Required ratio:

```text
2 : 1
```

Therefore:

```text
sum(BoxA) = (2 × 15) / 3 = 10
sum(BoxB) = 5
```

Valid partition:

```text
BoxA = {2, 3, 5} → sum = 10
BoxB = {1, 4} → sum = 5
```

Ratio:

```text
10 : 5 = 2 : 1
```

---

# Sample Input 2

```text
4
3 7 11 19
1 1
```

---

# Sample Output 2

```text
IMPOSSIBLE
```

---

# Explanation

Total sum:

```text
40
```

Required partition sums:

```text
20 and 20
```

No subset produces sum:

```text
20
```

Hence partition is impossible.

---

# Sample Input 3

```text
6
2 4 6 8 10 20
3 2
```

---

# Sample Output 3

```text
POSSIBLE
2 20 10
4 2 4 6 8
```

---

# Explanation

Total sum:

```text
50
```

Required partition sums:

```text
sum(BoxA) = (3 × 50) / 5 = 30
sum(BoxB) = (2 × 50) / 5 = 20
```

Valid partition:

```text
BoxA = {20, 10} → 30
BoxB = {2, 4, 6, 8} → 20
```

Ratio:

```text
30 : 20 = 3 : 2
```

---

# Recommended Approach

Efficient interview solution uses:

```text
Meet-in-the-Middle
```

because:

* `N ≤ 40`
* brute force `O(2^N)` becomes infeasible

---

# Optimal Strategy

## Step 1

Compute:

```text
target = (P × totalSum) / (P + Q)
```

If target is not an integer:

```text
IMPOSSIBLE
```

---

## Step 2

Split array into two halves.

Generate all subset sums for both halves.

---

## Step 3

Use hashing or binary search to find:

```text
leftSum + rightSum = target
```

---

## Step 4

Reconstruct subsets and minimize:

```text
|size(BoxA) - size(BoxB)|
```

---

# Expected Complexity

## Meet-in-the-Middle Approach

### Time Complexity

```text
O(2^(N/2) × N)
```

because:

* all subset sums are generated
* subset sums are sorted/searched efficiently
* reconstruction requires subset tracking

---

### Space Complexity

```text
O(2^(N/2))
```

for storing subset sums.

---

# Alternative Approaches

| Approach           | Time Complexity | Space Complexity |
| ------------------ | --------------- | ---------------- |
| Brute Force        | O(2^N)          | O(1)             |
| DP by Sum          | O(N × Sum)      | O(Sum)           |
| Meet-in-the-Middle | O(2^(N/2) × N)  | O(2^(N/2))       |

---

# Edge Cases

Your solution should correctly handle:

* impossible ratios
* non-divisible target sums
* duplicate bottle volumes
* all equal bottles
* very large values
* multiple optimal partitions
* minimum bottle count
* skewed ratios like `1000 : 1`
* partitions where one box may accidentally become empty

---

# Object-Oriented Design Expectations

Recommended classes:

| Class                | Responsibility                 |
| -------------------- | ------------------------------ |
| `BottleDistributor`  | Core partition logic           |
| `SubsetGenerator`    | Generates subset sums          |
| `PartitionValidator` | Validates ratio constraints    |
| `SolutionBuilder`    | Reconstructs optimal partition |

---

# Follow-Up Interview Questions

Interviewers may ask:

* Can this be solved for `N = 10^5`?
* How would you minimize memory usage?
* Can multiple ratios be processed efficiently?
* How would you parallelize subset generation?
* Can this be generalized to `K` boxes?

---

# Execution Time Limit

```text
3 seconds
```

```
```