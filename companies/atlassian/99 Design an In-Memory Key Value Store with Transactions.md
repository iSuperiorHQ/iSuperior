# **Problem 99: Design an In-Memory Key-Value Store with Transactions**

**Company:** Atlassian

**Category:** Low-Level Design (LLD) / Machine Coding

**Difficulty:** Hard

---

# **Problem Description**

A cloud-native configuration management service requires a high-performance in-memory key-value database capable of handling transactional updates.

The system should support:

* fast key-value operations
* nested transactions
* rollback support
* atomic commits
* efficient memory access
* real-time updates

Your task is to design and implement a modular, object-oriented in-memory key-value store supporting transactional behavior similar to lightweight database engines.

---

# **Functional Requirements**

The key-value store must support:

* inserting key-value pairs
* updating values
* deleting keys
* reading values
* nested transactions
* rollback operations
* transaction commits
* isolation of uncommitted changes

---

# **Supported Commands**

| Command         | Description                |
| --------------- | -------------------------- |
| `SET key value` | Insert/update value        |
| `GET key`       | Retrieve value             |
| `DELETE key`    | Remove key                 |
| `BEGIN`         | Start new transaction      |
| `COMMIT`        | Persist active transaction |
| `ROLLBACK`      | Undo active transaction    |

---

# **Transaction Rules**

## BEGIN

Creates a new transaction layer.

Changes inside a transaction remain isolated until committed.

Nested transactions are allowed.

---

## COMMIT

Applies all changes from the current transaction to its parent transaction.

If the committed transaction has no parent transaction, changes are merged into the base database.

If no transaction exists:

```text id="m2v8zk"
NO TRANSACTION
```

should be printed.

---

## ROLLBACK

Discards all changes made in the current transaction.

If no transaction exists:

```text id="x7m1qa"
NO TRANSACTION
```

should be printed.

---

# **Key Lookup Rules**

When reading a key:

1. Search latest active transaction first
2. Then search parent transactions
3. Finally search base database

This ensures transactional visibility.

---

# **Deletion Rules**

Deleting a key inside a transaction should:

* hide the key from current transaction scope
* preserve original value outside transaction until commit

Deleting a key outside transactions removes it directly from the base database.

---

# **Task**

Design a key-value store supporting:

| Operation         | Description        |
| ----------------- | ------------------ |
| `set(key, value)` | Store value        |
| `get(key)`        | Retrieve value     |
| `delete(key)`     | Remove key         |
| `begin()`         | Create transaction |
| `commit()`        | Persist changes    |
| `rollback()`      | Revert transaction |

---

# **Input Format**

First line contains integer:

```text id="u3m8qp"
Q
```

representing total commands.

Next `Q` lines contain one command.

---

# **Output Format**

For every:

* `GET`
* invalid `COMMIT`
* invalid `ROLLBACK`

print corresponding output.

---

## **GET Output**

Print:

* stored value
  OR

```text id="f9m1zk"
NULL
```

if key does not exist.

---

# **Constraints**

* **1 ≤ Q ≤ 10⁵**
* Keys and values are strings
* Key length ≤ `100`
* Value length ≤ `10⁴`

---

# **Sample Input 1**

```text id="r2m8vx"
10
SET a 10
GET a
BEGIN
SET a 20
GET a
ROLLBACK
GET a
DELETE a
GET a
COMMIT
```

---

# **Sample Output 1**

```text id="n7m2qa"
10
20
10
NULL
NO TRANSACTION
```

---

# **Explanation**

Initially:

```text id="p4m9xp"
a = 10
```

Inside transaction:

```text id="v1m8zk"
a = 20
```

After:

```text id="g8m2vx"
ROLLBACK
```

value reverts to:

```text id="x2m1qa"
10
```

Since no active transaction exists after rollback:

```text id="m9v2zk"
DELETE a
```

removes the key directly from the base database.

Final:

```text id="k4m8qp"
COMMIT
```

fails because no active transaction exists.

---

# **Sample Input 2**

```text id="u7m1xp"
12
SET x 1
BEGIN
SET x 2
BEGIN
DELETE x
GET x
ROLLBACK
GET x
COMMIT
GET x
ROLLBACK
GET x
```

---

# **Sample Output 2**

```text id="m4k8qa"
NULL
2
2
NO TRANSACTION
2
```

---

# **Explanation**

Nested transaction deletes:

```text id="v8m2zk"
x
```

temporarily.

After inner rollback:

```text id="x1m9vx"
x = 2
```

is restored.

Outer commit persists:

```text id="z7m2qp"
x = 2
```

to base database.

Final rollback fails because no transaction exists.

---

# **Sample Input 3**

```text id="u4m8zk"
11
BEGIN
SET name alice
BEGIN
SET name bob
GET name
COMMIT
GET name
ROLLBACK
GET name
BEGIN
DELETE name
GET name
```

---

# **Sample Output 3**

```text id="k2m1qa"
bob
bob
NULL
NULL
```

---

# **Explanation**

Outer transaction stores:

```text id="r7m2zk"
name = alice
```

Inner transaction updates:

```text id="u1m8xp"
name = bob
```

After:

```text id="m4k8qa"
COMMIT
```

inner transaction merges into outer transaction.

Thus:

```text id="v8m2zk"
GET name
```

still returns:

```text id="x1m9vx"
bob
```

After:

```text id="z7m2qp"
ROLLBACK
```

outer transaction is discarded completely.

Therefore:

```text id="u4m8zk"
GET name
```

returns:

```text id="k2m1qa"
NULL
```

New transaction deletes:

```text id="r7m2zk"
name
```

which remains invisible in current transaction scope.

---

# **Object-Oriented Design Expectations**

Recommended classes:

| Class                | Responsibility               |
| -------------------- | ---------------------------- |
| `KeyValueStore`      | Core database manager        |
| `Transaction`        | Stores transactional changes |
| `TransactionManager` | Handles transaction stack    |
| `CommandProcessor`   | Parses commands              |
| `Entry`              | Represents stored values     |

---

# **Recommended Data Structures**

| Structure | Purpose             |
| --------- | ------------------- |
| `HashMap` | Fast key lookup     |
| `Stack`   | Nested transactions |
| `HashSet` | Track deleted keys  |

---

# **Efficient Strategy**

Maintain:

* base database map
* stack of transaction layers

For every:

```text id="u1m8xp"
BEGIN
```

push new transaction map.

For:

```text id="m4k8qa"
COMMIT
```

merge current transaction into parent layer or base database.

For:

```text id="v8m2zk"
ROLLBACK
```

discard top transaction.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* nested transactions
* repeated rollbacks
* deleting non-existent keys
* shadowed keys
* committing empty transactions
* transaction visibility rules

---

# **Expected Complexity**

## HashMap + Transaction Stack Design

### SET / GET / DELETE

* **Time Complexity:** `O(T)`

Where:

* `T` = number of active transaction layers

Lookup may traverse nested transaction stack.

---

### BEGIN / ROLLBACK

* **Time Complexity:** `O(1)`

---

### COMMIT

* **Time Complexity:** `O(K)`

Where:

* `K` = number of modified keys in current transaction

---

### Space Complexity

* **O(N + M)**

Where:

* `N` = total stored keys
* `M` = total uncommitted transactional changes

---

# **Scalability Discussion**

Expected interview discussion points:

* write-ahead logging
* snapshot isolation
* MVCC (Multi-Version Concurrency Control)
* persistence mechanisms
* distributed transactions
* optimistic vs pessimistic locking

---

# **Bonus Follow-Up Questions**

Interviewers may ask:

* How would you support concurrent transactions?
* How would you persist state to disk?
* How would you implement expiration TTL?
* How would Redis-style transactions differ?
* How would you support rollback checkpoints?

---

# **Execution Time Limit**

**10 seconds**