# **Problem 1057: Calculate Bitwise OR Result of Two Integers**

**Company:** Accenture

**Topic:** Bit Manipulation

---

## **Problem Description**

In low-level programming and system design, bitwise operations are frequently used for efficient computation.

You are given two integers **A** and **B**. Your task is to compute the **bitwise OR** of these two numbers.

---

## **Definition**

The **bitwise OR ( | )** operation compares each bit of two numbers:

* If **at least one of the bits is 1**, the result is **1**
* Otherwise, the result is **0**

---

## **Task**

* Compute the value of:

```text id="k3m8vz"
A | B
```

* Return the resulting integer

---

## **Input Format**

* The first line contains integer **A**
* The second line contains integer **B**

---

## **Constraints**

* **0 ≤ A, B ≤ 10⁹**

---

## **Output Format**

* Print a single integer — the result of **A | B**

---

## **Sample Input 1**

```text id="x9m2kp"
5
3
```

---

## **Sample Output 1**

```text id="r4k8zt"
7
```

---

## **Explanation**

Binary representation:

```text id="n2x7qa"
5 → 101
3 → 011
```

Bitwise OR:

```text id="v8m3xp"
101
011
---
111 → 7
```

---

## **Sample Input 2**

```text id="p3k9vz"
8
2
```

---

## **Sample Output 2**

```text id="t6m1qa"
10
```

---

## **Explanation**

Binary:

```text id="k2m7zx"
8 → 1000
2 → 0010
```

Result:

```text id="b9x3rp"
1010 → 10
```

---

## **What they check:**

* Understanding of **bitwise operations**
* Binary representation of numbers
* Correct application of OR logic

---

## **Execution Time Limit**

**10 seconds**