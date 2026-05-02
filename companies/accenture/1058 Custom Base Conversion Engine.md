# **Problem 1058: Custom Base Conversion Engine**

**Company:** Accenture

**Topic:** Number System / Strings

---

## **Problem Description**

In a data encoding system, numbers must be converted from decimal format into a **custom base representation** for efficient storage.

You are given:

* An integer **n** representing the base
* A decimal integer **num**

Your task is to convert the decimal number into its **base-n equivalent** using a defined symbol set.

---

## **Representation Rules**

The system supports bases up to **36**, using the following mapping:

```text id="map1"
0 → '0', 1 → '1', ..., 9 → '9'
10 → 'A', 11 → 'B', ..., 35 → 'Z'
```

---

## **Task**

Implement the function:

```text id="func1"
char* convertToBase(int n, int num)
```

Return the **correct base-n representation** of the given number as a string.

---

## **Conversion Logic**

Follow these steps:

1. Divide the number by **n** (integer division)
2. Record the **remainder**
3. Replace the number with the quotient
4. Repeat until the number becomes **0**
5. Reverse the collected remainders to get the final result

---

## **Input Format**

* First line: integer **n**
* Second line: integer **num**

---

## **Constraints**

* **2 ≤ n ≤ 36**
* **1 ≤ num ≤ 10⁹**

---

## **Output Format**

* Print the base-n representation as a string

---

## **Sample Input 1**

```text id="in1"
n: 12
num: 845
```

---

## **Sample Output 1**

```text id="out1"
5A5
```

---

## **Explanation**

Step-by-step conversion:

```text id="exp1"
845 ÷ 12 = 70 remainder 5
70 ÷ 12 = 5 remainder 10 (A)
5 ÷ 12 = 0 remainder 5
```

Now reverse the remainders:

```text id="exp2"
5, A, 5 → 5A5
```

---

## **Sample Input 2**

```text id="in2"
n: 16
num: 1023
```

---

## **Sample Output 2**

```text id="out2"
3FF
```

---

## **Explanation**

```text id="exp3"
1023 ÷ 16 = 63 remainder 15 (F)
63 ÷ 16 = 3 remainder 15 (F)
3 ÷ 16 = 0 remainder 3
```

Reverse:

```text id="exp4"
3, F, F → 3FF
```

---

## **Edge Case**

```text id="edge1"
Input:
n: 2
num: 1

Output:
1
```

---

## **What they check:**

* Correct **division-remainder logic**
* Proper **character mapping (0–9, A–Z)**
* Correct **reverse construction of result**
* Edge case handling (small numbers, base extremes)

---

## **Execution Time Limit**

**10 seconds**