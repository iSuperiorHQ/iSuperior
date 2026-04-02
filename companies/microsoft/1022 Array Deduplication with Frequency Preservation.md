# **Problem 1022: Array Deduplication with Frequency Preservation**

**Company:** Microsoft

**Topic:** Arrays / Hash Map / Frequency Counting

---

## **Problem Statement**

You are given an array of integers. Your task is to **remove duplicates** from the array while preserving:

1. The **relative order of first occurrence** of elements
2. The **frequency information** of each element

---

### **Task**

Construct a new array such that:

* Each **distinct element appears exactly once**
* Elements are ordered based on their **first occurrence in the original array**
* Additionally, you must output the **frequency of each element**

---

## **Input Format**

* The **first line** contains an integer **n**, the size of the array
* The **second line** contains **n integers** representing the array

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **-10⁹ ≤ arr[i] ≤ 10⁹**

---

## **Output Format**

* First line: print the **deduplicated array**
* Second line: print the **frequency of each corresponding element**

---

## **Sample Input**

```text id="2n6b7x"
8
4 5 4 6 5 4 7 6
```

---

## **Sample Output**

```text id="k3v8pz"
4 5 6 7
3 2 2 1
```

---

## **Explanation**

Original array:

```text id="z9r1hk"
[4, 5, 4, 6, 5, 4, 7, 6]
```

* First occurrences → **4, 5, 6, 7**
* Frequencies:

  * 4 → 3 times
  * 5 → 2 times
  * 6 → 2 times
  * 7 → 1 time

---

## **Sample Input 2**

```text id="m7y2wq"
5
1 2 3 4 5
```

---

## **Sample Output 2**

```text id="r4k8t1"
1 2 3 4 5
1 1 1 1 1
```

---

## **Explanation**

All elements are unique, so each appears once.

---

## **Key Insight**

* Use a **Hash Map** to store frequency
* Use a **Set or Ordered Map** (or simple traversal) to maintain order of first occurrence

Time Complexity: **O(n)**
Space Complexity: **O(n)**

---

## **Execution Time Limit**

**10 seconds**