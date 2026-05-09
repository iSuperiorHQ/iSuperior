# **Problem 1075: Exact String Pattern Matching**

**Company:** Capgemini

**Topic:** Strings / Pattern Matching / KMP Basics

---

## **Problem Description**

A cybersecurity monitoring system continuously scans large text logs to detect suspicious signature patterns.

You are given:

* A large text string `T`
* A pattern string `P`

Your task is to identify all exact occurrences of the pattern inside the text and return the total number of matches.

The matching must be:

* Case-sensitive
* Exact character-by-character matching
* Efficient for very large input strings

---

## **Task**

Determine how many times the pattern string `P` occurs inside text string `T`.

Overlapping occurrences must also be counted separately.

---

## **Input Format**

* First line: string **T** — main text
* Second line: string **P** — pattern to search

---

## **Constraints**

* **1 ≤ |P| ≤ |T| ≤ 10⁶**
* Strings may contain:

  * Uppercase/lowercase English letters
  * Digits
  * Special characters

---

## **Output Format**

Print a single integer — the total number of exact occurrences of the pattern.

---

## **Sample Input 1**

```text id="m8v2zk"
abababa
aba
```

---

## **Sample Output 1**

```text id="x1m9qa"
3
```

---

## **Explanation**

Pattern `"aba"` occurs at:

```text id="k7m2vx"
Index 0
Index 2
Index 4
```

Overlapping matches are included.

---

## **Sample Input 2**

```text id="u3m8qp"
aaaaa
aa
```

---

## **Sample Output 2**

```text id="f9m1zk"
4
```

---

## **Explanation**

Occurrences:

```text id="r2m8vx"
aa
 aa
  aa
   aa
```

Total matches = **4**

---

## **Sample Input 3**

```text id="n7m2qa"
networksecurity
hack
```

---

## **Sample Output 3**

```text id="p4m9xp"
0
```

---

## **Explanation**

Pattern `"hack"` does not occur in the text.

---

## **Sample Input 4**

```text id="v1m8zk"
abcABCabc
ABC
```

---

## **Sample Output 4**

```text id="g8m2vx"
1
```

---

## **Explanation**

Matching is case-sensitive.

Only:

```text id="x2m1qa"
ABC
```

matches exactly.

---

## **Optimized Approach**

A naive approach checks every substring:

```text id="m9v2zk"
O(N × M)
```

For large inputs, efficient algorithms are preferred:

* Knuth-Morris-Pratt (KMP)
* Rabin-Karp
* Z-Algorithm

KMP preprocessing enables linear-time matching.

---

## **KMP Insight**

Construct:

```text id="k4m8qp"
LPS (Longest Prefix Suffix) array
```

to avoid rechecking already matched characters.

This improves performance significantly for repeated patterns.

---

## **Expected Complexity**

### KMP Algorithm

* **Time Complexity:** `O(N + M)`
* **Space Complexity:** `O(M)`

Where:

* `N` = length of text
* `M` = length of pattern

---

## **Execution Time Limit**

**10 seconds**
