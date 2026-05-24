# Problem 127: Design Hit Counter

**Company:** Uber  

**Category:** Queue / Sliding Window  

**Difficulty:** Medium  

---

# Problem Description

Large-scale ride-sharing platforms continuously receive massive streams of real-time events such as:

- ride requests  
- driver pings  
- API calls  
- payment validations  
- surge recalculations  

To monitor traffic spikes and system load, backend systems maintain a:

```text
Hit Counter
```

that tracks how many requests occurred within a recent fixed-duration time window.

Your task is to design a data structure that efficiently records hits and returns the number of hits received during the:

```text
last 300 seconds
```

(5-minute sliding window).

Efficient solutions require candidates to:

- maintain chronological event ordering  
- discard expired timestamps efficiently  
- support real-time queries  
- avoid rescanning historical events repeatedly  

This problem evaluates a candidate’s understanding of:

- sliding window techniques  
- queue-based processing  
- amortized analysis  
- real-time stream handling  
- time-window optimization  

Interviewers expect:

- **O(1)** amortized complexity for:
  
```text
hit()
```

and:

```text
getHits()
```

operations.

---

# Task

Design a data structure:

```text
HitCounter
```

supporting the following operations:

| Operation | Description |
|---|---|
| `hit(timestamp)` | Record a hit at given timestamp |
| `getHits(timestamp)` | Return hits in last 300 seconds |

---

# Window Definition

A hit recorded at time:

```text
t
```

is considered valid for queries within:



inclusive.

Equivalently, a hit at timestamp:

```text
x
```

remains valid if:



Thus:

- hits older than:
  
```text
timestamp - 299
```

must be removed from the active window.

---

# Important Rules

- Timestamps are provided in:
  
```text
seconds
```

- Timestamps are strictly non-decreasing  
- Multiple hits may occur at the same timestamp  
- Expired hits must NOT contribute to future queries  
- Operations must be optimized for high-frequency traffic streams  

---

# Required Operations

## hit(timestamp)

Record a hit occurring at:

```text
timestamp
```

---

## getHits(timestamp)

Return total number of hits received during the:

```text
last 300 seconds
```

including current timestamp.

---

# Input Format

First line contains integer:

```text
Q
```

representing number of operations.

Next:

```text
Q
```

lines contain operations in one of the following formats:

## Hit Operation

```text
HIT timestamp
```

## Query Operation

```text
GET timestamp
```

---

# Output Format

For every:

```text
GET
```

operation print the number of valid hits.

---

# Constraints

- **1 ≤ Q ≤ 2 × 10^5**
- **1 ≤ timestamp ≤ 10^9**
- Timestamps are non-decreasing

---

# Sample Input 1

```text
7
HIT 1
HIT 2
HIT 3
GET 4
HIT 300
GET 300
GET 301
```

---

# Sample Output 1

```text
3
4
3
```

---

# Explanation

---

## Operation 1

```text
HIT 1
```

Queue:

```text
[1]
```

---

## Operation 2

```text
HIT 2
```

Queue:

```text
[1, 2]
```

---

## Operation 3

```text
HIT 3
```

Queue:

```text
[1, 2, 3]
```

---

## Operation 4

```text
GET 4
```

Valid window:



All hits remain valid.

Result:

```text
3
```

---

## Operation 5

```text
HIT 300
```

Queue:

```text
[1, 2, 3, 300]
```

---

## Operation 6

```text
GET 300
```

Valid window:



All hits remain valid.

Result:

```text
4
```

---

## Operation 7

```text
GET 301
```

Valid window:



Hit at timestamp:

```text
1
```

expires.

Remaining valid hits:

```text
2, 3, 300
```

Result:

```text
3
```

---

# Why Naive Approaches Fail

A brute-force solution scans all historical hits during every query.

This results in:

- repeated traversal  
- unnecessary processing  
- poor scalability under large traffic volumes  

Worst-case complexity becomes:

- **O(N)** per query

which fails real-time system requirements.

---

# Key Observation

Only hits inside the most recent:

```text
300-second
```

window matter.

Older timestamps can be permanently removed.

This naturally forms a:

```text
sliding window
```

problem.

---

# Optimized Sliding Window Strategy

The optimal solution uses:

- queue-based timestamp ordering  
- incremental cleanup of expired hits  

---

# Core Design Idea

## Queue Structure

Maintain hit timestamps in chronological order.

Since timestamps are non-decreasing:

- newest hits are inserted at rear  
- expired hits always appear at front  

This enables efficient cleanup.

---

# Algorithm Overview

## hit(timestamp)

Insert timestamp into queue.

---

## getHits(timestamp)

### Step 1 — Remove Expired Hits

While:



remove front timestamp.

---

## Step 2 — Return Queue Size

Remaining queue elements represent valid hits inside current sliding window.

---

# Why This Works

The queue always stores only:

```text
valid timestamps
```

inside the active window.

Each timestamp:

- enters queue exactly once  
- leaves queue exactly once  

Therefore, total removals across all operations are bounded by total insertions.

This guarantees efficient amortized performance.

---

# Recommended Data Structures

| Structure | Purpose |
|---|---|
| `Queue` | Chronological timestamp storage |

No auxiliary indexing structures are required.

---

# Important Edge Cases

Your implementation should correctly handle:

- multiple hits at same timestamp  
- large timestamp gaps  
- all hits expiring simultaneously  
- repeated queries without new hits  
- exactly 300-second boundary cases  
- very large operation counts  

---

# Expected Complexity

## Optimized Queue Sliding Window Solution

### Time Complexity

| Operation | Complexity |
|---|---|
| `hit()` | **O(1)** |
| `getHits()` | **O(1)** amortized |

Each timestamp is inserted and removed at most once.

---

### Space Complexity

- **O(W)**

where:

```text
W
```

represents number of hits inside active 300-second window.

---

# Example Walkthrough

Operations:

```text
HIT 1
HIT 2
HIT 300
GET 301
```

---

## Queue Before Query

```text
[1, 2, 300]
```

---

## Valid Window

For:

```text
GET 301
```

window becomes:



Timestamp:

```text
1
```

expires.

---

## Queue After Cleanup

```text
[2, 300]
```

---

## Final Result

```text
2
```

---

# Alternative Approaches

Interviewers may also discuss:

- circular-buffer implementations  
- bucketed counting arrays  
- fixed-size rolling windows  
- distributed hit aggregation  

---

# Follow-Up Variants

Interviewers may ask:

- Design rate limiter  
- Sliding window median  
- Time-decayed analytics  
- Concurrent hit counters  
- Distributed monitoring systems  

---

# Execution Time Limit

**4 seconds**