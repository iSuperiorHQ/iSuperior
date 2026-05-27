# **Problem 24: Split Bottles Between Two Boxes Maintaining Ratio**

**Company:** Amazon

**Category:** Arrays / Greedy / Hashing / Meet-in-the-Middle

**Difficulty:** Hard

---

# **Problem Description**

You are given `n` bottles arranged in a line.

Each bottle contains some amount of liquid represented by an integer array:

```text
bottles[i]
```

Initially:

```text
All bottles belong to Box A
```

and:

```text
Box B is empty
```

You may transfer bottles from Box A to Box B.

A transfer operation consists of moving exactly one bottle from Box A to Box B.

After all transfers:

```text
sumA = total liquid in Box A
sumB = total liquid in Box B
```

The final arrangement is considered valid if:

```text
sumA : sumB = P : Q
```

Your task is to determine the minimum number of bottle transfers required to achieve the required ratio.

If it is impossible, return:

```text
-1
```

---

# **Business Requirement**

A beverage logistics company must distribute liquid containers between two storage chambers while maintaining a fixed capacity ratio for pressure balancing.

To minimize operational effort, the company wants the minimum number of bottle movements.

---

# **Task**

Find the minimum number of bottle transfers required such that:

```text
sumA : sumB = P : Q
```

---

# **Function Signature**

```cpp
int minimumTransfers(vector<int>& bottles, int P, int Q)
```

---

# **Input Format**

First line contains integer:

```text
n
```

representing number of bottles.

Second line contains `n` space-separated integers:

```text
bottles[i]
```

representing liquid amount in each bottle.

Third line contains two integers:

```text
P Q
```

representing required ratio.

---

# **Output Format**

Print a single integer representing minimum transfers required.

If valid distribution is impossible, print:

```text
-1
```

---

# **Constraints**

* **1 ≤ n ≤ 30**
* **1 ≤ bottles[i] ≤ 10⁹**
* **1 ≤ P, Q ≤ 10⁹**

---

# **Sample Input 1**

```text
5
1 2 3 4 5
2 1
```

---

# **Sample Output 1**

```text
1
```

---

# **Explanation**

Total liquid:

```text
1 + 2 + 3 + 4 + 5 = 15
```

Required ratio:

```text
2 : 1
```

Thus:

```text
sumA = 10
sumB = 5
```

Move bottle:

```text
5
```

to Box B.

Transfers required:

```text
1
```

---

# **Sample Input 2**

```text
4
2 2 2 2
3 1
```

---

# **Sample Output 2**

```text
1
```

---

# **Explanation**

Total liquid:

```text
8
```

Required split:

```text
6 : 2
```

Move one bottle containing:

```text
2
```

to Box B.

Minimum transfers:

```text
1
```

---

# **Sample Input 3**

```text
3
1 2 5
1 1
```

---

# **Sample Output 3**

```text
-1
```

---

# **Explanation**

Total liquid:

```text
8
```

Required ratio:

```text
1 : 1
```

Thus both boxes must contain:

```text
4
```

No subset of bottles sums to:

```text
4
```

Hence answer is:

```text
-1
```

---

# **Key Observation**

Let:

```text
total = sum of all bottles
```

For valid ratio:

```text
sumA : sumB = P : Q
```

we must satisfy:

```text
sumA = total × P / (P + Q)
sumB = total × Q / (P + Q)
```

Thus:

1. Total sum must be divisible by:

```text
P + Q
```

2. We only need to find subset having sum:

```text
target = total × Q / (P + Q)
```

because transferred bottles form Box B.

3. Among all valid subsets, minimize number of selected bottles.

---

# **Approaches**

| Approach | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| Brute Force Subset Enumeration | O(2ⁿ) | O(1) |
| Backtracking with Pruning | O(2ⁿ) | O(n) |
| Meet-in-the-Middle | O(2ⁿᐟ²) | O(2ⁿᐟ²) |

---

# **Recommended Interview Approach**

Preferred interview solution:

```text
Meet-in-the-Middle
```

because constraints make classical subset-sum DP infeasible.

---

# **Efficient Strategy**

1. Compute total sum.
2. Verify divisibility condition.
3. Compute required target sum for Box B.
4. Split array into two halves.
5. Generate all subset sums for both halves.
6. Use hashing or binary search to combine subsets reaching target.
7. Track minimum number of selected bottles.

---

# **Example Walkthrough**

Input:

```text
1 2 3 4 5
P = 2
Q = 1
```

Total:

```text
15
```

Required Box B sum:

```text
15 × 1 / (2 + 1)
= 5
```

Possible subsets:

```text
{5}
{2,3}
{1,4}
```

Minimum transfers:

```text
1
```

using subset:

```text
{5}
```

---

# **Expected Complexity**

## Meet-in-the-Middle Approach

### Time Complexity

* **O(2ⁿᐟ²)**

because all subset sums of both halves are generated.

---

### Space Complexity

* **O(2ⁿᐟ²)**

for storing subset sums.

---

# **Edge Cases**

Your solution should correctly handle:

* impossible ratios
* large bottle values
* duplicate bottle sizes
* all bottles identical
* already balanced configurations
* minimum input size
* very large sums

---

# **Follow-Up Questions**

Interviewers may ask:

* Can this be solved using bitmask DP?
* How would you optimize memory usage?
* What if bottles could be split?
* How would you solve this for streaming data?
* Can you support multiple ratio queries efficiently?

---

# **Execution Time Limit**

```text
2 seconds
```