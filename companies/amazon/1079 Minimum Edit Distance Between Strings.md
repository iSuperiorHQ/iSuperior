# **Problem 1079: Minimum Edit Distance Between Strings**

**Company:** Amazon

**Topic:** Dynamic Programming (2D)

---

## **Problem Description**

An enterprise document synchronization system compares two text strings to determine how many modifications are required to transform one document into another.

The system supports only the following operations:

1. **Insert** a character
2. **Delete** a character
3. **Replace** a character

Each operation costs exactly:

```text id="m2v8zk"
1 operation
```

Given two strings:

```text id="x7m1qa"
A and B
```

your task is to compute the minimum number of operations required to convert string `A` into string `B`.

This problem is commonly used in:

* Spell checkers
* DNA sequence comparison
* Version control systems
* Search recommendation engines

---

## **Task**

Return the minimum number of insertions, deletions, and replacements required to transform string `A` into string `B`.

---

## **Allowed Operations**

### Insert

Add a character into string `A`

Example:

```text id="u3m8qp"
cat → cart
```

---

### Delete

Remove a character from string `A`

Example:

```text id="f9m1zk"
plane → plan
```

---

### Replace

Replace one character with another

Example:

```text id="r2m8vx"
bat → bot
```

---

## **Input Format**

* First line: string **A**
* Second line: string **B**

---

## **Constraints**

* **1 ≤ |A|, |B| ≤ 5000**
* Strings contain lowercase English letters

---

## **Output Format**

Print a single integer — the minimum edit distance between the two strings.

---

## **Sample Input 1**

```text id="n7m2qa"
horse
ros
```

---

## **Sample Output 1**

```text id="p4m9xp"
3
```

---

## **Explanation**

One optimal transformation:

```text id="v1m8zk"
horse
→ rorse   (replace 'h' with 'r')
→ rose    (delete 'r')
→ ros     (delete 'e')
```

Total operations:

```text id="g8m2vx"
3
```

---

## **Sample Input 2**

```text id="x2m1qa"
intention
execution
```

---

## **Sample Output 2**

```text id="m9v2zk"
5
```

---

## **Explanation**

One valid optimal transformation:

```text id="k4m8qp"
intention
→ entention   (replace 'i' with 'e')
→ extention   (replace 'n' with 'x')
→ exention    (delete 't')
→ exection    (replace 'n' with 'c')
→ execution   (insert 'u')
```

Total operations:

```text id="u7m1xp"
5
```

---

## **Sample Input 3**

```text id="m4k8qa"
abc
abc
```

---

## **Sample Output 3**

```text id="v8m2zk"
0
```

---

## **Explanation**

Both strings are already identical.

No operations are required.

---

## **Sample Input 4**

```text id="x1m9vx"
abcd
wxyz
```

---

## **Sample Output 4**

```text id="z7m2qp"
4
```

---

## **Explanation**

Every character must be replaced:

```text id="u4m8zk"
a → w
b → x
c → y
d → z
```

Total operations:

```text id="k2m1qa"
4
```

---

## **Dynamic Programming Insight**

Define:

```text id="r7m2zk"
dp[i][j]
```

where:

> `dp[i][j]` represents the minimum operations required to convert:

```text id="u1m8xp"
A[0...i-1] → B[0...j-1]
```

---

## **Transition Rules**

If characters match:

```text id="m4k8qa"
dp[i][j] = dp[i-1][j-1]
```

Otherwise:

```text id="v8m2zk"
dp[i][j] =
1 + min(
    insert,
    delete,
    replace
)
```

---

## **Base Conditions**

```text id="x1m9vx"
dp[0][j] = j
dp[i][0] = i
```

because converting:

* Empty string → non-empty string requires insertions
* Non-empty string → empty string requires deletions

---

## **Expected Complexity**

### Standard 2D Dynamic Programming

* **Time Complexity:** `O(|A| × |B|)`
* **Space Complexity:** `O(|A| × |B|)`

---

## **Optimization**

Space can be optimized using rolling arrays:

* Optimized Space Complexity: `O(min(|A|, |B|))`

---

## **Execution Time Limit**

**10 seconds**