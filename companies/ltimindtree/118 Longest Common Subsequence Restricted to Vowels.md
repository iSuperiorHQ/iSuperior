# **Problem 118: Longest Common Subsequence Restricted to Vowels**

**Company:** LTIMindtree

**Category:** Dynamic Programming / Strings

**Difficulty:** Hard

---

# **Problem Description**

A linguistic analytics system compares two textual sequences to identify common phonetic patterns.

Unlike the classical:

```text id="m2v8zk"
Longest Common Subsequence (LCS)
```

problem, the system only considers:

```text id="x7m1qa"
vowel characters
```

as valid contributors to the subsequence.

Given two strings, your task is to determine the length of the:

```text id="u3m8qp"
longest common subsequence consisting only of vowels
```

The valid vowels are:

```text id="f9m1zk"
a, e, i, o, u
```

This problem evaluates a candidate’s understanding of:

* dynamic programming
* state transitions
* subsequence constraints
* matrix optimization
* conditional DP updates

Interviewers expect candidates to adapt the standard LCS recurrence relation to include an additional validity constraint.

---

# **Task**

Given two lowercase English strings:

```text id="r2m8vx"
s1
```

and:

```text id="n7m2qa"
s2
```

return the length of the longest common subsequence formed exclusively using vowel characters.

---

# **Important Rules**

* A subsequence does NOT require contiguous characters
* Character order must remain preserved
* Only vowels contribute to the subsequence length
* Consonants may appear in the strings but cannot be included in the final subsequence
* Valid vowels are:

```text id="p4m9xp"
a, e, i, o, u
```

* Strings contain lowercase English letters only

---

# **Input Format**

First line contains string:

```text id="v1m8zk"
s1
```

Second line contains string:

```text id="g8m2vx"
s2
```

---

# **Output Format**

Print a single integer representing:

```text id="x2m1qa"
length of the longest vowel-only common subsequence
```

---

# **Constraints**

* **1 ≤ |s1| ≤ 2000**
* **1 ≤ |s2| ≤ 2000**
* Strings contain lowercase English alphabet characters only

---

# **Sample Input 1**

```text id="m9v2zk"
education
dedication
```

---

# **Sample Output 1**

```text id="k4m8qp"
4
```

---

# **Explanation**

Vowels in:

```text id="u7m1xp"
education
```

are:

```text id="m4k8qa"
e u a i o
```

Vowels in:

```text id="v8m2zk"
dedication
```

are:

```text id="x1m9vx"
e i a i o
```

Longest valid vowel-only common subsequence:

```text id="z7m2qp"
e a i o
```

Length:

```text id="u4m8zk"
4
```

---

# **Sample Input 2**

```text id="k2m1qa"
aeiou
aeiou
```

---

# **Sample Output 2**

```text id="r7m2zk"
5
```

---

# **Explanation**

Entire string forms the valid vowel-only subsequence.

---

# **Sample Input 3**

```text id="u1m8xp"
programming
dynamic
```

---

# **Sample Output 3**

```text id="m4k8qa"
1
```

---

# **Explanation**

Common vowel:

```text id="v8m2zk"
a
```

Maximum valid subsequence length:

```text id="x1m9vx"
1
```

---

# **Sample Input 4**

```text id="z7m2qp"
bcdfg
hjklm
```

---

# **Sample Output 4**

```text id="u4m8zk"
0
```

---

# **Explanation**

No vowels exist in common.

Thus no valid vowel-only subsequence exists.

---

# **Why Brute Force Fails**

Generating all subsequences of two strings requires exponential complexity:

```text id="k2m1qa"
O(2^M × 2^N)
```

which is computationally infeasible for large inputs.

Interviewers expect dynamic programming optimization.

---

# **Classical LCS Insight**

Standard LCS uses:

```text id="r7m2zk"
DP[i][j]
```

to represent:

```text id="u1m8xp"
LCS length between first i characters of s1
and first j characters of s2
```

This problem introduces an additional restriction:

```text id="m4k8qa"
only vowels may contribute
```

to the subsequence length.

---

# **Optimized Dynamic Programming Strategy**

Construct DP matrix:

```text id="v8m2zk"
DP[M+1][N+1]
```

where:

* `M = length of s1`
* `N = length of s2`

---

# **Vowel Validation Function**

Use helper function:

```text id="x1m9vx"
isVowel(c)
```

which returns true if:

```text id="z7m2qp"
c ∈ {a,e,i,o,u}
```

---

# **DP Transition Rules**

---

## Case 1 — Characters Match AND Are Vowels

If:

```text id="u4m8zk"
s1[i-1] == s2[j-1]
```

AND the character is a vowel:

```text id="k2m1qa"
DP[i][j] = DP[i-1][j-1] + 1
```

---

## Case 2 — Otherwise

If the characters differ, or the matching character is a consonant:

```text id="r7m2zk"
DP[i][j] =
max(DP[i-1][j], DP[i][j-1])
```

Matching consonants are ignored because consonants cannot contribute to the valid subsequence.

---

# **Why This Works**

The DP matrix explores all valid subsequence possibilities while:

* preserving character order
* enforcing vowel-only inclusion
* avoiding repeated computation

This guarantees an optimal solution.

---

# **Recommended Data Structures**

| Structure         | Purpose                  |
| ----------------- | ------------------------ |
| `2D DP Array`     | Store subproblem results |
| `Helper Function` | Validate vowels          |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* strings without vowels
* repeated vowels
* completely identical strings
* empty valid subsequences
* long strings with sparse vowels
* strings containing only consonants

---

# **Expected Complexity**

## Optimized DP Solution

### Time Complexity

* **O(M × N)**

Every DP state is computed exactly once.

---

### Space Complexity

* **O(M × N)**

for maintaining the DP matrix.

---

# **Example Walkthrough**

Input:

```text id="u1m8xp"
s1 = "education"
s2 = "dedication"
```

---

## Relevant Vowels

| String     | Vowels    |
| ---------- | --------- |
| education  | e u a i o |
| dedication | e i a i o |

---

## DP Matching

Valid common vowel subsequence:

```text id="m4k8qa"
e a i o
```

Length:

```text id="v8m2zk"
4
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Space-optimized LCS
* Recursive memoization
* Bitset optimization
* Generic constrained subsequence problems

---

# **Follow-Up Variants**

Interviewers may ask:

* Return actual subsequence
* Restrict to consonants instead
* Weighted character matching
* Longest palindromic vowel subsequence
* Streaming string comparison

---

# **Execution Time Limit**

**5 seconds**