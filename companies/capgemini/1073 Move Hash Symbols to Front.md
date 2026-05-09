# **Problem 1073: Move Hash Symbols to Front**

**Company:** Capgemini

**Topic:** Strings / Stable Rearrangement

---

## **Problem Description**

A secure logging system stores encoded event identifiers using alphanumeric characters mixed with hash (`#`) symbols.
During preprocessing, all hash symbols must be shifted to the beginning of the string while preserving the relative order of all remaining characters.

You are given a string containing:

* Lowercase and uppercase alphabets
* Digits
* Hash (`#`) symbols

Your task is to rearrange the string such that:

1. All `#` symbols appear at the front
2. The relative order of non-hash characters remains unchanged

---

## **Task**

Implement the function:

```text id="v1m9zk"
moveHash(char str[], int n)
```

which returns the transformed string after moving all hash symbols to the beginning.

---

## **Important Requirement**

The transformation must be:

```text id="k7m2qa"
Stable
```

meaning the original order of non-hash characters must remain unchanged.

---

## **Input Format**

* First line: integer **n** — length of the string
* Second line: string **str**

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* String contains:

  * Alphabets (`a-z`, `A-Z`)
  * Digits (`0-9`)
  * Hash symbols (`#`)

---

## **Output Format**

Print the modified string after shifting all hash symbols to the front.

---

## **Sample Input 1**

```text id="q2m8vx"
8
ab#c#d##
```

---

## **Sample Output 1**

```text id="x7m1qa"
####abcd
```

---

## **Explanation**

Original string:

```text id="m4k9zp"
ab#c#d##
```

Total hash symbols:

```text id="p8m2qa"
4
```

Remaining characters in original order:

```text id="z1m9vx"
abcd
```

Final transformed string:

```text id="u7m2zk"
####abcd
```

---

## **Sample Input 2**

```text id="k2m8qp"
10
12#AB#9xy
```

---

## **Sample Output 2**

```text id="n9m1qa"
##12AB9xy
```

---

## **Explanation**

Hash symbols are moved to the beginning while preserving the order:

```text id="g7m2vx"
1 → 2 → A → B → 9 → x → y
```

---

## **Sample Input 3**

```text id="r8m1zk"
5
#####
```

---

## **Sample Output 3**

```text id="v3m2qa"
#####
```

---

## **Explanation**

The string already contains only hash symbols.

---

## **Sample Input 4**

```text id="y1m8xp"
6
abc123
```

---

## **Sample Output 4**

```text id="f2m9qa"
abc123
```

---

## **Explanation**

No hash symbols exist, so the string remains unchanged.

---

## **Optimized Approach**

Efficient solution strategy:

1. Count total hash symbols
2. Store non-hash characters in original order
3. Construct final string:

```text id="h8m2vx"
(all hashes) + (remaining characters)
```

---

## **Expected Complexity**

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(N)`

---

## **Execution Time Limit**

**10 seconds**
