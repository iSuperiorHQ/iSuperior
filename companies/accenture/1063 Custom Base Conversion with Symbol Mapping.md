# **Problem 1063: Custom Base Conversion with Symbol Mapping**

**Company:** Accenture

**Topic:** Math / Number System

---

## **Problem Description**

A data encoding system uses **non-standard base representations** with a custom set of symbols. Each base can have its own mapping of digits to characters.

You are given multiple queries where each query consists of:

* A decimal number **N**
* A base **B**
* A custom symbol string **S** representing the digits of that base

Your task is to convert the decimal number into its **base-B representation using the provided symbol mapping**.

---

## **Symbol Mapping Rules**

* The string **S** contains exactly **B distinct characters**
* Each character represents a digit:

```text
S[0] → value 0  
S[1] → value 1  
...  
S[B-1] → value B-1  
```

---

## **Task**

For each query:

* Convert the decimal number **N** into base **B**
* Replace each digit using the mapping defined by **S**
* Return the resulting encoded string

---

## **Input Format**

* First line: integer **Q** — number of queries
* For each query:

  * Line 1: integer **N**
  * Line 2: integer **B**
  * Line 3: string **S**

---

## **Constraints**

* **1 ≤ Q ≤ 10⁵**
* **0 ≤ N ≤ 10⁹**
* **2 ≤ B ≤ 36**
* **|S| = B**, all characters in **S** are unique

---

## **Output Format**

* For each query, print the converted encoded string

---

## **Sample Input**

```text
2
31
16
0123456789ABCDEF
10
2
01
```

---

## **Sample Output**

```text
1F
1010
```

---

## **Explanation**

### Query 1:

```text
N = 31, B = 16
31 → base16 = 1F
Mapping is standard → result = 1F
```

---

### Query 2:

```text
N = 10, B = 2
10 → binary = 1010
Mapping: 0→'0', 1→'1'
Result = 1010
```

---

## **Sample Input 2 (Custom Symbols)**

```text
1
10
3
XYZ
```

---

## **Sample Output 2**

```text
YXY
```

---

## **Explanation**

```text
10 → base3 = 101
Mapping:
0 → X
1 → Y
2 → Z

So:
101 → Y X Y → YXY
```

---

## **Edge Case**

```text
Input:
1
0
5
ABCDE

Output:
A
```

---

## **Key Insight**

* Use repeated **division by base (B)**
* Store remainders and map using string **S**
* Reverse the result
* Special handling for **N = 0**

---

## **What they check:**

* Understanding of **generalized base conversion**
* Handling **custom digit mapping**
* Efficient processing of **multiple queries**
* Edge cases (zero, large inputs, custom symbols)

---

## **Execution Time Limit**

**10 seconds**