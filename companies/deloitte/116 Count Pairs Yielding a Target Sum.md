# **Problem 116: Count Pairs Yielding a Target Sum**

**Company:** Deloitte

**Category:** Arrays / Hash Map

**Difficulty:** Medium

---

# **Problem Description**

A financial analytics engine processes streams of transaction values to identify pairs of entries whose combined value matches a predefined target amount.

Given an array of integers and a target value, your task is to determine the total number of:

```text id="m2v8zk"
distinct index pairs
```

whose sum equals the target.

A brute-force approach that checks every possible pair becomes computationally expensive for large datasets.

Interviewers expect candidates to optimize the solution using:

* hashing
* frequency tracking
* complement lookup techniques

This problem evaluates understanding of:

* hash map optimization
* time-memory trade-offs
* frequency counting
* efficient pair discovery

---

# **Task**

Given:

* an integer array:

```text id="x7m1qa"
nums
```

* an integer:

```text id="u3m8qp"
target
```

return the total number of distinct index pairs:

```text id="f9m1zk"
(i, j)
```

such that:

```text id="r2m8vx"
i < j
```

and:

```text id="n7m2qa"
nums[i] + nums[j] = target
```

---

# **Important Rules**

* Each pair is identified using distinct indices
* Duplicate values may exist
* Negative integers are allowed
* Multiple pairs involving the same value are valid if indices differ
* Order of pair selection does NOT matter:

```text id="p4m9xp"
(i, j) and (j, i)
```

represent the same pair.

---

# **Input Format**

First line contains integer:

```text id="v1m8zk"
N
```

representing size of array.

Second line contains:

```text id="g8m2vx"
N space-separated integers
```

representing array elements.

Third line contains integer:

```text id="x2m1qa"
target
```

representing required pair sum.

---

# **Output Format**

Print a single integer representing:

```text id="m9v2zk"
total number of valid index pairs
```

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* **-10⁹ ≤ nums[i] ≤ 10⁹**
* **-10⁹ ≤ target ≤ 10⁹**

---

# **Sample Input 1**

```text id="k4m8qp"
6
1 5 7 -1 5 3
6
```

---

# **Sample Output 1**

```text id="u7m1xp"
3
```

---

# **Explanation**

Valid index pairs:

| Pair  | Values | Sum |
| ----- | ------ | --- |
| (0,1) | (1,5)  | 6   |
| (2,3) | (7,-1) | 6   |
| (0,4) | (1,5)  | 6   |

Total valid pairs:

```text id="m4k8qa"
3
```

---

# **Sample Input 2**

```text id="v8m2zk"
5
1 1 1 1 1
2
```

---

# **Sample Output 2**

```text id="x1m9vx"
10
```

---

# **Explanation**

Every pair of distinct indices forms a valid pair.

Total index pairs:

```text id="z7m2qp"
5C2 = 10
```

---

# **Sample Input 3**

```text id="u4m8zk"
7
2 4 3 5 7 8 9
10
```

---

# **Sample Output 3**

```text id="k2m1qa"
2
```

---

# **Explanation**

Valid pairs:

```text id="r7m2zk"
(2,8)
(3,7)
```

---

# **Sample Input 4**

```text id="u1m8xp"
4
10 20 30 40
100
```

---

# **Sample Output 4**

```text id="m4k8qa"
0
```

---

# **Explanation**

No pair sums to:

```text id="v8m2zk"
100
```

---

# **Naive Brute Force Approach**

A straightforward solution may:

1. Iterate over every pair of indices
2. Compute pair sum
3. Count valid matches

This requires:

```text id="x1m9vx"
O(N²)
```

time complexity.

Too slow for very large datasets.

---

# **Optimized Hash Map Strategy**

For every element:

```text id="z7m2qp"
x
```

compute required complement:

```text id="u4m8zk"
target - x
```

If the complement has already appeared earlier in the array:

* all occurrences of the complement form valid pairs with current element

Use a hash map to store frequencies of previously processed values.

---

# **Efficient Algorithm**

Maintain:

| Structure                   | Purpose                     |
| --------------------------- | --------------------------- |
| `HashMap<Integer, Integer>` | Frequency of visited values |
| `pairCount`                 | Total valid pairs           |

---

## Step 1 — Traverse Array

For current value:

```text id="k2m1qa"
x
```

compute:

```text id="r7m2zk"
complement = target - x
```

---

## Step 2 — Check Complement Frequency

If complement exists in hash map:

* increment answer by:

```text id="u1m8xp"
frequency[complement]
```

because every previous occurrence forms a valid pair.

---

## Step 3 — Update Frequency Map

Insert/update current value frequency.

---

# **Why This Works**

Every valid pair is counted exactly once:

* when processing the second element of the pair

Using frequency tracking eliminates redundant pair scanning.

---

# **Handling Duplicate Values**

Example:

```text id="m4k8qa"
[1,1,1,1]
target = 2
```

Processing:

| Current Element | Existing 1s | New Pairs |
| --------------- | ----------- | --------- |
| 1               | 0           | 0         |
| 1               | 1           | 1         |
| 1               | 2           | 2         |
| 1               | 3           | 3         |

Total:

```text id="v8m2zk"
1 + 2 + 3 = 6
```

which equals:

```text id="x1m9vx"
4C2
```

---

# **Recommended Data Structures**

| Structure           | Purpose          |
| ------------------- | ---------------- |
| `Hash Map`          | Frequency lookup |
| `Integer Variables` | Pair counting    |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* duplicate values
* negative numbers
* zero target values
* empty valid pair sets
* large arrays
* repeated complements
* identical element pairing

---

# **Expected Complexity**

## Optimized Hash Map Solution

### Time Complexity

* **O(N)** average-case

assuming constant-time hash map operations.

Each element is processed exactly once.

---

### Space Complexity

* **O(N)**

for storing element frequencies in the hash map.

---

# **Example Walkthrough**

Input:

```text id="z7m2qp"
nums = [1,5,7,-1,5]
target = 6
```

---

## Traversal

| Current | Complement | Existing Complement Count | Total Pairs |
| ------- | ---------- | ------------------------- | ----------- |
| 1       | 5          | 0                         | 0           |
| 5       | 1          | 1                         | 1           |
| 7       | -1         | 0                         | 1           |
| -1      | 7          | 1                         | 2           |
| 5       | 1          | 1                         | 3           |

Final answer:

```text id="u4m8zk"
3
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Sorting + Two Pointers
* Frequency array optimization
* Pair enumeration variants
* Online streaming pair counting

---

# **Follow-Up Variants**

Interviewers may ask:

* Return actual index pairs
* Count unique value pairs only
* Three-sum / four-sum extensions
* Dynamic insert/delete queries
* Pair sums within a range

---

# **Execution Time Limit**

**4 seconds**