# Problem 125: Clone Graph

**Company:** Uber  

**Category:** Graphs / Graph Traversal  

**Difficulty:** Hard  

---

# Problem Description

A distributed ride-sharing platform internally represents road connectivity, service regions, and routing dependencies using graph-based structures.

To safely run simulations without mutating production graph data, engineers must create a deep copy of an existing graph.

You are given a reference to a node in a connected undirected graph.

Your task is to create an exact deep clone of the entire graph such that:

- every node is duplicated  
- every edge relationship is preserved  
- cloned nodes do not share memory references with original nodes  

Efficient solutions require candidates to:

- traverse graphs using BFS or DFS  
- avoid infinite traversal in cyclic graphs  
- maintain a mapping between original and cloned nodes  
- correctly recreate adjacency relationships  

This problem evaluates a candidate’s understanding of:

- graph traversal  
- cycle handling  
- hash map state tracking  
- deep-copy semantics  
- adjacency reconstruction  

Interviewers typically expect an:

- **O(V + E)**

time solution.

---

# Graph Definition

Each graph node contains:

| Field | Description |
|---|---|
| `val` | Unique integer identifier |
| `neighbors` | List of adjacent graph nodes |

Example node structure:

```cpp
class Node {
public:
    int val;
    vector<Node*> neighbors;
};
```

---

# Task

Given a reference to a node in an undirected connected graph, return the reference to the cloned graph.

The cloned graph must:

- preserve all connections  
- contain completely new node instances  
- replicate the original graph structure exactly  

---

# Important Rules

- The graph may contain cycles  
- The graph may contain self-loops  
- Every node value is unique  
- The graph is connected  
- The returned graph must be a deep copy  
- Original nodes and cloned nodes must not share references  

---

# Input Representation

The graph is represented using adjacency lists.

First line contains integer:

```text
N
```

representing the number of nodes.

Next:

```text
N
```

lines describe graph connectivity.

Each line follows the format:

```text
node neighborCount neighbor1 neighbor2 ...
```

where:

- `node` = current node value  
- `neighborCount` = total adjacent nodes  
- remaining integers represent neighboring node values  

---

# Output Format

Print the cloned graph using the same adjacency-list format.

For evaluation purposes, preserve the input node ordering in the output.

---

# Constraints

- **1 ≤ N ≤ 10^4**
- **0 ≤ E ≤ 2 × 10^4**
- **1 ≤ Node Value ≤ 10^5**

---

# Sample Input 1

```text
4
1 2 2 4
2 2 1 3
3 2 2 4
4 2 1 3
```

---

# Sample Output 1

```text
1 2 2 4
2 2 1 3
3 2 2 4
4 2 1 3
```

---

# Explanation

Original graph:

```text
1 -- 2
|    |
4 -- 3
```

The cloned graph preserves:

- all node values  
- all bidirectional edges  
- graph structure  

while creating entirely new node instances.

---

# Sample Input 2

```text
1
1 0
```

---

# Sample Output 2

```text
1 0
```

---

# Explanation

Graph contains only one isolated node with no neighbors.

The cloned graph contains exactly one independent node.

---

# Sample Input 3

```text
3
1 1 2
2 2 1 3
3 1 2
```

---

# Sample Output 3

```text
1 1 2
2 2 1 3
3 1 2
```

---

# Explanation

The graph forms a simple linear chain:

```text
1 -- 2 -- 3
```

The cloned graph preserves all connectivity.

---

# Sample Input 4

```text
2
1 2 1 2
2 1 1
```

---

# Sample Output 4

```text
1 2 1 2
2 1 1
```

---

# Explanation

Node:

```text
1
```

contains:

- a self-loop to itself  
- an edge to node:
  
```text
2
```

The cloned graph must preserve both relationships correctly.

---

# Why Naive Approaches Fail

A recursive copy without visited tracking may:

- infinitely traverse cycles  
- duplicate nodes multiple times  
- corrupt adjacency relationships  

Graphs with cycles require state tracking during traversal.

---

# Key Observation

Each original node must map to exactly one cloned node.

This requires maintaining a state map between:

| Original Node | Cloned Node |
|---|---|
| Original reference | Deep-copy reference |

---

# Optimized Graph Traversal Strategy

The optimal solution uses:

- BFS or DFS traversal  
- hash map node tracking  
- adjacency reconstruction  

---

# Algorithm Overview

## Step 1 — Create State Map

Maintain hash map:

```text
originalNode → clonedNode
```

This prevents:

- duplicate cloning  
- infinite traversal in cycles  

---

## Step 2 — Start Graph Traversal

Use either:

- Breadth-First Search (BFS)  
OR
- Depth-First Search (DFS)

starting from the given node.

---

## Step 3 — Clone Neighbor Nodes

For every neighbor:

- if not cloned:
  
```text
create new clone
```

- store in state map  
- continue traversal  

---

## Step 4 — Rebuild Adjacency List

For every edge:

```text
original → neighbor
```

add corresponding edge:

```text
clone → clonedNeighbor
```

---

# Why This Works

The state map guarantees:

- every node is cloned exactly once  
- cycles are handled safely  
- adjacency structure remains consistent  

Traversal ensures all reachable nodes are reconstructed.

---

# Recommended Data Structures

| Structure | Purpose |
|---|---|
| `Queue / Stack` | BFS or DFS traversal |
| `Hash Map` | Original-to-clone mapping |
| `Adjacency Lists` | Graph connectivity |

---

# Important Edge Cases

Your implementation should correctly handle:

- single-node graphs  
- cyclic graphs  
- self-loops  
- dense graphs  
- sparse graphs  
- graphs containing repeated traversal paths  

---

# Expected Complexity

## Optimized BFS/DFS Clone Solution

### Time Complexity

- **O(V + E)**

Every node and edge is processed exactly once.

---

### Auxiliary Space Complexity

- **O(V)**

Traversal queue/stack and hash map store graph nodes.

---

### Total Graph Storage Complexity

- **O(V + E)**

The cloned graph stores all cloned nodes and adjacency relationships.

---

# Example Walkthrough

Input graph:

```text
1 -- 2
|    |
4 -- 3
```

---

## Start Traversal

Clone node:

```text
1
```

Store mapping:

| Original | Clone |
|---|---|
| 1 | clone(1) |

---

## Visit Neighbors

Neighbors:

```text
2, 4
```

Clone both and store mappings.

---

## Continue Traversal

Process:

```text
2
```

then:

```text
3
```

then:

```text
4
```

while rebuilding adjacency connections.

---

## Final Cloned Graph

```text
1 -- 2
|    |
4 -- 3
```

All nodes are newly allocated objects.

---

# Alternative Approaches

Interviewers may also discuss:

- recursive DFS cloning  
- iterative BFS cloning  
- serialization/deserialization cloning  
- graph copy validation  

---

# Follow-Up Variants

Interviewers may ask:

- Clone directed graphs  
- Clone disconnected graphs  
- Clone weighted graphs  
- Clone graphs with random pointers  
- Verify graph equality after cloning  

---

# Execution Time Limit

**4 seconds**