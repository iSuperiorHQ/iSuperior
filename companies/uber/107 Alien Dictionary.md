# **Problem 107: Alien Dictionary**

**Company:** Uber

**Category:** Graph / Topological Sort (Kahn’s Algorithm)

**Difficulty:** Hard

---

# **Problem Description**

Uber’s language intelligence team is building a translation engine for a newly discovered alien civilization.

The alien language uses the English lowercase alphabet:

```text id="m2v8zk"
a-z
```

but the character ordering is completely unknown.

You are given a dictionary of words already sorted according to the alien language rules.

Your task is to determine a valid ordering of characters in the alien alphabet.

This problem is a classic:

```text id="x7m1qa"
Topological Sorting
```

problem on a directed graph.

Interviewers typically expect an optimized:

```text id="u3m8qp"
Kahn’s Algorithm (BFS Topological Sort)
```

solution with:

* graph construction
* indegree tracking
* cycle detection

---

# **Task**

Given a sorted list of alien words:

```text id="f9m1zk"
words
```

return a valid ordering of characters in the alien language.

If:

* no valid ordering exists
* contradictory rules are detected
* cyclic dependencies occur

return:

```text id="r2m8vx"
INVALID
```

---

# **Important Rules**

* Words are already sorted lexicographically according to the alien language
* Character ordering must satisfy all inferred precedence constraints
* Multiple valid answers may exist
* Return any valid ordering
* All unique characters appearing in input must appear in output

---

# **Input Format**

First line contains integer:

```text id="n7m2qa"
N
```

representing number of words.

Next `N` lines contain one alien word each.

---

# **Output Format**

Print:

* a valid alien character ordering

OR

```text id="p4m9xp"
INVALID
```

if no valid ordering exists.

---

# **Constraints**

* **1 ≤ N ≤ 10⁴**
* **1 ≤ word length ≤ 100**
* Words contain only lowercase English letters
* Total characters across all words ≤ `10⁵`

---

# **Sample Input 1**

```text id="v1m8zk"
5
wrt
wrf
er
ett
rftt
```

---

# **Sample Output 1**

```text id="g8m2vx"
wertf
```

---

# **Explanation**

Compare adjacent words:

| Word 1 | Word 2 | First Different Character | Rule  |
| ------ | ------ | ------------------------- | ----- |
| wrt    | wrf    | t vs f                    | t → f |
| wrf    | er     | w vs e                    | w → e |
| er     | ett    | r vs t                    | r → t |
| ett    | rftt   | e vs r                    | e → r |

Combined ordering:

```text id="x2m1qa"
w → e → r → t → f
```

Result:

```text id="m9v2zk"
wertf
```

---

# **Sample Input 2**

```text id="k4m8qp"
2
z
x
```

---

# **Sample Output 2**

```text id="u7m1xp"
zx
```

---

# **Explanation**

From:

```text id="m4k8qa"
z
x
```

we infer:

```text id="v8m2zk"
z → x
```

Thus one valid ordering is:

```text id="x1m9vx"
zx
```

---

# **Sample Input 3**

```text id="z7m2qp"
4
z
x
x
z
```

---

# **Sample Output 3**

```text id="u4m8zk"
INVALID
```

---

# **Explanation**

Rules inferred:

```text id="k2m1qa"
z → x
x → z
```

This creates a cycle.

Thus no valid ordering exists.

---

# **Sample Input 4**

```text id="r7m2zk"
2
abc
ab
```

---

# **Sample Output 4**

```text id="u1m8xp"
INVALID
```

---

# **Explanation**

A longer word appearing before its own prefix is invalid.

Because:

```text id="m4k8qa"
abc
```

cannot come before:

```text id="v8m2zk"
ab
```

in lexicographical ordering.

---

# **Graph Interpretation**

Each character represents:

```text id="x1m9vx"
a graph node
```

Directed edge:

```text id="z7m2qp"
u → v
```

means:

```text id="u4m8zk"
u appears before v
```

in alien ordering.

---

# **How Constraints Are Derived**

Compare adjacent words.

Find the first differing character.

Example:

```text id="k2m1qa"
abcd
abef
```

First mismatch:

```text id="r7m2zk"
c vs e
```

Thus infer:

```text id="u1m8xp"
c → e
```

Only the first differing character matters.

---

# **Efficient Strategy — Kahn’s Algorithm**

---

## Step 1 — Initialize Graph

Create:

* adjacency list
* indegree array/map

for all unique characters.

---

## Step 2 — Build Directed Edges

For every adjacent word pair:

1. Find first differing character
2. Add directed edge
3. Increment indegree

---

## Step 3 — Detect Prefix Invalidity

If:

```text id="m4k8qa"
word1.length > word2.length
```

AND:

```text id="v8m2zk"
word1 startsWith(word2)
```

then ordering is invalid.

---

## Step 4 — Perform BFS Topological Sort

Push all characters having:

```text id="x1m9vx"
indegree = 0
```

into queue.

Repeatedly:

1. Pop character
2. Add to result
3. Reduce indegree of neighbors
4. Push newly unlocked nodes

---

# **Cycle Detection**

After BFS:

If processed character count is smaller than total unique characters:

```text id="z7m2qp"
a cycle exists
```

Thus return:

```text id="u4m8zk"
INVALID
```

---

# **Why Kahn’s Algorithm Works**

Topological sorting guarantees:

* precedence rules are satisfied
* characters appear after dependencies
* cycle detection becomes straightforward

---

# **Recommended Data Structures**

| Structure                             | Purpose                 |
| ------------------------------------- | ----------------------- |
| `HashMap<Character, List<Character>>` | Graph adjacency list    |
| `HashMap<Character, Integer>`         | Indegree tracking       |
| `Queue`                               | BFS processing          |
| `HashSet`                             | Prevent duplicate edges |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* disconnected characters
* multiple valid orderings
* cyclic dependencies
* repeated words
* prefix invalidity
* single-character words
* isolated characters

---

# **Expected Complexity**

## Kahn’s Topological Sort Solution

### Time Complexity

* **O(C + V + E)**

Where:

* `C` = total characters across all words
* `V` = number of unique characters
* `E` = number of precedence relations

Graph construction processes all characters once, while BFS processes every node and edge at most once.

---

### Space Complexity

* **O(V + E)**

for adjacency list, indegree map, and BFS queue.

---

# **Example Walkthrough**

Words:

```text id="k2m1qa"
["wrt","wrf","er","ett","rftt"]
```

Derived graph:

```text id="r7m2zk"
w → e
e → r
r → t
t → f
```

Indegrees:

| Character | Indegree |
| --------- | -------- |
| w         | 0        |
| e         | 1        |
| r         | 1        |
| t         | 1        |
| f         | 1        |

BFS order:

```text id="u1m8xp"
w → e → r → t → f
```

Final result:

```text id="m4k8qa"
wertf
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* DFS-based Topological Sort
* Cycle detection using DFS coloring
* Lexicographically smallest ordering
* Graph compression optimizations

---

# **Follow-Up Variants**

Interviewers may ask:

* Return lexicographically smallest valid ordering
* Detect all possible orderings
* Dynamic dictionary updates
* Streaming alien words
* Unicode character support

---

# **Execution Time Limit**

**8 seconds**