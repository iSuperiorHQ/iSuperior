# **Problem 108: Number of Islands**

**Company:** Uber

**Category:** Depth-First Search (Matrix Traversal)

**Difficulty:** Medium

---

# **Problem Description**

Uber’s geospatial analytics system processes large satellite maps represented as 2D grids.

Each cell in the grid represents either:

* land
* water

Connected land regions form islands.

Your task is to determine how many distinct islands exist in the grid.

An island is formed by connecting adjacent land cells:

* vertically
* horizontally

Diagonal connections do NOT count.

This is a classic:

```text id="m2v8zk"
graph traversal problem
```

commonly solved using:

```text id="x7m1qa"
Depth-First Search (DFS)
```

or:

```text id="u3m8qp"
Breadth-First Search (BFS)
```

on matrices.

---

# **Task**

Given an:

```text id="f9m1zk"
m × n
```

grid consisting of:

```text id="r2m8vx"
'1'
```

and:

```text id="n7m2qa"
'0'
```

characters:

* `'1'` represents land
* `'0'` represents water

Return the total number of islands.

---

# **Island Definition**

Two land cells belong to the same island if they are connected:

* up
* down
* left
* right

Diagonal connections are NOT considered connected.

---

# **Input Format**

First line contains two integers:

```text id="p4m9xp"
m n
```

representing:

* number of rows
* number of columns

Next `m` lines each contain a binary string of length:

```text id="v1m8zk"
n
```

representing the grid.

---

# **Output Format**

Print a single integer representing:

```text id="g8m2vx"
number of islands
```

---

# **Constraints**

* **1 ≤ m, n ≤ 1000**
* Grid contains only:

```text id="x2m1qa"
'0' and '1'
```

---

# **Important Note**

For very large grids:

```text id="m9v2zk"
iterative DFS or BFS may be preferred
```

to avoid recursion depth limitations and stack overflow.

---

# **Sample Input 1**

```text id="k4m8qp"
4 5
11000
11000
00100
00011
```

---

# **Sample Output 1**

```text id="u7m1xp"
3
```

---

# **Explanation**

Grid contains:

1. Top-left island
2. Middle isolated island
3. Bottom-right island

Thus total islands:

```text id="m4k8qa"
3
```

---

# **Sample Input 2**

```text id="v8m2zk"
3 3
111
010
111
```

---

# **Sample Output 2**

```text id="x1m9vx"
1
```

---

# **Explanation**

All land cells are connected horizontally or vertically.

Thus entire grid forms:

```text id="z7m2qp"
one island
```

---

# **Sample Input 3**

```text id="u4m8zk"
3 4
0000
0000
0000
```

---

# **Sample Output 3**

```text id="k2m1qa"
0
```

---

# **Explanation**

No land cells exist.

---

# **Sample Input 4**

```text id="r7m2zk"
5 5
10101
01010
10101
01010
10101
```

---

# **Sample Output 4**

```text id="u1m8xp"
13
```

---

# **Explanation**

No land cell shares a horizontal or vertical neighbor with another land cell.

Thus every:

```text id="m4k8qa"
'1'
```

forms its own island.

---

# **Graph Interpretation**

Treat each land cell as:

```text id="v8m2zk"
a graph node
```

Edges exist between adjacent land cells.

Each connected component corresponds to:

```text id="x1m9vx"
one island
```

---

# **Core Insight**

Whenever an unvisited land cell is found:

1. A new island is discovered
2. Perform DFS/BFS to mark all connected land cells
3. Continue scanning remaining grid

---

# **Efficient DFS Strategy**

Traverse entire grid.

For every cell:

---

## If Cell is Water

Skip.

---

## If Cell is Unvisited Land

1. Increment island count
2. Run DFS from current cell
3. Mark all connected land as visited

---

# **DFS Traversal Directions**

Use four directions:

| Direction | Coordinate Change |
| --------- | ----------------- |
| Up        | `(-1, 0)`         |
| Down      | `(1, 0)`          |
| Left      | `(0, -1)`         |
| Right     | `(0, 1)`          |

---

# **Visited Marking Techniques**

You may either:

* maintain separate visited matrix

OR

* modify grid in-place by converting:

```text id="z7m2qp"
'1' → '0'
```

after visiting.

---

# **Why DFS Works**

DFS completely explores one connected component before moving to another.

Thus each DFS traversal identifies exactly:

```text id="u4m8zk"
one island
```

---

# **Recommended Data Structures**

| Structure                 | Purpose                |
| ------------------------- | ---------------------- |
| `2D Grid`                 | Input matrix           |
| `Recursion Stack / Stack` | DFS traversal          |
| `Queue`                   | Optional BFS traversal |
| `Visited Matrix`          | Track explored cells   |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* empty grids
* all water
* all land
* single-row grids
* single-column grids
* isolated cells
* large connected islands

---

# **Recursive DFS Pseudocode**

```text id="k2m1qa"
dfs(row, col):
    if out of bounds:
        return

    if grid[row][col] == '0':
        return

    mark current cell visited

    dfs(up)
    dfs(down)
    dfs(left)
    dfs(right)
```

---

# **Expected Complexity**

## DFS / BFS Solution

### Time Complexity

* **O(m × n)**

Each cell is visited at most once.

---

### Space Complexity

* **O(m × n)** worst-case space

due to recursion stack and/or visited tracking.

---

# **Example Walkthrough**

Grid:

```text id="r7m2zk"
110
010
011
```

Traversal:

| Step            | Action                    |
| --------------- | ------------------------- |
| (0,0)           | Start Island #1           |
| DFS             | Visits all connected land |
| Remaining Cells | Already visited           |

Total islands:

```text id="u1m8xp"
1
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* BFS traversal
* Union-Find (Disjoint Set Union)
* Iterative DFS using stack
* Connected component labeling

---

# **Follow-Up Variants**

Interviewers may ask:

* Maximum island area
* Number of distinct island shapes
* Dynamic island additions
* Shortest bridge between islands
* Counting diagonal islands

---

# **Execution Time Limit**

**5 seconds**