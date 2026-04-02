# **Problem 1020: Minimum Dictionary String Partition**

**Company:** Microsoft

**Topic:** Dynamic Programming / String / Trie

---

## **Problem Statement**

You are given:

* A string **s**
* A list of valid **dictionary words**

Your task is to partition the string **s** into **non-overlapping substrings** such that:

* Each substring is present in the **dictionary**
* The entire string is fully covered (no leftover characters)

---

### **Task**

Return the **minimum number of substrings** required to partition the string.

If it is **not possible** to partition the string using the dictionary, return **-1**.

---

## **Input Format**

* The **first line** contains string **s**
* The **second line** contains integer **n** (number of words in dictionary)
* The next **n lines** contain dictionary words

---

## **Constraints**

* **1 ≤ |s| ≤ 10⁴**
* **1 ≤ n ≤ 10⁴**
* Total length of all dictionary words ≤ **10⁵**
* All strings consist of **lowercase English letters**

---

## **Output Format**

Return an integer representing the **minimum number of partitions** required.
Return **-1** if no valid partition exists.

---

## **Sample Input 1**

```text id="czr3a5"
applepenapple
2
apple
pen
```

---

## **Sample Output 1**

```text id="dpv8s2"
3
```

---

## **Explanation**

Valid partition:

```text id="xk0c7m"
apple | pen | apple
```

Total substrings = **3**

---

## **Sample Input 2**

```text id="5vx7jk"
catsandog
5
cats
dog
sand
and
cat
```

---

## **Sample Output 2**

```text id="5sj0tk"
-1
```

---

## **Explanation**

The string cannot be fully segmented using the given dictionary.

---

## **Sample Input 3**

```text id="tn0o2f"
aaaaaaa
2
aa
aaa
```

---

## **Sample Output 3**

```text id="7w4t8c"
3
```

---

## **Explanation**

One optimal partition:

```text id="k9g7s1"
aaa | aaa | aa
```

Total substrings = **3**

---

## **Key Insight**

This problem is a variation of **Word Break**, but instead of checking feasibility, we must:

* **Minimize the number of partitions**

Approaches:

* **Dynamic Programming (DP)**
* Optional optimization using **Trie** for faster lookup

Time Complexity: **O(n²)** (can be optimized with Trie)

---

## **Execution Time Limit**

**10 seconds**