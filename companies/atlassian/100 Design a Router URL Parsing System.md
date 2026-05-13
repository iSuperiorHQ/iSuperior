# **Problem 100: Design a Router / URL Parsing System**

**Company:** Atlassian

**Category:** Low-Level Design (LLD) / Machine Coding

**Difficulty:** Hard

---

# **Problem Description**

A backend API gateway service must efficiently route incoming HTTP requests to their corresponding handlers.

Modern routing systems support:

* static routes
* dynamic path parameters
* nested URL hierarchies
* fast lookup performance
* path normalization
* conflict resolution

Your task is to design and implement a trie-based URL routing engine capable of:

* registering API routes
* parsing incoming URL paths
* extracting dynamic parameters
* resolving correct handlers efficiently

The implementation should be modular, object-oriented, scalable, and optimized for real-time request routing.

---

# **Functional Requirements**

The routing system should support:

* adding routes dynamically
* static route matching
* parameterized route matching
* nested route traversal
* efficient URL lookup
* path parameter extraction
* invalid route handling

---

# **Route Definitions**

A route may contain:

## Static Segments

Example:

```text id="m2v8zk"
/api/users/list
```

---

## Dynamic Parameters

Dynamic segments begin with:

```text id="x7m1qa"
:
```

Example:

```text id="u3m8qp"
/api/users/:id
```

For incoming path:

```text id="f9m1zk"
/api/users/42
```

parameter mapping becomes:

```text id="r2m8vx"
id → 42
```

---

# **Routing Rules**

## Exact Static Match Has Higher Priority

If both routes exist:

```text id="n7m2qa"
/api/users/list
/api/users/:id
```

then incoming request:

```text id="p4m9xp"
/api/users/list
```

must match:

```text id="v1m8zk"
/api/users/list
```

instead of dynamic route.

---

## Parameter Matching

Dynamic parameters match exactly one path segment.

Example:

```text id="g8m2vx"
/users/:id
```

matches:

```text id="x2m1qa"
/users/100
```

but does NOT match:

```text id="m9v2zk"
/users/100/orders
```

---

## Path Normalization

Trailing slashes should be ignored.

Example:

```text id="k4m8qp"
/api/users/
/api/users
```

should be treated identically.

---

## Duplicate Route Registration

If a route already exists:

```text id="u7m1xp"
its handler should be updated
```

with the latest registered handler.

---

# **Task**

Design a router supporting:

| Operation                 | Description                |
| ------------------------- | -------------------------- |
| `addRoute(path, handler)` | Register route             |
| `match(path)`             | Resolve incoming request   |
| `removeRoute(path)`       | Delete existing route      |
| `getParams(path)`         | Extract dynamic parameters |

---

# **Input Format**

First line contains integer:

```text id="m4k8qa"
Q
```

representing total operations.

Next `Q` lines contain one of the following commands:

---

## Add Route

```text id="v8m2zk"
ADD route handlerName
```

Example:

```text id="x1m9vx"
ADD /api/users/:id getUserHandler
```

---

## Match Route

```text id="z7m2qp"
MATCH path
```

---

## Remove Route

```text id="u4m8zk"
REMOVE route
```

---

# **Output Format**

For every:

```text id="k2m1qa"
MATCH
```

operation print:

---

## Successful Match

```text id="r7m2zk"
handlerName param1=value1 param2=value2
```

Parameters should be printed in traversal order.

---

## Failed Match

Print:

```text id="u1m8xp"
NOT FOUND
```

---

# **Constraints**

* **1 ≤ Q ≤ 10⁵**
* Total path length across all operations ≤ `10⁶`
* Path depth ≤ `100`
* Handler names contain only alphanumeric characters

---

# **Sample Input 1**

```text id="m4k8qa"
7
ADD /api/users/:id getUser
ADD /api/users/list getUserList
MATCH /api/users/42
MATCH /api/users/list
REMOVE /api/users/:id
MATCH /api/users/42
MATCH /api/users/list
```

---

# **Sample Output 1**

```text id="v8m2zk"
getUser id=42
getUserList
NOT FOUND
getUserList
```

---

# **Explanation**

Dynamic route:

```text id="x1m9vx"
/api/users/:id
```

matches:

```text id="z7m2qp"
/api/users/42
```

and extracts:

```text id="u4m8zk"
id = 42
```

Static route:

```text id="k2m1qa"
/api/users/list
```

takes precedence over parameterized route.

After removal:

```text id="r7m2zk"
/api/users/:id
```

no longer resolves requests.

---

# **Sample Input 2**

```text id="u1m8xp"
8
ADD /products/:category/:id getProduct
MATCH /products/books/100
MATCH /products/electronics/55
ADD /products/list getProductList
MATCH /products/list
REMOVE /products/list
MATCH /products/list
MATCH /products/books
```

---

# **Sample Output 2**

```text id="m4k8qa"
getProduct category=books id=100
getProduct category=electronics id=55
getProductList
NOT FOUND
NOT FOUND
```

---

# **Explanation**

Parameterized route:

```text id="v8m2zk"
/products/:category/:id
```

matches multiple incoming paths.

Static route:

```text id="x1m9vx"
/products/list
```

takes precedence when present.

After removing static route:

```text id="z7m2qp"
/products/list
```

no longer matches because the parameterized route requires:

```text id="u4m8zk"
two dynamic segments
```

after:

```text id="k2m1qa"
/products
```

---

# **Sample Input 3**

```text id="r7m2zk"
6
ADD /home getHome
MATCH /home/
MATCH /home
REMOVE /home
MATCH /home
MATCH /
```

---

# **Sample Output 3**

```text id="u1m8xp"
getHome
getHome
NOT FOUND
NOT FOUND
```

---

# **Explanation**

Trailing slash normalization ensures:

```text id="m4k8qa"
/home/
/home
```

behave identically.

After route removal:

```text id="v8m2zk"
/home
```

no longer exists.

---

# **Recommended Data Structures**

| Structure     | Purpose                    |
| ------------- | -------------------------- |
| `Trie`        | Hierarchical route storage |
| `HashMap`     | Child route lookup         |
| `Node`        | Represents route segment   |
| `Vector/List` | Parameter extraction       |

---

# **Object-Oriented Design Expectations**

Recommended classes:

| Class              | Responsibility              |
| ------------------ | --------------------------- |
| `Router`           | Main routing engine         |
| `RouteTrie`        | Trie management             |
| `TrieNode`         | Stores route segment        |
| `RouteMatchResult` | Encapsulates match response |
| `PathParser`       | Splits and normalizes URLs  |

---

# **Efficient Strategy**

For every route:

1. Normalize path
2. Split path by:

```text id="x1m9vx"
/
```

3. Insert segments into trie
4. Mark terminal handler node

During matching:

1. Prefer exact static child
2. Otherwise try parameter child
3. Store extracted parameters
4. Return matched handler

---

# **Important Edge Cases**

Your implementation should correctly handle:

* overlapping routes
* duplicate route registration
* trailing slashes
* empty root paths
* deep nested routes
* parameter conflicts
* removing non-existent routes

---

# **Expected Complexity**

## Trie-Based Routing Design

### addRoute / removeRoute / match

* **Time Complexity:** `O(P)`

Where:

* `P` = number of path segments

---

### Parameter Extraction

* **Time Complexity:** `O(P)`

---

### Space Complexity

* **O(N)**

Where:

* `N` = total route segments stored in trie

---

# **Scalability Discussion**

Expected interview discussion points:

* compressed tries (Radix Trees)
* HTTP method-specific routing
* middleware chaining
* regex-based route matching
* distributed API gateways
* route caching strategies

---

# **Bonus Follow-Up Questions**

Interviewers may ask:

* How would you support wildcard routes?
* How would you handle route versioning?
* How would you optimize memory usage?
* How would you implement middleware execution?
* How would you support query parameter parsing?

---

# **Execution Time Limit**

**10 seconds**