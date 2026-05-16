# **Problem 104: Spiral Matrix**

**Company:** ServiceNow

**Category:** Arrays / Matrix Traversal

**Difficulty:** Medium

---

# **Problem Description**

A data visualization platform stores information inside large 2D matrices representing sensor readings, image pixels, and heatmaps.

To efficiently serialize matrix data for reporting and transmission, engineers need to traverse matrices in a:

```text id="m2v8zk"
spiral order
```

starting from the top-left corner.

Your task is to return all elements of an:

```text id="x7m1qa"
m × n
```

matrix in clockwise spiral traversal order.

---

# **Spiral Traversal Order**

Traversal proceeds layer-by-layer in the following sequence:

1. Left → Right
2. Top → Bottom
3. Right → Left
4. Bottom → Top

Then continue inward toward the next layer.

---

# **Task**

Given an integer matrix:

```text id="u3m8qp"
matrix
```

return all matrix elements in spiral order.

---

# **Input Format**

First line contains two integers:

```text id="f9m1zk"
m n
```

representing:

* number of rows
* number of columns

Next `m` lines each contain:

```text id="r2m8vx"
n space-separated integers
```

representing matrix elements.

---

# **Output Format**

Print:

```text id="n7m2qa"
all matrix elements in spiral order
```

as space-separated integers.

---

# **Constraints**

* **1 ≤ m, n ≤ 10³**
* **-10⁹ ≤ matrix[i][j] ≤ 10⁹**

---

# **Important Note**

For very large matrices:

```text id="p4m9xp"
efficient buffered output is recommended
```

to avoid slow printing performance.

---

# **Sample Input 1**

```text id="v1m8zk"
3 3
1 2 3
4 5 6
7 8 9
```

---

# **Sample Output 1**

```text id="g8m2vx"
1 2 3 6 9 8 7 4 5
```

---

# **Explanation**

Traversal order:

| Step | Direction        | Elements |
| ---- | ---------------- | -------- |
| 1    | Left → Right     | 1 2 3    |
| 2    | Top → Bottom     | 6 9      |
| 3    | Right → Left     | 8 7      |
| 4    | Bottom → Top     | 4        |
| 5    | Remaining Center | 5        |

Final spiral traversal:

```text id="x2m1qa"
1 2 3 6 9 8 7 4 5
```

---

# **Sample Input 2**

```text id="m9v2zk"
3 4
1 2 3 4
5 6 7 8
9 10 11 12
```

---

# **Sample Output 2**

```text id="k4m8qp"
1 2 3 4 8 12 11 10 9 5 6 7
```

---

# **Explanation**

Outer layer traversal:

```text id="u7m1xp"
1 2 3 4 8 12 11 10 9 5
```

Remaining inner layer:

```text id="m4k8qa"
6 7
```

---

# **Sample Input 3**

```text id="v8m2zk"
1 5
1 2 3 4 5
```

---

# **Sample Output 3**

```text id="x1m9vx"
1 2 3 4 5
```

---

# **Explanation**

Single-row matrix is traversed directly from left to right.

---

# **Sample Input 4**

```text id="z7m2qp"
4 1
1
2
3
4
```

---

# **Sample Output 4**

```text id="u4m8zk"
1 2 3 4
```

---

# **Explanation**

Single-column matrix is traversed directly from top to bottom.

---

# **Naive Simulation Approach**

Maintain:

* visited matrix
* directional movement simulation

Traverse until all cells are visited.

---

## **Complexity of Naive Simulation**

### Time Complexity

* **O(m × n)**

---

### Space Complexity

* **O(m × n)**

for visited tracking.

---

# **Optimized Boundary Traversal Approach**

Instead of tracking visited cells, maintain four moving boundaries:

| Boundary | Meaning                    |
| -------- | -------------------------- |
| `top`    | topmost unvisited row      |
| `bottom` | bottommost unvisited row   |
| `left`   | leftmost unvisited column  |
| `right`  | rightmost unvisited column |

---

# **Efficient Strategy**

While boundaries remain valid:

---

## Step 1 — Traverse Left → Right

Traverse:

```text id="k2m1qa"
matrix[top][left → right]
```

Then increment:

```text id="r7m2zk"
top
```

---

## Step 2 — Traverse Top → Bottom

Traverse:

```text id="u1m8xp"
matrix[top → bottom][right]
```

Then decrement:

```text id="m4k8qa"
right
```

---

## Step 3 — Traverse Right → Left

Only if:

```text id="v8m2zk"
top <= bottom
```

Traverse:

```text id="x1m9vx"
matrix[bottom][right → left]
```

Then decrement:

```text id="z7m2qp"
bottom
```

---

## Step 4 — Traverse Bottom → Top

Only if:

```text id="u4m8zk"
left <= right
```

Traverse:

```text id="k2m1qa"
matrix[bottom → top][left]
```

Then increment:

```text id="r7m2zk"
left
```

---

# **Why Boundary Checks Matter**

Conditions:

```text id="u1m8xp"
top <= bottom
left <= right
```

prevent duplicate traversal in:

* single-row matrices
* single-column matrices
* odd-dimension centers

---

# **Recommended Data Structures**

| Structure           | Purpose                       |
| ------------------- | ----------------------------- |
| `Array/List`        | Store spiral traversal result |
| `Integer Variables` | Boundary management           |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* single-row matrices
* single-column matrices
* square matrices
* rectangular matrices
* odd dimensions
* even dimensions
* negative numbers

---

# **Expected Complexity**

## Boundary Traversal Solution

### Time Complexity

* **O(m × n)**

Each matrix cell is visited exactly once.

---

### Space Complexity

* **O(1)** extra traversal space excluding the required output array.

---

# **Example Walkthrough**

Matrix:

```text id="m4k8qa"
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

Traversal sequence:

| Layer       | Elements        |
| ----------- | --------------- |
| Outer Layer | 1 2 3 6 9 8 7 4 |
| Inner Layer | 5               |

Final result:

```text id="v8m2zk"
1 2 3 6 9 8 7 4 5
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Direction-array simulation
* Recursive layer traversal
* Spiral Matrix II generation
* Matrix rotation relationships

---

# **Follow-Up Variants**

Interviewers may ask:

* Generate spiral matrix
* Counterclockwise traversal
* Zigzag matrix traversal
* Diagonal traversal
* Spiral traversal from center

---

# **Execution Time Limit**

**5 seconds**