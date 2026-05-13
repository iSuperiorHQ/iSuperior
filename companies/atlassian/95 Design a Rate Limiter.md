# **Problem 95: Design a Rate Limiter**

**Company:** Atlassian

**Category:** Low-Level Design (LLD) / Machine Coding

**Difficulty:** Hard

---

# **Problem Description**

A large-scale collaboration platform serves millions of API requests every minute from users across the globe.

To prevent:

* server overload
* API abuse
* denial-of-service attacks
* unfair resource consumption

the platform must enforce:

```text id="m2v8zk"
Request Rate Limiting
```

for every user.

Your task is to design and implement a modular, extensible, object-oriented rate limiter capable of controlling how many requests a user can make within a specified time interval.

The implementation should support efficient request validation in real time.

---

# **Business Requirement**

Each user is allowed a limited number of requests within a configurable time window.

Example:

```text id="x7m1qa"
Maximum 5 requests per 10 seconds
```

If the user exceeds the limit:

```text id="u3m8qp"
Request must be rejected
```

Otherwise:

```text id="f9m1zk"
Request is allowed
```

---

# **Functional Requirements**

Your implementation must support:

* user-specific request tracking
* configurable rate limits
* real-time request validation
* efficient memory usage
* scalable architecture
* thread-safe design considerations

---

# **Supported Algorithms**

You may implement any one of the following:

| Algorithm            | Description                                          |
| -------------------- | ---------------------------------------------------- |
| Token Bucket         | Tokens refill at fixed rate; requests consume tokens |
| Sliding Window       | Requests counted within rolling time interval        |
| Fixed Window Counter | Count requests within discrete windows               |
| Leaky Bucket         | Requests processed at constant drain rate            |

---

# **Recommended Approach**

Preferred interview implementation:

```text id="r2m8vx"
Sliding Window Rate Limiter
```

because it provides smoother request distribution and avoids burst-edge problems of fixed windows.

---

# **Task**

Design a rate limiter system supporting the following operations:

| Operation                         | Description                           |
| --------------------------------- | ------------------------------------- |
| `allowRequest(userId, timestamp)` | Returns whether request is allowed    |
| `configure(limit, windowSize)`    | Sets maximum requests and time window |
| `cleanup()`                       | Removes expired request history       |

---

# **Input Format**

First line contains:

```text id="n7m2qa"
limit windowSize
```

where:

* `limit` → maximum allowed requests
* `windowSize` → time window in seconds

Second line contains integer:

```text id="p4m9xp"
Q
```

representing total API requests.

Next `Q` lines contain:

```text id="v1m8zk"
userId timestamp
```

where:

* `userId` → unique user identifier
* `timestamp` → request timestamp in seconds

---

# **Output Format**

For every request print:

```text id="g8m2vx"
ALLOWED
```

or

```text id="x2m1qa"
REJECTED
```

---

# **Constraints**

* **1 ≤ Q ≤ 10⁵**
* **1 ≤ limit ≤ 10⁴**
* **1 ≤ windowSize ≤ 10⁶**
* **1 ≤ timestamp ≤ 10⁹**

---

# **Sample Input 1**

```text id="m9v2zk"
3 10
7
101 1
101 2
101 3
101 5
101 11
101 12
101 13
```

---

# **Sample Output 1**

```text id="k4m8qp"
ALLOWED
ALLOWED
ALLOWED
REJECTED
ALLOWED
ALLOWED
ALLOWED
```

---

# **Explanation**

Rate limit:

```text id="u7m1xp"
3 requests per 10 seconds
```

Requests at:

```text id="m4k8qa"
1, 2, 3
```

are allowed.

Request at timestamp:

```text id="v8m2zk"
5
```

is rejected because 3 previous requests already exist within the last 10-second sliding window.

At timestamp:

```text id="x1m9vx"
11
```

request at timestamp:

```text id="z7m2qp"
1
```

expires from the sliding window.

Hence request becomes allowed again.

---

# **Sample Input 2**

```text id="u4m8zk"
2 5
8
201 1
202 1
201 2
201 3
202 4
202 5
202 6
202 7
```

---

# **Sample Output 2**

```text id="k2m1qa"
ALLOWED
ALLOWED
ALLOWED
REJECTED
ALLOWED
REJECTED
ALLOWED
REJECTED
```

---

# **Explanation**

Each user maintains an independent request window.

User:

```text id="r7m2zk"
201
```

exceeds:

```text id="u1m8xp"
2 requests within 5 seconds
```

at timestamp:

```text id="m4k8qa"
3
```

thus request is rejected.

---

# **Object-Oriented Design Expectations**

Your solution should be modular and extensible.

Recommended classes:

| Class               | Responsibility                |
| ------------------- | ----------------------------- |
| `RateLimiter`       | Core request validation       |
| `UserBucket`        | Stores request timestamps     |
| `Request`           | Encapsulates request metadata |
| `RateLimiterConfig` | Stores rate limit settings    |

---

# **Thread Safety Considerations**

A production-grade implementation should consider:

* concurrent request processing
* synchronization
* race conditions
* atomic updates

Possible approaches:

* mutex locks
* concurrent hash maps
* distributed caching systems

---

# **Scalability Discussion**

Expected interview discussion points:

* horizontal scaling
* Redis-based distributed rate limiting
* sharding users across servers
* memory optimization
* request eviction policies

---

# **Sliding Window Strategy**

For each user:

Maintain a queue of timestamps.

For every incoming request:

1. Remove expired timestamps
2. Check queue size
3. If queue size < limit:

   * allow request
   * insert timestamp
4. Else:

   * reject request

---

# **Expected Complexity**

## Sliding Window Queue Approach

### Time Complexity

* **O(1)** amortized per request

because every timestamp is inserted and removed at most once.

---

### Space Complexity

* **O(U × L)**

Where:

* `U` = number of active users
* `L` = maximum requests stored per user

---

# **Bonus Follow-Up Questions**

Interviewers may ask:

* How would you implement distributed rate limiting?
* How would Redis sorted sets help?
* How would you avoid clock synchronization issues?
* How would you handle millions of users?
* How would you persist limiter state?

---

# **Execution Time Limit**

**10 seconds**