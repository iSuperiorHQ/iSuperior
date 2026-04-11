# **Problem 1045: Calculate Frequency of Elements in an Array**

**Company:** TCS

**Topic:** Arrays / Hash Map

---

## **Problem Description**

You are given an array of integers. Your task is to calculate the **exact frequency of each unique element** present in the array.

The frequency of an element is defined as the number of times it appears in the array.

---

## **Input Format**

* The first line contains an integer **n** — number of elements in the array
* The second line contains **n integers** representing the array

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **-10⁹ ≤ arr[i] ≤ 10⁹**

---

## **Output Format**

* Print each unique element along with its frequency
* The output should follow the order of **first occurrence of elements** in the array

---

## **Sample Input**

```text
8
1 2 2 3 1 4 2 3
```

---

## **Sample Output**

```text
1 2
2 3
3 2
4 1
```

---

## **Explanation**

Array:

```text
[1, 2, 2, 3, 1, 4, 2, 3]
```

Frequencies:

* 1 → 2 times
* 2 → 3 times
* 3 → 2 times
* 4 → 1 time

---

## **What they check:**

* Proper use of **Hash Map / Dictionary**
* Maintaining **order of first occurrence**
* Handling large input efficiently

---

## **Execution Time Limit**

**10 seconds**