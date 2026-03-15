# **Problem 1008: Find the Kth Largest Element in a Continuous Data Stream**

**Company:** Amazon

**Topic:** Heap / Priority Queue

---

## **Problem Statement**

You are given a stream of integers arriving one by one. Your task is to design a system that efficiently returns the **kth largest element** in the stream at any point in time.

You must implement a data structure that supports the following operations:

* **add(val)** → Adds the integer **val** to the data stream.
* **getKthLargest()** → Returns the **kth largest element** among all elements seen so far.

Your solution should be efficient even for a **large number of incoming elements**.

---

## **Input Format**

* The **first line** contains two integers **k** and **n**.
* The **second line** contains **n integers** representing the initial stream.
* The **next lines** contain operations:

```
add value
get
```

---

## **Constraints**

* **1 ≤ k ≤ 10⁴**
* **1 ≤ n ≤ 10⁵**
* **-10⁹ ≤ value ≤ 10⁹**
* Total number of operations ≤ **10⁵**

---

## **Output Format**

For every **get** operation, print the **kth largest element** in the stream.

---

## **Sample Input**

```
3 4
4 5 8 2
add 3
get
add 10
get
```

---

## **Sample Output**

```
4
5
```

---

## **Explanation**

Initial stream: **[4,5,8,2]**

3rd largest element = **4**

After inserting **10**:

Stream becomes **[4,5,8,2,3,10]**

3rd largest element = **5**

---

## **Execution Time Limit**

**10 seconds**