# **Problem 1056: Implement Iterative Binary Search**

**Company:** Cognizant

**Topic:** Arrays

---

## **Problem Description**

You are given a **sorted array of integers** and a target value.

Your task is to implement the **Binary Search algorithm using an iterative approach** (without recursion) to find the index of the target element.

This approach avoids recursion and helps prevent **stack overflow issues** for large inputs.

---

## **Task**

* Search for the given target in the sorted array
* If the target is found, return its **index (0-based)**
* If the target is not found, return **-1**

---

## **Input Format**

* The first line contains an integer **n** — number of elements
* The second line contains **n sorted integers**
* The third line contains the **target value**

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **-10⁹ ≤ arr[i] ≤ 10⁹**
* Array is sorted in **ascending order**

---

## **Output Format**

* Print the index of the target element
* Print **-1** if the element is not found

---

## **Sample Input 1**

```text id="n3x9vk"
5
1 3 5 7 9
7
```

---

## **Sample Output 1**

```text id="k2m8xp"
3
```

---

## **Explanation**

Array:

```text id="r7m4qa"
[1, 3, 5, 7, 9]
```

Target = **7**, found at index **3**

---

## **Sample Input 2**

```text id="v8p2xz"
4
2 4 6 8
5
```

---

## **Sample Output 2**

```text id="t3k9mz"
-1
```

---

## **Explanation**

Target **5** is not present in the array.

---

## **What they check:**

* Understanding of **binary search logic**
* Correct use of **loop conditions (low ≤ high)**
* Avoiding recursion
* Handling edge cases (single element, not found)

---

## **Execution Time Limit**

**10 seconds**