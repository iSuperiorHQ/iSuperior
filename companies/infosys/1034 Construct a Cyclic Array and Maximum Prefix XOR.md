# **Problem 1034: Construct a Cyclic Array and Find Maximum Prefix XOR Sum**

**Company:** Infosys

**Topic:** Bit Manipulation / Trie

---

## **Problem Statement**

You are given an array of **N integers**. You can form a **cyclic array** by choosing any index as the starting point and wrapping around the array.

For a chosen starting index, construct a new array by traversing elements in order and wrapping back to the beginning when the end is reached.

---

### **Task**

For each possible cyclic rotation:

1. Construct the rotated array
2. Compute the **prefix XOR values**
3. Find the **maximum XOR value among all prefixes**

Return the **maximum prefix XOR value across all possible cyclic rotations**.

---

## **Definitions**

* **Cyclic Array:**
  If original array is:

```text id="j8k3w1"
[ a0, a1, a2, ..., an-1 ]
```

Then one cyclic rotation starting at index `i` becomes:

```text id="h7t9d2"
[ ai, ai+1, ..., an-1, a0, a1, ..., ai-1 ]
```

---

* **Prefix XOR:**
  For array `[x1, x2, x3, ...]`

```text id="z6v1q8"
prefix[1] = x1
prefix[2] = x1 ^ x2
prefix[3] = x1 ^ x2 ^ x3
...
```

---

## **Input Format**

* The **first line** contains integer **N**
* The **second line** contains **N integers** representing the array

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **0 ≤ arr[i] ≤ 10⁹**

---

## **Output Format**

Return a single integer representing the **maximum prefix XOR value** among all cyclic rotations.

---

## **Sample Input**

```text id="7m2kq1"
4
1 2 3 4
```

---

## **Sample Output**

```text id="d3k8n0"
7
```

---

## **Explanation**

Consider cyclic rotations:

1. **[1, 2, 3, 4]**
   Prefix XORs → 1, 3, 0, 4 → max = 4

2. **[2, 3, 4, 1]**
   Prefix XORs → 2, 1, 5, 4 → max = 5

3. **[3, 4, 1, 2]**
   Prefix XORs → 3, 7, 6, 4 → max = 7

4. **[4, 1, 2, 3]**
   Prefix XORs → 4, 5, 7, 4 → max = 7

Final answer = **7**

---

## **Key Insight**

* XOR properties can be leveraged for optimization
* Instead of checking all rotations naively (**O(N²)**), optimize using:

  * **Prefix XOR arrays**
  * **Trie (for maximum XOR queries)**

Time Complexity (optimized): **O(N log M)**
(M = maximum number of bits)

---

## **Execution Time Limit**

**10 seconds**