# **Problem 1003: Stable Range Partition of Array**

**Company:** EPAM

---

## **Problem Statement**

You are given an array of exactly **n integers** and two integers **low** and **high** that define a range. Your task is to rearrange the array such that all elements with values within the range **[low, high]** are moved to the end of the array.

The **relative order of elements within each partition should remain unchanged**.

---

## **Input Format**

* The **first line** contains an integer **n**, the size of the array.
* The **next n lines** contain the **array elements**.
* After the elements, **low** — an integer representing the **lower bound of the value range**.
* **high** — an integer representing the **upper bound of the value range**.

---

## **Constraints**

* **1 <= n <= 10⁶**
* **low and high are within the range of a 32-bit signed integer**

---

## **Output Format**

Modify the array so that **elements within the range [low, high] are moved to the end of the array while preserving their relative order**.
The elements **not in this range should appear first**.

---

## **Evaluation Parameters**

### **Sample Input**

```
5
3
1
5
4
7
2
5
```

---

### **Sample Output**

```
1
7
3
5
4
```

---

## **Explanation**

Elements **3, 5, and 4** fall within the range **[2, 5]** and are moved to the end, while elements **1 and 7** are kept at the beginning in their **original order**.

---

## **Execution Time Limit**

**10 seconds**