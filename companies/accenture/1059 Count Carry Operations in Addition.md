# **Problem 1059: Count Carry Operations During Integer Addition**

**Company:** Accenture

**Topic:** Math / Implementation

---

## **Problem Description**

In standard arithmetic addition, when the sum of two digits exceeds 9, a **carry** is generated and added to the next higher digit.

You are given two non-negative integers. Your task is to determine how many **carry operations** occur when adding these two numbers digit by digit (from right to left).

---

## **Task**

Implement the function:

```text id="func1"
int countCarries(int num1, int num2)
```

Return the **total number of carry operations** generated during the addition process.

---

## **Rules**

* Start adding digits from the **rightmost side (least significant digit)**
* If the sum of digits (including previous carry) is **greater than or equal to 10**, a carry is generated
* This carry is added to the next digit addition
* Continue until all digits are processed

---

## **Input Format**

* First line: integer **num1**
* Second line: integer **num2**

---

## **Constraints**

* **0 ≤ num1, num2 ≤ 10⁹**

---

## **Output Format**

* Print a single integer — the total number of carry operations

---

## **Sample Input 1**

```text id="in1"
num1: 451
num2: 349
```

---

## **Sample Output 1**

```text id="out1"
2
```

---

## **Explanation**

Step-by-step addition:

```text id="exp1"
  451
+ 349
------
```

From right to left:

* 1 + 9 = 10 → carry generated (count = 1)
* 5 + 4 + 1 (carry) = 10 → carry generated (count = 2)
* 4 + 3 + 1 (carry) = 8 → no carry

Total carries = **2**

---

## **Sample Input 2**

```text id="in2"
num1: 23
num2: 563
```

---

## **Sample Output 2**

```text id="out2"
0
```

---

## **Explanation**

```text id="exp2"
   23
+ 563
------
```

* 3 + 3 = 6 → no carry
* 2 + 6 = 8 → no carry
* 0 + 5 = 5 → no carry

Total carries = **0**

---

## **Edge Case**

```text id="edge1"
num1: 999
num2: 1
```

Output:

```text id="edge2"
3
```

---

## **What they check:**

* Digit-wise processing using **modulo and division**
* Correct handling of **carry propagation**
* Edge cases (different lengths, zero values)

---

## **Execution Time Limit**

**10 seconds**