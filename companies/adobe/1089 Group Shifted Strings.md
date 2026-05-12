# **Problem 1089: Group Shifted Strings**

**Company:** Adobe

**Topic:** Hashing / String Math

**Difficulty:** Medium

---

## **Problem Description**

A text compression engine analyzes patterns between encoded strings to identify transformation-based equivalence groups.

Two strings are considered:

```text id="m2v8zk"
Shift-Equivalent
```

if every character in one string can be shifted forward by the same number of positions cyclically in the English alphabet to obtain the other string.

Character shifting follows circular alphabetical order:

```text id="x7m1qa"
'z' → 'a'
```

For example:

```text id="u3m8qp"
abc → bcd
xyz → yza
az → ba
```

all belong to valid shifted groups.

Your task is to group all strings that belong to the same shifting sequence.

---

## **Shift Rule**

For every adjacent pair of characters:

```text id="f9m1zk"
difference =
(currentCharacter - previousCharacter + 26) % 26
```

Two strings belong to the same group if their relative difference patterns are identical.

---

## **Task**

Given a list of lowercase strings, group together all shift-equivalent strings.

Strings inside each group should appear in lexicographical order.

For consistency, print groups ordered by the lexicographically smallest string in each group.

---

## **Input Format**

* First line: integer **N** — total number of strings
* Next `N` lines: one lowercase string per line

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **1 ≤ length of each string ≤ 100**
* Total combined characters ≤ `10⁶`

---

## **Output Format**

Print grouped shifted strings.

Each group should be printed on a separate line.

Strings inside a group must be space-separated and lexicographically sorted.

---

## **Sample Input 1**

```text id="r2m8vx"
8
abc
bcd
acef
xyz
az
ba
a
z
```

---

## **Sample Output 1**

```text id="n7m2qa"
a z
abc bcd xyz
acef
az ba
```

---

## **Explanation**

Relative shift patterns:

```text id="p4m9xp"
abc  → (1,1)
bcd  → (1,1)
xyz  → (1,1)
```

Hence they belong to the same group.

Similarly:

```text id="v1m8zk"
az → (25)
ba → (25)
```

Single-character strings:

```text id="g8m2vx"
a
z
```

always belong together because shifting preserves single-length structure.

---

## **Sample Input 2**

```text id="x2m1qa"
5
no
op
qr
lm
yz
```

---

## **Sample Output 2**

```text id="m9v2zk"
lm no op qr yz
```

---

## **Explanation**

All strings share identical relative shift pattern:

```text id="k4m8qp"
(1)
```

Hence they form a single group.

---

## **Sample Input 3**

```text id="u7m1xp"
6
acd
dfg
wyz
bdf
egi
fhj
```

---

## **Sample Output 3**

```text id="m4k8qa"
acd dfg wyz
bdf egi fhj
```

---

## **Explanation**

Group 1 pattern:

```text id="v8m2zk"
acd → (2,1)
dfg → (2,1)
wyz → (2,1)
```

Group 2 pattern:

```text id="x1m9vx"
bdf → (2,2)
egi → (2,2)
fhj → (2,2)
```

---

## **Sample Input 4**

```text id="z7m2qp"
4
aaa
bbb
ccc
xyz
```

---

## **Sample Output 4**

```text id="u4m8zk"
aaa bbb ccc
xyz
```

---

## **Explanation**

Strings:

```text id="k2m1qa"
aaa
bbb
ccc
```

all produce identical difference pattern:

```text id="r7m2zk"
(0,0)
```

Hence they belong to the same group.

String:

```text id="u1m8xp"
xyz
```

has pattern:

```text id="m4k8qa"
(1,1)
```

and forms a separate group.

---

## **Hashing Insight**

Each string can be transformed into a canonical signature based on relative character differences.

Example:

```text id="v8m2zk"
abc → 1#1
bcd → 1#1
xyz → 1#1
```

Use this signature as the hash key for grouping.

---

## **Efficient Strategy**

For every string:

1. Compute cyclic adjacent differences
2. Build normalized pattern key
3. Insert string into corresponding hash bucket

Finally:

* Sort strings inside every group
* Sort groups using the lexicographically smallest string
* Print grouped results

---

## **Expected Complexity**

### HashMap Grouping Approach

* **Time Complexity:** `O(T)`
* **Space Complexity:** `O(T)`

Where:

* `T` = total number of characters across all strings

Additional sorting cost:

```text id="x1m9vx"
O(N log N)
```

across grouped outputs.

---

## **Execution Time Limit**

**10 seconds**