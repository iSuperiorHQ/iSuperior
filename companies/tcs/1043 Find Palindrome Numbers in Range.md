# **Problem 1043: Discover Palindrome Numbers in a Given Range**

**Company:** TCS

**Topic:** Math

---

## **Problem Statement**

A number is called a **palindrome** if it reads the same forward and backward.

You are given a range of integers **[L, R]**. Your task is to **find and print all palindrome numbers** within this range (inclusive).

---

## **Task**

* Identify all numbers between **L and R**
* Print only those numbers that are **palindromes**

---

## **Input Format**

* The **first line** contains an integer **L** (lower bound)
* The **second line** contains an integer **R** (upper bound)

---

## **Constraints**

* **1 ≤ L ≤ R ≤ 10⁶**

---

## **Output Format**

* Print all palindrome numbers in the range **[L, R]** separated by spaces

---

## **Sample Input**

```text id="u8m3zn"
10
50
```

---

## **Sample Output**

```text id="p9k2wx"
11 22 33 44
```

---

## **Explanation**

Numbers between 10 and 50:

```text id="r2m8qv"
10, 11, 12, ..., 50
```

Palindrome numbers:

```text id="z7x1dc"
11, 22, 33, 44
```

---

## **Sample Input 2**

```text id="f4k7qa"
1
20
```

---

## **Sample Output 2**

```text id="n5p2tr"
1 2 3 4 5 6 7 8 9 11
```

---

## **Explanation**

Single-digit numbers are always palindromes.

---

## **Key Insight**

* A number is palindrome if:

```text id="g9v2xm"
number == reverse(number)
```

* Can be checked using:

  * String conversion
  * OR mathematical reversal

Time Complexity: **O((R - L) × digits)**

---

## **Execution Time Limit**

**10 seconds**