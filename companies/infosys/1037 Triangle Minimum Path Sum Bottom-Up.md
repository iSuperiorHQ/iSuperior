# **Problem 1037: Triangle Minimum Path Sum (Bottom-Up Approach)**

**Company:** Infosys

**Topic:** Dynamic Programming

---

## **Problem Statement**

You are given a **triangle array**, where each row contains one more element than the previous row.

Your task is to find the **minimum path sum** from the **top to the bottom** of the triangle.

---

## **Movement Rules**

* Starting from the **top element**, you can move to:

  * The **same index** in the next row
  * The **next index (i + 1)** in the next row

---

## **Objective**

Return the **minimum possible sum** of values along a path from the **top to the bottom**.

---

## **Important Requirement**

You must solve this problem using a **strictly bottom-up dynamic programming approach**.

---

## **Input Format**

* The **first line** contains an integer **n** (number of rows in the triangle)
* The next **n lines** contain the triangle elements

---

## **Constraints**

* **1 ≤ n ≤ 200**
* **-10⁴ ≤ triangle[i][j] ≤ 10⁴**

---

## **Output Format**

Return a single integer representing the **minimum path sum**.

---

## **Sample Input**

```text id="x1v9pm"
4
2
3 4
6 5 7
4 1 8 3
```

---

## **Sample Output**

```text id="k8n2xy"
11
```

---

## **Explanation**

Triangle:

```text id="r7c2zd"
      2
     3 4
    6 5 7
   4 1 8 3
```

Possible path with minimum sum:

```text id="m5b1qa"
2 → 3 → 5 → 1
```

Sum:

```text id="z3k9hp"
2 + 3 + 5 + 1 = 11
```

---

## **Bottom-Up Approach**

Start from the **last row** and move upwards:

* Replace each element with:

```text id="t9x4ac"
current_value + min(down, down-right)
```

* Continue until reaching the top

---

## **Key Insight**

* Avoid recursion for optimal performance
* Use **in-place DP** or a **1D array optimization**

Time Complexity: **O(n²)**
Space Complexity: **O(n)** (optimized)

---

## **Execution Time Limit**

**10 seconds**