# **Problem 1064: Sum of Numbers Divisible by Two Integers in a Range**

**Company:** Accenture

**Topic:** Math / Number Theory

---

## **Problem Description**

In a data filtering system, you are required to compute the total contribution of numbers that satisfy multiple divisibility constraints.

You are given:

* Two integers **A** and **B**
* A range defined by **L** and **R**

Your task is to calculate the **sum of all integers within the range [L, R]** that are divisible by **both A and B**.

---

## **Key Observation**

A number divisible by both **A** and **B** must be divisible by:

```text id="lcmdef"
LCM(A, B)
```

---

## **Task**

Return the sum of all numbers in the range **[L, R]** that are divisible by **LCM(A, B)**.

---

## **Input Format**

* First line: integer **L** (lower bound)
* Second line: integer **R** (upper bound)
* Third line: integer **A**
* Fourth line: integer **B**

---

## **Constraints**

* **1 ≤ L ≤ R ≤ 10⁹**
* **1 ≤ A, B ≤ 10⁶**

---

## **Output Format**

* Print a single integer — the required sum

---

## **Sample Input 1**

```text id="in1"
1
20
2
3
```

---

## **Sample Output 1**

```text id="out1"
36
```

---

## **Explanation**

```text id="exp1"
LCM(2,3) = 6

Multiples of 6 in [1,20]:
6, 12, 18

Sum = 6 + 12 + 18 = 36
```

---

## **Sample Input 2**

```text id="in2"
10
50
4
6
```

---

## **Sample Output 2**

```text id="out2"
120
```

---

## **Explanation**

```text id="exp2"
LCM(4,6) = 12

Multiples of 12 in [10,50]:
12, 24, 36, 48

Sum = 12 + 24 + 36 + 48 = 120
```

---

## **Edge Case**

```text id="edge1"
Input:
5
10
7
11

Output:
0
```

---

## **Explanation**

```text id="edge2"
LCM(7,11) = 77
No multiples in range → sum = 0
```

---

## **Key Insight**

* Compute **LCM(A, B)** using:

```text id="formula1"
LCM(A,B) = (A × B) / GCD(A,B)
```

* Instead of iterating, use arithmetic progression:

  * Find first and last multiples in range
  * Use sum formula for AP

Time Complexity: **O(log(min(A,B)))**

---

## **What they check:**

* Understanding of **LCM and GCD**
* Ability to optimize from brute force to **math-based solution**
* Handling large ranges efficiently
* Edge cases with no valid multiples

---

## **Execution Time Limit**

**10 seconds**