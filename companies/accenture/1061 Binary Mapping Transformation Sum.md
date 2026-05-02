# **Problem 1061: Binary Mapping Transformation and Summation**

**Company:** Accenture

**Topic:** Math / Bit Manipulation

---

## **Problem Description**

In a custom encoding system, a decimal number is transformed using a **binary mapping rule**.

You are given a non-negative integer **N**. You must apply a sequence of transformations and compute the final result.

---

## **Transformation Rules**

1. Convert the decimal number **N** into its **binary representation**
2. For each binary digit:

   * Replace **0 → 2**
   * Replace **1 → 3**
3. Treat the resulting sequence as a **decimal number**
4. Compute the **sum of its digits**

---

## **Task**

Return the final computed sum after applying all transformations.

---

## **Input Format**

* A single integer **N**

---

## **Constraints**

* **0 ≤ N ≤ 10⁹**

---

## **Output Format**

* Print a single integer — the resulting sum

---

## **Sample Input 1**

```text
5
```

---

## **Sample Output 1**

```text
8
```

---

## **Explanation**

```text
5 → binary = 101
map → 3 2 3 → 323
sum = 3 + 2 + 3 = 8
```

---

## **Sample Input 2**

```text
8
```

---

## **Sample Output 2**

```text
9
```

---

## **Explanation**

```text
8 → binary = 1000
map → 3 2 2 2 → 3222
sum = 3 + 2 + 2 + 2 = 9
```

---

## **Sample Input 3**

```text
0
```

---

## **Sample Output 3**

```text
2
```

---

## **Explanation**

```text
0 → binary = 0
map → 2
sum = 2
```

---

## **Key Insight**

* Binary conversion takes **O(log N)**
* No need to build full number — directly sum mapped digits
* Efficient solution avoids large string construction

---

## **What they check:**

* Understanding of **binary representation**
* Correct mapping logic
* Edge case handling (especially N = 0)
* Optimization awareness

---

## **Execution Time Limit**

**10 seconds**