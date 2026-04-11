# **Problem 1041: Shift Empty Chocolate Packets to the End**

**Company:** TCS

**Topic:** Arrays / Two Pointers

---

## **Problem Statement**

In a chocolate factory warehouse, packets of chocolates are stored in a row. Each packet is represented by an integer:

* **0** → represents an **empty packet**
* **Non-zero value** → represents a packet containing chocolates

Due to poor arrangement, empty packets are scattered throughout the row. To improve efficiency, the factory manager wants all **empty packets (0s)** to be moved to the **end of the row**, while maintaining the **relative order of non-empty packets**.

---

## **Task**

Rearrange the given array such that:

* All **0s are moved to the end**
* The **relative order of non-zero elements remains unchanged**
* The operation must be done **in-place** (without using extra space if possible)

---

## **Input Format**

* The **first line** contains an integer **n** — number of packets
* The **second line** contains **n integers** representing the packets

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **0 ≤ arr[i] ≤ 10⁹**

---

## **Output Format**

Print the **modified array** after shifting all zeroes to the end.

---

## **Sample Input 1**

```text id="x3k9va"
6
0 1 0 3 12 0
```

---

## **Sample Output 1**

```text id="b8r2dy"
1 3 12 0 0 0
```

---

## **Explanation**

Original array:

```text id="n2w8qp"
[0, 1, 0, 3, 12, 0]
```

After moving all zeroes to the end while preserving order:

```text id="k4t7mz"
[1, 3, 12, 0, 0, 0]
```

---

## **Sample Input 2**

```text id="v1m8qs"
5
1 2 3 4 5
```

---

## **Sample Output 2**

```text id="r7d2lx"
1 2 3 4 5
```

---

## **Explanation**

There are no empty packets, so the array remains unchanged.

---

## **Key Insight**

* Use a **two-pointer approach**:

  * One pointer tracks position for next non-zero element
  * Another iterates through the array
* Efficiently shifts elements in **O(n)** time

---

## **Execution Time Limit**

**10 seconds**