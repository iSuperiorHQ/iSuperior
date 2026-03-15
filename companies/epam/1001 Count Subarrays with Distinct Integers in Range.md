# **Problem 1001: Count Subarrays with Distinct Integers in Range**

**Company:** EPAM

---

## **Problem Statement**

Given a collection of **N cards**, each labeled with a numerical value, your task is to find and count the **consecutive cards (forming subarrays)** where the number of **distinct integers** falls within the inclusive range **[l, r]**.

---

## **Input Format**

* The **first line of input** contains an integer **l**.
* The **second line of input** contains an integer **r**.
* The **third line of input** contains an integer **N**.
* The **next N lines of input** each contain an integer.

---

## **Constraints**

* **1 <= cards.length <= 2 * 10^4**
* **1 <= cards[i], k <= cards.length**
* **1 <= l <= r < cards.length**

---

## **Output Format**

* It will be an integer which represents the **total count of the consecutive cards (subarrays)** where the number of **distinct integers falls within the inclusive range [l, r]**.

---

## **Sample Test Case**

### **Input**

```
2
3
5
1
2
4
2
3
```

---

### **Output**

```
9
```

---

## **Explanation**

As given **l = 2, r = 3, n = 5**

**cards = [1,2,4,2,3]**

Total possible **consecutive cards (subarrays)** where the count of distinct integers falls within the inclusive range **[l, r]** are:

```
(1,2)
(1,2,4)
(1,2,4,2)
(2,4)
(2,4,2)
(2,4,2,3)
(4,2)
(4,2,3)
(2,3)
```

So the answer is **9**.

---

## **Execution Time Limit**

**10 seconds**