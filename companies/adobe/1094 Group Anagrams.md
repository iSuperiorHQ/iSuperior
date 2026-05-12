# **Problem 1094: Group Anagrams**

**Company:** Adobe

**Topic:** Hash Table / Sorting

**Difficulty:** Medium

---

## **Problem Description**

A document indexing platform stores millions of keywords for semantic similarity analysis.

Two words are considered:

```text id="m2v8zk"
Anagrams
```

if they contain:

* exactly the same characters
* with exactly the same frequencies
* but possibly in different orders

Examples:

```text id="x7m1qa"
listen ↔ silent
evil ↔ vile
```

belong to the same anagram group.

The platform must efficiently cluster all related strings together for faster lookup and duplicate pattern detection.

Your task is to group all strings that belong to the same anagram family.

---

## **Task**

Given an array of lowercase strings, group all anagrams together.

Strings inside each group must be printed in lexicographical order.

Groups themselves should be printed ordered by the lexicographically smallest string inside each group.

---

## **Anagram Rules**

Two strings are anagrams if:

* both strings contain identical character frequencies
* string lengths are equal

Examples:

```text id="u3m8qp"
eat ↔ tea ↔ ate
```

because all contain:

```text id="f9m1zk"
a, e, t
```

exactly once.

---

## **Input Format**

* First line: integer **N** — number of strings
* Next `N` lines: one lowercase string per line

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **1 ≤ length of each string ≤ 100**
* Total combined characters ≤ `10⁶`

---

## **Output Format**

Print grouped anagrams.

Each group should appear on a separate line.

Strings inside each group must be:

* space-separated
* lexicographically sorted

---

## **Sample Input 1**

```text id="r2m8vx"
6
eat
tea
tan
ate
nat
bat
```

---

## **Sample Output 1**

```text id="n7m2qa"
ate eat tea
bat
nat tan
```

---

## **Explanation**

Group 1:

```text id="p4m9xp"
eat
tea
ate
```

share identical frequency mapping.

Group 2:

```text id="v1m8zk"
tan
nat
```

are anagrams.

Group 3:

```text id="g8m2vx"
bat
```

has no matching pair.

---

## **Sample Input 2**

```text id="x2m1qa"
5
listen
silent
enlist
google
gogole
```

---

## **Sample Output 2**

```text id="m9v2zk"
enlist listen silent
gogole google
```

---

## **Explanation**

Strings:

```text id="k4m8qp"
listen
silent
enlist
```

contain identical character counts.

Similarly:

```text id="u7m1xp"
google
gogole
```

belong together.

---

## **Sample Input 3**

```text id="m4k8qa"
4
abc
def
ghi
cab
```

---

## **Sample Output 3**

```text id="v8m2zk"
abc cab
def
ghi
```

---

## **Explanation**

Only:

```text id="x1m9vx"
abc
cab
```

form an anagram group.

---

## **Sample Input 4**

```text id="z7m2qp"
5
a
b
ab
ba
aa
```

---

## **Sample Output 4**

```text id="u4m8zk"
a
aa
ab ba
b
```

---

## **Explanation**

Single-character strings:

```text id="k2m1qa"
a
b
```

are not anagrams because frequencies differ.

Strings:

```text id="r7m2zk"
ab
ba
```

belong to the same group.

---

## **Hashing Insight**

All anagrams produce the same canonical representation.

Two common approaches:

### Sorting-Based Key

```text id="u1m8xp"
eat → aet
tea → aet
ate → aet
```

Use sorted string as hash key.

---

### Frequency Mapping Key

Build:

```text id="m4k8qa"
[26]
```

character frequency signature.

Strings with identical signatures belong to the same group.

---

## **Efficient Strategy**

For every string:

1. Generate canonical key
2. Insert into corresponding hash bucket
3. Sort each bucket lexicographically
4. Sort groups using smallest string in each group

---

## **Expected Complexity**

### Sorting-Based Approach

* **Time Complexity:** `O(N × K log K)`
* **Space Complexity:** `O(N × K)`

Where:

* `N` = number of strings
* `K` = average string length

---

## **Frequency Hash Optimization**

Using fixed-size frequency arrays:

* **Time Complexity:** `O(N × K)`
* **Space Complexity:** `O(N × K)`

---

## **Execution Time Limit**

**10 seconds**