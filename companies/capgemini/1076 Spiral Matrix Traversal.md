# **Problem 1076: Spiral Matrix Traversal**

**Company:** Capgemini

**Topic:** Arrays / Matrix Traversal

---

## **Problem Description**

A robotics navigation system stores terrain information in the form of a 2D matrix.
To optimize scanning efficiency, the robot processes the matrix in a spiral pattern starting from the top-left corner.

You are given a matrix of size `R × C`. Your task is to traverse and print all elements of the matrix in clockwise spiral order.

The traversal order must follow:

1. Left → Right
2. Top → Bottom
3. Right → Left
4. Bottom → Top

This process continues layer-by-layer until all elements are visited.

---

## **Task**

Print the elements of the given matrix in spiral order.

---

## **Input Format**

* First line: integers **R** and **C**

  * `R` → number of rows
  * `C` → number of columns

* Next `R` lines:

  * Each line contains `C` integers representing the matrix

---

## **Constraints**

* **1 ≤ R, C ≤ 10³**
* **-10⁹ ≤ matrix[i][j] ≤ 10⁹**

---

## **Output Format**

Print all matrix elements in clockwise spiral traversal order separated by spaces.

---

## **Sample Input 1**

```text id="m2v8zk"
3 3
1 2 3
4 5 6
7 8 9
```

---

## **Sample Output 1**

```text id="x7m1qa"
1 2 3 6 9 8 7 4 5
```

---

## **Explanation**

Traversal sequence:

```text id="k9m2vx"
Top row    → 1 2 3
Right col  → 6 9
Bottom row → 8 7
Left col   → 4
Center     → 5
```

---

## **Sample Input 2**

```text id="u3m8qp"
4 4
1 2 3 4
5 6 7 8
9 10 11 12
13 14 15 16
```

---

## **Sample Output 2**

```text id="f9m1zk"
1 2 3 4 8 12 16 15 14 13 9 5 6 7 11 10
```

---

## **Explanation**

The traversal processes the matrix layer-by-layer in clockwise direction.

---

## **Sample Input 3**

```text id="r2m8vx"
2 5
1 2 3 4 5
6 7 8 9 10
```

---

## **Sample Output 3**

```text id="n7m2qa"
1 2 3 4 5 10 9 8 7 6
```

---

## **Explanation**

Single outer layer traversal:

```text id="p4m9xp"
Top row    → 1 2 3 4 5
Right col  → 10
Bottom row → 9 8 7 6
```

---

## **Sample Input 4**

```text id="v1m8zk"
1 4
5 10 15 20
```

---

## **Sample Output 4**

```text id="g8m2vx"
5 10 15 20
```

---

## **Explanation**

A single-row matrix is traversed directly from left to right.

---

## **Optimized Approach**

Maintain four boundaries:

```text id="x2m1qa"
top
bottom
left
right
```

After traversing one side, update the corresponding boundary.

Continue until all boundaries overlap.

---

## **Traversal Logic**

Repeat the following while:

```text id="m9v2zk"
top <= bottom
AND
left <= right
```

1. Traverse top row
2. Traverse right column
3. Traverse bottom row
4. Traverse left column

Shrink boundaries after every traversal cycle.

---

## **Expected Complexity**

* **Time Complexity:** `O(R × C)`
* **Space Complexity:** `O(1)`
  (excluding output storage)

---

## **Execution Time Limit**

**10 seconds**
