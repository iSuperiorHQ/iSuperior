# **Problem 1085: Lexicographically Smallest Suffix Query**

**Company:** Infosys

**Topic:** Strings / Trie

---

## **Problem Description**

A cloud-based document indexing platform stores millions of textual identifiers for rapid keyword lookup.

To optimize query performance, the platform analyzes all possible suffixes of a given string and retrieves the lexicographically smallest suffix.

A suffix of a string is formed by removing zero or more characters from the beginning of the string.

For example:

```text id="m2v8zk"
String: "banana"
```

Possible suffixes:

```text id="x7m1qa"
banana
anana
nana
ana
na
a
```

Among all suffixes, the lexicographically smallest one is:

```text id="u3m8qp"
a
```

Your task is to identify and print the lexicographically smallest suffix of the given string.

---

## **Task**

Given a string `S`, determine the suffix that appears first in dictionary order.

---

## **Lexicographical Ordering Rules**

String `A` is lexicographically smaller than string `B` if:

* At the first differing character:

  * `A` contains a smaller character than `B`

OR

* All compared characters are equal, but:

  * `A` is shorter than `B`

Example:

```text id="f9m1zk"
apple < apply
abc < abcd
```

---

## **Input Format**

* First line: string **S**

---

## **Constraints**

* **1 ≤ |S| ≤ 10⁵**
* String contains lowercase English letters only

---

## **Output Format**

Print the lexicographically smallest suffix of the string.

---

## **Sample Input 1**

```text id="r2m8vx"
banana
```

---

## **Sample Output 1**

```text id="n7m2qa"
a
```

---

## **Explanation**

Suffixes:

```text id="p4m9xp"
banana
anana
nana
ana
na
a
```

Smallest suffix:

```text id="v1m8zk"
a
```

---

## **Sample Input 2**

```text id="g8m2vx"
mississippi
```

---

## **Sample Output 2**

```text id="x2m1qa"
i
```

---

## **Explanation**

Suffixes beginning with:

```text id="m9v2zk"
i
```

are:

```text id="k4m8qp"
ississippi
issippi
ippi
i
```

Among these, the single-character suffix:

```text id="u7m1xp"
i
```

is lexicographically smallest because shorter strings come first when prefixes match.

---

## **Sample Input 3**

```text id="m4k8qa"
abcd
```

---

## **Sample Output 3**

```text id="v8m2zk"
abcd
```

---

## **Explanation**

Suffixes:

```text id="x1m9vx"
abcd
bcd
cd
d
```

Since:

```text id="z7m2qp"
a < b < c < d
```

the complete string itself is the smallest suffix.

---

## **Sample Input 4**

```text id="u4m8zk"
zzza
```

---

## **Sample Output 4**

```text id="k2m1qa"
a
```

---

## **Explanation**

Suffixes:

```text id="r7m2zk"
zzza
zza
za
a
```

Smallest suffix:

```text id="u1m8xp"
a
```

---

## **Trie-Based Insight**

Every suffix can be inserted into a Trie structure.

The lexicographically smallest suffix corresponds to:

* The path with smallest characters first
* Earliest terminal suffix encountered in sorted traversal

---

## **Alternative Optimized Observation**

The problem can also be solved efficiently without explicitly storing all suffixes.

Compare suffixes starting from different indices and track the smallest lexicographical candidate.

---

## **Expected Complexity**

### Trie-Based Approach

* **Time Complexity:** `O(N²)`
* **Space Complexity:** `O(N²)`

because all suffixes may collectively contain:

```text id="m4k8qa"
N + (N-1) + (N-2) + ...
```

characters.

---

## **Optimized Comparison Approach**

* **Time Complexity:** `O(N²)` worst case
* **Space Complexity:** `O(1)`

---

## **Execution Time Limit**

**10 seconds**