# **Problem 1081: Longest Palindromic Substring Detection**

**Company:** Amazon

**Topic:** Strings / Dynamic Programming

---

## **Problem Description**

A cybersecurity analytics engine scans encrypted communication logs to identify symmetric data signatures.

A symmetric signature is defined as a substring that reads the same:

* From left to right
* From right to left

Such substrings are called:

```text id="m2v8zk"
Palindromes
```

Given a string containing lowercase English characters, your task is to identify the longest contiguous palindromic substring present in the string.

If multiple palindromic substrings have the same maximum length, return the one that appears first in the string.

---

## **Task**

Find and print the longest palindromic substring of the given string.

---

## **Important Notes**

* A substring must contain contiguous characters only
* Single characters are also valid palindromes
* Matching is case-sensitive

---

## **Input Format**

* First line: string **S**

---

## **Constraints**

* **1 ≤ |S| ≤ 5000**
* String contains lowercase English letters

---

## **Output Format**

Print the longest palindromic substring.

---

## **Sample Input 1**

```text id="x7m1qa"
babad
```

---

## **Sample Output 1**

```text id="u3m8qp"
bab
```

---

## **Explanation**

Possible palindromic substrings:

```text id="f9m1zk"
bab
aba
```

Both have length `3`.

Since `"bab"` appears first, it is returned.

---

## **Sample Input 2**

```text id="r2m8vx"
cbbd
```

---

## **Sample Output 2**

```text id="n7m2qa"
bb
```

---

## **Explanation**

Longest symmetric substring:

```text id="p4m9xp"
bb
```

Length:

```text id="v1m8zk"
2
```

---

## **Sample Input 3**

```text id="g8m2vx"
forgeeksskeegfor
```

---

## **Sample Output 3**

```text id="x2m1qa"
geeksskeeg
```

---

## **Explanation**

The substring:

```text id="m9v2zk"
geeksskeeg
```

reads the same in both directions.

Length:

```text id="k4m8qp"
10
```

---

## **Sample Input 4**

```text id="u7m1xp"
abcd
```

---

## **Sample Output 4**

```text id="m4k8qa"
a
```

---

## **Explanation**

No palindrome longer than length `1` exists.

Hence the first character is returned.

---

## **Dynamic Programming Insight**

Define:

```text id="v8m2zk"
dp[i][j]
```

where:

> `dp[i][j] = true`

if substring:

```text id="x1m9vx"
S[i...j]
```

is a palindrome.

---

## **Transition Rules**

A substring is palindromic if:

```text id="z7m2qp"
S[i] == S[j]
```

and:

* Inner substring is also palindrome
* Or substring length ≤ 2

Transition:

```text id="u4m8zk"
dp[i][j] =
(S[i] == S[j]) AND
(dp[i+1][j-1] OR length <= 2)
```

---

## **Base Cases**

* Every single character is a palindrome
* Two equal adjacent characters form a palindrome of length `2`

---

## **Optimized Alternatives**

Besides Dynamic Programming, the problem can also be solved using:

* Expand Around Center → `O(N²)` time, `O(1)` space
* Manacher’s Algorithm → `O(N)` time

---

## **Expected Complexity**

### Standard DP Solution

* **Time Complexity:** `O(N²)`
* **Space Complexity:** `O(N²)`

---

## **Execution Time Limit**

**10 seconds**