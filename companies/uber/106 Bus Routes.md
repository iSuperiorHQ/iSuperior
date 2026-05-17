# **Problem 106: Bus Routes**

**Company:** Uber

**Category:** Breadth-First Search (Graph)

**Difficulty:** Hard

---

# **Problem Description**

Uber’s urban transit team manages a large network of interconnected bus routes across multiple cities.

Each bus route operates in a cyclic manner and visits a predefined sequence of bus stops repeatedly.

Passengers may:

* board a bus at any stop on its route
* travel through all stops served by that route
* switch buses at common stops shared by multiple routes

Your task is to determine the minimum number of buses required to travel from a given source stop to a target stop.

This is a classic:

```text id="m2v8zk"
graph shortest path problem
```

commonly solved using:

```text id="x7m1qa"
Breadth-First Search (BFS)
```

---

# **Task**

You are given:

* a list of bus routes
* a source stop
* a target stop

Return the minimum number of buses needed to travel from:

```text id="u3m8qp"
source
```

to:

```text id="f9m1zk"
target
```

If the destination cannot be reached, return:

```text id="r2m8vx"
-1
```

---

# **Important Rules**

* Each route repeats infinitely in a cycle

* You may travel between any stops belonging to the same route

* Switching buses is allowed only at common stops

* Boarding the first bus counts as:

```text id="n7m2qa"
1 bus
```

* If:

```text id="p4m9xp"
source == target
```

answer is:

```text id="v1m8zk"
0
```

because no travel is needed.

---

# **Input Format**

First line contains integer:

```text id="g8m2vx"
N
```

representing number of bus routes.

Next `N` lines contain:

```text id="x2m1qa"
k stop1 stop2 stop3 ...
```

Where:

* `k` = number of stops in the route
* remaining integers represent bus stops

Last line contains:

```text id="m9v2zk"
source target
```

---

# **Output Format**

Print a single integer representing:

```text id="k4m8qp"
minimum buses required
```

to reach destination.

If destination is unreachable, print:

```text id="u7m1xp"
-1
```

---

# **Constraints**

* **1 ≤ N ≤ 500**
* **1 ≤ Total Stops Across All Routes ≤ 10⁵**
* **0 ≤ stopId ≤ 10⁶**

---

# **Sample Input 1**

```text id="m4k8qa"
2
3 1 2 7
3 3 6 7
1 6
```

---

# **Sample Output 1**

```text id="v8m2zk"
2
```

---

# **Explanation**

Route 1:

```text id="x1m9vx"
1 → 2 → 7
```

Route 2:

```text id="z7m2qp"
3 → 6 → 7
```

Passenger:

1. Boards Route 1 at stop:

```text id="u4m8zk"
1
```

2. Travels to shared stop:

```text id="k2m1qa"
7
```

3. Switches to Route 2
4. Reaches stop:

```text id="r7m2zk"
6
```

Total buses used:

```text id="u1m8xp"
2
```

---

# **Sample Input 2**

```text id="m4k8qa"
3
4 1 5 7 9
4 9 10 11 12
3 12 13 14
1 14
```

---

# **Sample Output 2**

```text id="v8m2zk"
3
```

---

# **Explanation**

Optimal path:

| Bus Route | Stops Used |
| --------- | ---------- |
| Route 1   | 1 → 9      |
| Route 2   | 9 → 12     |
| Route 3   | 12 → 14    |

Thus:

```text id="x1m9vx"
3 buses
```

are required.

---

# **Sample Input 3**

```text id="z7m2qp"
2
3 1 2 3
3 4 5 6
1 6
```

---

# **Sample Output 3**

```text id="u4m8zk"
-1
```

---

# **Explanation**

No shared stops exist between routes.

Destination cannot be reached.

---

# **Sample Input 4**

```text id="k2m1qa"
2
3 1 2 3
3 3 4 5
3 3
```

---

# **Sample Output 4**

```text id="r7m2zk"
0
```

---

# **Explanation**

Source and target are identical.

No bus is needed.

---

# **Graph Interpretation**

This problem can be modeled as a graph:

| Entity                    | Graph Representation |
| ------------------------- | -------------------- |
| Bus stop                  | Node                 |
| Shared route connectivity | Edges                |

BFS guarantees the minimum number of bus transfers.

---

# **Efficient BFS Strategy**

## Step 1 — Build Stop-to-Route Mapping

Create:

```text id="u1m8xp"
stop → list of routes
```

mapping.

This enables efficient route transitions.

---

# **Step 2 — BFS Traversal**

Start BFS from:

```text id="m4k8qa"
source stop
```

At every step:

1. Explore all routes passing through current stop
2. Traverse all stops in those routes
3. Push newly discovered stops into queue
4. Count bus transfers level-by-level

---

# **Visited Tracking**

To avoid repeated processing:

---

## Visited Stops

Prevent revisiting stops.

---

## Visited Routes

Prevent reprocessing entire routes repeatedly.

This optimization is crucial for achieving near-linear complexity.

---

# **Recommended Data Structures**

| Structure | Purpose               |
| --------- | --------------------- |
| `HashMap` | Stop → routes mapping |
| `Queue`   | BFS traversal         |
| `HashSet` | Visited stops         |
| `HashSet` | Visited routes        |

---

# **Why BFS Works**

BFS explores routes level-by-level.

Each BFS level corresponds to:

```text id="v8m2zk"
taking one additional bus
```

Thus the first time target is reached gives the minimum buses required.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* source equals target
* disconnected routes
* circular routes
* repeated stops inside routes
* multiple optimal paths
* isolated stops
* very large transit networks

---

# **Expected Complexity**

## Optimized BFS Solution

### Time Complexity

* **O(R + S)**

Where:

* `R` = number of routes
* `S` = total stop occurrences across all routes

Each route and stop occurrence is processed at most once.

---

### Space Complexity

* **O(R + S)**

Where:

* `R` = number of routes
* `S` = total stop occurrences across all routes

Additional space is used for:

* BFS queue
* visited sets
* stop-to-route mapping

---

# **Example Walkthrough**

Routes:

```text id="x1m9vx"
Route 1 → [1, 2, 7]
Route 2 → [3, 6, 7]
```

Source:

```text id="z7m2qp"
1
```

Target:

```text id="u4m8zk"
6
```

---

## BFS Levels

| Level | Reachable Stops | Buses Used |
| ----- | --------------- | ---------- |
| 0     | 1               | 0          |
| 1     | 2, 7            | 1          |
| 2     | 3, 6            | 2          |

Target:

```text id="k2m1qa"
6
```

reached using:

```text id="r7m2zk"
2 buses
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Route graph BFS
* Bidirectional BFS
* Multi-source BFS
* Union-Find connectivity checks

---

# **Follow-Up Variants**

Interviewers may ask:

* Return actual route sequence
* Minimize travel time instead of buses
* Weighted route switching costs
* Real-time dynamic route updates
* Multi-modal transport systems

---

# **Execution Time Limit**

**8 seconds**