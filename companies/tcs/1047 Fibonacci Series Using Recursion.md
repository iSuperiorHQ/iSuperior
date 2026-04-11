# **Problem 1047: Generate Fibonacci Series Using Recursion**

**Company:** TCS

**Topic:** Recursion

---

## **Problem Description**

The Fibonacci sequence is a series of numbers where each number is the sum of the two preceding ones.

The sequence starts as:

```text
0, 1, 1, 2, 3, 5, 8, ...
```

You are required to generate the Fibonacci series up to the **Nth term** using a **recursive approach**.

---

## **Task**

* Implement a recursive function to generate Fibonacci numbers
* Print the Fibonacci series up to **N terms**

---

## **Input Format**

* The first line contains an integer **N** — number of terms

---

## **Constraints**

* **1 ≤ N ≤ 30**

---

## **Output Format**

* Print the first **N Fibonacci numbers** separated by spaces

---

## **Sample Input**

```text
5
```

---

## **Sample Output**

```text
0 1 1 2 3
```

---

## **Explanation**

Fibonacci series:

* F(0) = 0
* F(1) = 1
* F(n) = F(n-1) + F(n-2)

For N = 5:

```text
0 1 1 2 3
```

---

## **What they check:**

* Understanding of **recursion base cases**
* Correct recursive relation
* Handling small values of N

---

## **Execution Time Limit**

**10 seconds**