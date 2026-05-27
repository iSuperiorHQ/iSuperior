# **Problem 23: Maximum Mathematical Distance Between Good Triplets**

**Company:** Google

**Category:** Arrays / Greedy / Prefix-Suffix Optimization

**Difficulty:** Hard

---

# **Problem Description**

You are given an integer array `nums` of size `n`.

A triplet `(i, j, k)` is called a **good triplet** if:

```text
0 ≤ i < j < k < n
```

and:

```text
nums[i] < nums[j] < nums[k]
```

For every good triplet, define its mathematical distance as:

```text
|nums[i] - nums[j]| + |nums[j] - nums[k]| + |nums[i] - nums[k]|
```

Your task is to find the maximum possible mathematical distance among all good triplets.

If no valid good triplet exists, return:

```text
-1
```

---

# **Business Requirement**

A financial analytics system tracks increasing profit milestones across multiple stages of growth.

The system wants to identify three strictly increasing milestones having maximum overall separation between values for volatility analysis.

---

# **Task**

Find the maximum mathematical distance among all valid good triplets.

---

# **Function Signature**

```cpp
long long maximumTripletDistance(vector<int>& nums)
```

---

# **Input Format**

First line contains integer:

```text
n
```

representing size of array.

Second line contains `n` space-separated integers:

```text
nums[i]
```

representing array elements.

---

# **Output Format**

Print a single integer representing the maximum mathematical distance among all good triplets.

If no valid triplet exists, print:

```text
-1
```

---

# **Constraints**

* **3 ≤ n ≤ 2 × 10⁵**
* **-10⁹ ≤ nums[i] ≤ 10⁹**

---

# **Sample Input 1**

```text
6
1 3 5 2 7 9
```

---

# **Sample Output 1**

```text
16
```

---

# **Explanation**

One optimal good triplet is:

```text
(1, 5, 9)
```

Distance becomes:

```text
|1 - 5| + |5 - 9| + |1 - 9|
= 4 + 4 + 8
= 16
```

No other valid triplet produces larger distance.

---

# **Sample Input 2**

```text
5
9 8 7 6 5
```

---

# **Sample Output 2**

```text
-1
```

---

# **Explanation**

No strictly increasing triplet exists.

Hence answer is:

```text
-1
```

---

# **Sample Input 3**

```text
7
2 1 4 6 3 8 10
```

---

# **Sample Output 3**

```text
18
```

---

# **Explanation**

One optimal good triplet is:

```text
(1, 4, 10)
```

Distance becomes:

```text
|1 - 4| + |4 - 10| + |1 - 10|
= 3 + 6 + 9
= 18
```

---

# **Key Observation**

For every strictly increasing triplet:

```text
nums[i] < nums[j] < nums[k]
```

the mathematical expression:

```text
|a-b| + |b-c| + |a-c|
```

simplifies to:

```text
2 × (nums[k] - nums[i])
```

because:

```text
|a-b| = b-a
|b-c| = c-b
|a-c| = c-a
```

Thus:

```text
(b-a) + (c-b) + (c-a)
= 2(c-a)
```

Therefore the problem reduces to:

```text
Find increasing triplet maximizing:
nums[k] - nums[i]
```

while ensuring there exists some middle element:

```text
nums[i] < nums[j] < nums[k]
```

with:

```text
i < j < k
```

---

# **Approaches**

| Approach | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| Brute Force Triplets | O(n³) | O(1) |
| Fixed Middle Expansion | O(n²) | O(1) |
| Prefix Minimum + Suffix Maximum | O(n) | O(n) |

---

# **Recommended Interview Approach**

Preferred interview solution:

```text
Prefix Minimum + Suffix Maximum
```

because it validates triplets efficiently in linear time.

---

# **Efficient Strategy**

For every index `j`:

1. Maintain smallest value on left side:

```text
leftMin[j]
```

2. Maintain largest value on right side:

```text
rightMax[j]
```

3. If:

```text
leftMin[j] < nums[j] < rightMax[j]
```

then valid triplet exists.

4. Compute:

```text
2 × (rightMax[j] - leftMin[j])
```

5. Return maximum value across all valid indices.

---

# **Example Walkthrough**

Input:

```text
1 3 5 2 7 9
```

For middle element:

```text
5
```

Best left value:

```text
1
```

Best right value:

```text
9
```

Distance:

```text
2 × (9 - 1)
= 16
```

---

# **Expected Complexity**

## Prefix-Suffix Optimization

### Time Complexity

* **O(n)**

because the array is traversed constant number of times.

---

### Space Complexity

* **O(n)**

for storing prefix minimum and suffix maximum arrays.

---

# **Edge Cases**

Your solution should correctly handle:

* no increasing triplet
* duplicate values
* negative numbers
* strictly increasing arrays
* strictly decreasing arrays
* multiple optimal triplets
* very large values

---

# **Follow-Up Questions**

Interviewers may ask:

* Can you optimize space complexity?
* Can this be solved in streaming fashion?
* What changes if duplicates are allowed?
* Can you generalize this for subsequences of length `k`?
* How would you solve this for distributed datasets?

---

# **Execution Time Limit**

```text
2 seconds
```