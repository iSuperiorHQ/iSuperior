# **Problem 1013: Alien Dictionary Order from Sorted Words**

**Company:** Amazon

**Topic:** Graph / Topological Sort

---

## **Problem Statement**

You are given a list of **words sorted according to an unknown alien language**.

Your task is to **determine the order of characters in the alien language**.

If multiple valid orders exist, return **any one of them**.
If it is **impossible to determine a valid ordering**, return an **empty string**.

---

## **Input Format**

* The **first line** contains an integer **n** representing the number of words.
* The **next n lines** contain the words.

---

## **Constraints**

* **1 ≤ n ≤ 10⁴**
* **1 ≤ length of each word ≤ 100**
* Words consist of **lowercase English letters**

---

## **Output Format**

Return a string representing the **correct character order** in the alien language.

---

## **Sample Input**

```
5
wrt
wrf
er
ett
rftt
```

---

## **Sample Output**

```
wertf
```

---

## **Explanation**

From the sorted order of words we deduce character dependencies such as:

```
w → e
e → r
r → t
t → f
```

A valid ordering is **wertf**.

---

## **Execution Time Limit**

**10 seconds**