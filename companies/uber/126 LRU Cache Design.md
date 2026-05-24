# Problem 126: LRU Cache Design

**Company:** Uber  

**Category:** System Design / Data Structures  

**Difficulty:** Hard  

---

# Problem Description

Modern ride-sharing platforms process millions of real-time requests involving:

- route calculations  
- surge pricing lookups  
- driver-region mappings  
- frequently accessed trip metadata  

Repeated database access for recently queried information significantly increases latency.

To optimize performance, Uber engineers deploy an:

```text
LRU (Least Recently Used) Cache
```

that stores recently accessed entries and automatically evicts stale data when memory capacity is exceeded.

Your task is to design and implement an LRU Cache supporting:

- constant-time retrieval  
- constant-time insertion/update  
- automatic least-recently-used eviction  

Efficient solutions require candidates to combine:

- hash-based indexing  
- doubly linked list ordering  

This problem evaluates a candidate’s understanding of:

- cache eviction policies  
- pointer manipulation  
- hybrid data structures  
- state synchronization  
- constant-time design guarantees  

Interviewers expect:

- **O(1)** average time complexity for both:
  
```text
get()
```

and:

```text
put()
```

operations.

Assume hash map operations execute in average:

- **O(1)**

time complexity.

---

# Task

Design a data structure:

```text
LRUCache
```

that supports the following operations:

| Operation | Description |
|---|---|
| `get(key)` | Return value associated with key |
| `put(key, value)` | Insert or update key-value pair |

---

# LRU Policy Rules

The cache follows the:

```text
Least Recently Used
```

eviction strategy.

This means:

- whenever a key is accessed using:
  
```text
get()
```

it becomes the:

```text
most recently used
```

item

- whenever:
  
```text
put()
```

updates or inserts a key, that key also becomes:

```text
most recently used
```

- if cache capacity is exceeded:
  
```text
least recently used
```

entry must be removed automatically

---

# Cache Ordering Convention

Throughout the problem statement, cache order is represented as:

```text
[LRU → MRU]
```

where:

- left side = least recently used item  
- right side = most recently used item  

In the doubly linked list:

- head stores the:
  
```text
MRU
```

item

- tail stores the:
  
```text
LRU
```

item

---

# Required Operations

## get(key)

Return:

- associated value if key exists  
- otherwise:
  
```text
-1
```

Accessing a key marks it as recently used.

---

## put(key, value)

Insert or update the key-value pair.

If insertion exceeds cache capacity:

- evict the least recently used key  

Updating an existing key should:

- update its value  
- move it to most recently used position  
- NOT increase cache size

---

# Important Constraints

- Both:
  
```text
get()
```

and:

```text
put()
```

must execute in:

- **O(1)** average time complexity

- Built-in ordered map structures are NOT allowed  
- Manual pointer manipulation is expected  
- Cache ordering must update dynamically after every operation  

---

# Input Format

First line contains integer:

```text
capacity
```

representing maximum cache size.

Second line contains integer:

```text
Q
```

representing number of operations.

Next:

```text
Q
```

lines contain operations in one of the following formats:

## Get Operation

```text
GET key
```

## Put Operation

```text
PUT key value
```

---

# Output Format

For every:

```text
GET
```

operation print the returned value.

---

# Constraints

- **1 ≤ capacity ≤ 10^5**
- **1 ≤ Q ≤ 2 × 10^5**
- **0 ≤ key ≤ 10^9**
- **0 ≤ value ≤ 10^9**

---

# Sample Input 1

```text
2
7
PUT 1 10
PUT 2 20
GET 1
PUT 3 30
GET 2
PUT 4 40
GET 1
```

---

# Sample Output 1

```text
10
-1
-1
```

---

# Explanation

Initial capacity:

```text
2
```

---

## Operation 1

```text
PUT 1 10
```

Cache:

```text
[1]
```

---

## Operation 2

```text
PUT 2 20
```

Cache:

```text
[1, 2]
```

where:

- `1` = LRU  
- `2` = MRU  

---

## Operation 3

```text
GET 1
```

Returns:

```text
10
```

Key:

```text
1
```

becomes most recently used.

Cache order:

```text
[2, 1]
```

---

## Operation 4

```text
PUT 3 30
```

Capacity exceeded.

Least recently used key:

```text
2
```

is evicted.

Cache:

```text
[1, 3]
```

---

## Operation 5

```text
GET 2
```

Key does not exist.

Return:

```text
-1
```

---

## Operation 6

```text
PUT 4 40
```

Least recently used key:

```text
1
```

is evicted.

Cache:

```text
[3, 4]
```

---

## Operation 7

```text
GET 1
```

Key no longer exists.

Return:

```text
-1
```

---

# Why Naive Approaches Fail

Using only arrays or linked lists causes:

- linear-time search  
- slow eviction handling  
- inefficient updates  

Similarly, using only hash maps fails to maintain usage ordering.

An efficient solution requires combining:

- direct key lookup  
- ordered recency tracking  

---

# Key Observation

Two operations are needed simultaneously:

| Requirement | Ideal Structure |
|---|---|
| Fast key lookup | Hash Map |
| Fast recency updates | Doubly Linked List |

Combining both structures enables:

- constant-time insertion  
- constant-time deletion  
- constant-time movement  

---

# Optimized Hybrid Data Structure Strategy

The optimal solution combines:

- Hash Map  
- Doubly Linked List  

---

# Core Design Idea

## Hash Map

Stores:

```text
key → nodePointer
```

This provides:

- O(1) average lookup  
- O(1) average node access  

---

## Doubly Linked List

Maintains usage ordering.

| Position | Meaning |
|---|---|
| Head | Most Recently Used |
| Tail | Least Recently Used |

This enables:

- O(1) insertion  
- O(1) deletion  
- O(1) movement  

---

# Algorithm Overview

## get(key)

### Case 1 — Key Missing

Return:

```text
-1
```

---

### Case 2 — Key Exists

- locate node using hash map  
- move node to front of doubly linked list  
- return stored value  

---

# put(key, value)

## Case 1 — Key Already Exists

- update node value  
- move node to front  
- do NOT increase cache size  

---

## Case 2 — New Key

### If Capacity Available

- create new node  
- insert at front  
- store mapping  

---

### If Capacity Full

- remove tail node  
- erase key from hash map  
- insert new node at front  

---

# Why This Works

The hash map guarantees:

- direct access to nodes  

The doubly linked list guarantees:

- efficient recency maintenance  
- efficient eviction  

Together they achieve:

- **O(1)** average complexity for all operations.

---

# Recommended Data Structures

| Structure | Purpose |
|---|---|
| `Hash Map` | Key → node lookup |
| `Doubly Linked List` | Usage ordering |
| `Node Pointers` | Constant-time deletion/insertion |

---

# Important Edge Cases

Your implementation should correctly handle:

- repeated updates to same key  
- updating existing key without increasing cache size  
- capacity:
  
```text
1
```

- consecutive evictions  
- repeated accesses  
- missing keys  
- very large operation counts  

---

# Expected Complexity

## Optimized LRU Cache Solution

### Time Complexity

| Operation | Complexity |
|---|---|
| `get()` | **O(1)** average |
| `put()` | **O(1)** average |

---

### Space Complexity

- **O(capacity)**

for:

- hash map storage  
- doubly linked list nodes  

---

# Example Walkthrough

Capacity:

```text
2
```

Operations:

```text
PUT 1 10
PUT 2 20
GET 1
PUT 3 30
```

---

## After First Two Inserts

Cache order:

```text
[1, 2]
```

where:

- `1` = LRU  
- `2` = MRU  

---

## Access Key 1

```text
GET 1
```

Move key:

```text
1
```

to MRU position.

Cache:

```text
[2, 1]
```

---

## Insert Key 3

Capacity exceeded.

Evict:

```text
2
```

Final cache:

```text
[1, 3]
```

---

# Alternative Approaches

Interviewers may also discuss:

- deque + hash map solutions  
- ordered dictionary implementations  
- LFU cache comparison  
- clock replacement policies  

---

# Follow-Up Variants

Interviewers may ask:

- Design LFU Cache  
- Thread-safe LRU Cache  
- Distributed cache sharding  
- TTL-based cache expiration  
- Persistent cache recovery  

---

# Execution Time Limit

**5 seconds**