# **Problem 1088: Queue Implementation using Two Stacks**

**Company:** Infosys

**Topic:** Stack / Queue

---

## **Problem Description**

A distributed messaging platform processes incoming service requests in:

```text id="m2v8zk"
FIFO (First In First Out)
```

order.

However, due to system-level memory restrictions, the platform only provides access to:

```text id="x7m1qa"
Stack
```

operations.

Your task is to design and implement a fully functional queue using exactly:

```text id="u3m8qp"
Two Stacks
```

The queue must support standard operations while preserving correct FIFO behavior.

---

## **Task**

Implement a queue using two stacks and process the following operations:

| Operation   | Description                                       |
| ----------- | ------------------------------------------------- |
| `ENQUEUE x` | Insert element `x` into the queue                 |
| `DEQUEUE`   | Remove the front element from the queue           |
| `FRONT`     | Print the front element without removing it       |
| `SIZE`      | Print the current queue size                      |
| `EMPTY`     | Print `true` if queue is empty, otherwise `false` |

---

## **Important Constraint**

You may only use stack operations:

* `push`
* `pop`
* `top/peek`
* `isEmpty`

Direct queue data structures are not allowed.

---

## **Input Format**

* First line: integer **Q** — total number of operations

* Next `Q` lines contain one of the following commands:

```text id="f9m1zk"
ENQUEUE x
DEQUEUE
FRONT
SIZE
EMPTY
```

---

## **Constraints**

* **1 ≤ Q ≤ 10⁵**
* **-10⁹ ≤ x ≤ 10⁹**

---

## **Output Format**

For every:

* `FRONT`
* `SIZE`
* `EMPTY`

operation, print the corresponding result.

If:

```text id="r2m8vx"
DEQUEUE
```

or:

```text id="n7m2qa"
FRONT
```

is performed on an empty queue, print:

```text id="p4m9xp"
Queue Underflow
```

---

## **Sample Input 1**

```text id="v1m8zk"
8
ENQUEUE 10
ENQUEUE 20
FRONT
DEQUEUE
FRONT
SIZE
EMPTY
DEQUEUE
```

---

## **Sample Output 1**

```text id="g8m2vx"
10
20
1
false
```

---

## **Explanation**

Operations:

```text id="x2m1qa"
Queue = [10]
Queue = [10, 20]
FRONT → 10
DEQUEUE removes 10
FRONT → 20
SIZE → 1
EMPTY → false
DEQUEUE removes 20
```

Queue becomes empty after the final dequeue.

---

## **Sample Input 2**

```text id="m9v2zk"
7
DEQUEUE
ENQUEUE 5
FRONT
DEQUEUE
FRONT
EMPTY
SIZE
```

---

## **Sample Output 2**

```text id="k4m8qp"
Queue Underflow
5
Queue Underflow
true
0
```

---

## **Explanation**

Initially queue is empty.

Hence first:

```text id="u7m1xp"
DEQUEUE
```

causes underflow.

After removing `5`, queue becomes empty again.

---

## **Sample Input 3**

```text id="m4k8qa"
10
ENQUEUE 1
ENQUEUE 2
ENQUEUE 3
SIZE
DEQUEUE
FRONT
DEQUEUE
FRONT
EMPTY
SIZE
```

---

## **Sample Output 3**

```text id="v8m2zk"
3
2
3
false
1
```

---

## **Explanation**

Queue evolution:

```text id="x1m9vx"
[1]
[1,2]
[1,2,3]
```

After one dequeue:

```text id="z7m2qp"
[2,3]
```

Front becomes:

```text id="u4m8zk"
2
```

After another dequeue:

```text id="k2m1qa"
[3]
```

Queue is still non-empty.

---

## **Two Stack Architecture**

Maintain:

```text id="r7m2zk"
inputStack
outputStack
```

### ENQUEUE

Push directly into:

```text id="u1m8xp"
inputStack
```

### DEQUEUE / FRONT

If:

```text id="m4k8qa"
outputStack
```

is empty:

* Transfer all elements from `inputStack`
* Reverse order automatically forms FIFO sequence

Then process removal or access from:

```text id="v8m2zk"
outputStack
```

---

## **Why This Works**

Stacks operate in:

```text id="x1m9vx"
LIFO
```

order.

Using two reversals:

```text id="z7m2qp"
inputStack → outputStack
```

restores FIFO behavior required for queues.

---

## **Expected Complexity**

### Amortized Analysis

* **ENQUEUE:** `O(1)`
* **DEQUEUE:** `O(1)` amortized
* **FRONT:** `O(1)` amortized
* **SIZE:** `O(1)`
* **EMPTY:** `O(1)`

---

## **Space Complexity**

* **O(N)**

Where:

* `N` = number of elements stored in the queue

---

## **Execution Time Limit**

**10 seconds**