# **Problem 109: Number of Islands II**

**Company:** Uber

**Category:** Union-Find (Disjoint Set Union)

**Difficulty:** Hard

---

# **Problem Description**

Uber’s geospatial infrastructure team maintains a massive dynamic map system for flood monitoring and land development analysis.

Initially, an:

```text id="m2v8zk"
m × n
```

grid contains only water cells.

Land is added dynamically over time at specific coordinates.

After every land addition, the system must efficiently determine the current number of distinct islands.

An island is formed by connecting adjacent land cells:

* vertically
* horizontally

Diagonal connections do NOT count.

Since the grid updates dynamically, repeatedly running DFS/BFS after every operation becomes too slow.

Interviewers typically expect an optimized:

```text id="x7m1qa"
Union-Find (Disjoint Set Union)
```

solution.

---

# **Task**

You are given:

* grid dimensions
* a sequence of land addition operations

After each operation:

```text id="u3m8qp"
addLand(row, col)
```

return the current number of islands.

---

# **Initial Grid State**

Initially:

```text id="f9m1zk"
all cells are water
```

represented by:

```text id="r2m8vx"
0
```

Adding land converts a cell into:

```text id="n7m2qa"
1
```

---

# **Island Definition**

Two land cells belong to the same island if they are connected:

* up
* down
* left
* right

Diagonal adjacency does NOT form an island.

---

# **Input Format**

First line contains two integers:

```text id="p4m9xp"
m n
```

representing:

* number of rows
* number of columns

Second line contains integer:

```text id="v1m8zk"
K
```

representing number of operations.

Next `K` lines each contain:

```text id="g8m2vx"
row col
```

representing a land addition operation.

---

# **Output Format**

Print:

```text id="x2m1qa"
K space-separated integers
```

where the `i-th` integer represents the number of islands after the `i-th` operation.

---

# **Constraints**

* **1 ≤ m, n ≤ 10³**
* **1 ≤ K ≤ 10⁵**
* **0 ≤ row < m**
* **0 ≤ col < n**

---

# **Sample Input 1**

```text id="m9v2zk"
3 3
4
0 0
0 1
1 2
2 1
```

---

# **Sample Output 1**

```text id="k4m8qp"
1 1 2 3
```

---

# **Explanation**

Operations:

| Operation | Grid Change                 | Islands |
| --------- | --------------------------- | ------- |
| add(0,0)  | New island formed           | 1       |
| add(0,1)  | Merges with existing island | 1       |
| add(1,2)  | New isolated island         | 2       |
| add(2,1)  | New isolated island         | 3       |

---

# **Sample Input 2**

```text id="u7m1xp"
3 3
5
0 0
0 1
1 1
1 0
0 0
```

---

# **Sample Output 2**

```text id="m4k8qa"
1 1 1 1 1
```

---

# **Explanation**

All newly added land cells eventually connect into a single island.

The last operation:

```text id="v8m2zk"
add(0,0)
```

is repeated.

Since the cell is already land:

```text id="x1m9vx"
island count does not change
```

---

# **Sample Input 3**

```text id="z7m2qp"
2 2
4
0 0
1 1
0 1
1 0
```

---

# **Sample Output 3**

```text id="u4m8zk"
1 2 1 1
```

---

# **Explanation**

Initially:

* `(0,0)` creates island #1
* `(1,1)` creates island #2

Then:

```text id="k2m1qa"
(0,1)
```

connects the previously separate islands containing:

```text id="r7m2zk"
(0,0) and (1,1)
```

forming one larger island.

---

# **Why DFS/BFS is Too Slow**

After every operation:

* recomputing islands using DFS/BFS costs:

```text id="u1m8xp"
O(m × n)
```

For:

```text id="m4k8qa"
K
```

operations, worst-case complexity becomes:

```text id="v8m2zk"
O(K × m × n)
```

which is too slow for large inputs.

---

# **Optimized Union-Find Strategy**

Treat every land cell as:

```text id="x1m9vx"
a disjoint set node
```

Each island corresponds to:

```text id="z7m2qp"
one connected component
```

---

# **Core Idea**

Whenever land is added:

1. Create a new component
2. Increase island count
3. Check 4 neighboring cells
4. If neighboring land belongs to another component:

   * union both sets
   * decrease island count

---

# **Union-Find Operations**

## Find(x)

Returns representative parent of component.

Used to determine whether two cells belong to the same island.

---

## Union(x, y)

Merges two components if parents differ.

---

# **Path Compression**

Optimize:

```text id="u4m8zk"
find()
```

by directly attaching nodes to root parent.

This significantly reduces lookup complexity.

---

# **Union by Rank / Size**

Always attach smaller tree under larger tree.

This prevents deep chains and improves efficiency.

---

# **2D to 1D Mapping**

Map cell:

```text id="k2m1qa"
(row, col)
```

to unique ID:

```text id="r7m2zk"
row * n + col
```

This allows efficient DSU implementation using arrays.

---

# **Neighbor Traversal**

Check four directions:

| Direction | Coordinate Change |
| --------- | ----------------- |
| Up        | `(-1, 0)`         |
| Down      | `(1, 0)`          |
| Left      | `(0, -1)`         |
| Right     | `(0, 1)`          |

---

# **Handling Duplicate Operations**

If:

```text id="u1m8xp"
addLand(row, col)
```

is called on an already existing land cell:

* ignore operation
* island count remains unchanged

---

# **Recommended Data Structures**

| Structure         | Purpose             |
| ----------------- | ------------------- |
| `Parent Array`    | DSU parent tracking |
| `Rank/Size Array` | Balanced unions     |
| `Grid / HashSet`  | Track land cells    |
| `Vector/List`     | Store answers       |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* duplicate land additions
* fully connected grids
* isolated cells
* single-row grids
* single-column grids
* large operation counts
* repeated unions

---

# **Expected Complexity**

## Union-Find Solution

### Time Complexity

* **O(K × α(m × n))**

Where:

* `K` = number of operations
* `α` = inverse Ackermann function

With path compression and union by rank, operations are nearly constant time.

---

### Space Complexity

* **O(m × n)**

for DSU parent arrays, rank arrays, and land tracking.

---

# **Example Walkthrough**

Grid size:

```text id="m4k8qa"
3 × 3
```

Operations:

```text id="v8m2zk"
(0,0)
(0,1)
(1,1)
```

---

## Step 1

Add:

```text id="x1m9vx"
(0,0)
```

Islands:

```text id="z7m2qp"
1
```

---

## Step 2

Add:

```text id="u4m8zk"
(0,1)
```

Adjacent to `(0,0)`.

Union both cells.

Islands remain:

```text id="k2m1qa"
1
```

---

## Step 3

Add:

```text id="r7m2zk"
(1,1)
```

Adjacent to `(0,1)`.

Union again.

Final islands:

```text id="u1m8xp"
1
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* BFS recomputation approach
* Dynamic graph connectivity
* Offline connectivity queries
* Sparse DSU optimization using HashMaps

---

# **Follow-Up Variants**

Interviewers may ask:

* Maximum island size after operations
* Remove land operations
* 8-direction connectivity
* Dynamic bridge counting
* Online connectivity queries

---

# **Execution Time Limit**

**8 seconds**