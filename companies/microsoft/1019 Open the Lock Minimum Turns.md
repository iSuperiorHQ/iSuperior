# **Problem 1019: Open the Lock Minimum Turns**

**Company:** Microsoft

**Topic:** Graph / BFS

---

## **Problem Statement**

You are given a lock with **4 circular wheels**, each having digits from **0 to 9**.
Each wheel can rotate:

* **Forward** → digit increases by 1 (9 wraps to 0)
* **Backward** → digit decreases by 1 (0 wraps to 9)

The lock initially starts at **"0000"**.

---

### **Task**

Given:

* A list of **deadends** (forbidden lock states)
* A **target combination**

Your task is to determine the **minimum number of moves required** to reach the target from `"0000"`.

---

### **Rules**

* You **cannot enter any deadend state**.
* If the starting state `"0000"` is a deadend → return **-1**.
* If it is **impossible** to reach the target → return **-1**.
* Each move consists of rotating **one wheel by one position**.

---

## **Input Format**

* The **first line** contains an integer **n** (number of deadends).
* The next **n lines** contain strings representing deadend combinations.
* The last line contains the **target string**.

---

## **Constraints**

* **1 ≤ n ≤ 500**
* Each combination is a string of length **4**
* Only digits **0–9**
* Target is a valid 4-digit string

---

## **Output Format**

Return an integer representing the **minimum number of moves required** to reach the target.
Return **-1** if it is not possible.

---

## **Sample Input 1**

```text id="x6o0bm"
5
0201
0101
0102
1212
2002
0202
```

---

## **Sample Output 1**

```text id="b6g9hk"
6
```

---

## **Explanation**

One possible shortest sequence is:

```text id="rz33zw"
0000 → 1000 → 1100 → 1200 → 1201 → 1202 → 0202
```

Total moves = **6**

---

## **Sample Input 2**

```text id="b9n5l0"
1
8888
0009
```

---

## **Sample Output 2**

```text id="0ygr3x"
1
```

---

## **Explanation**

Just rotate the last wheel:

```text id="t9v8q2"
0000 → 0009
```

---

## **Sample Input 3**

```text id="p6x4dj"
1
0000
8888
```

---

## **Sample Output 3**

```text id="mq9f0w"
-1
```

---

## **Explanation**

The starting point **"0000"** is a deadend, so it is impossible to make any move.

---

## **Key Insight**

This problem can be modeled as a **shortest path problem in an unweighted graph**:

* Each lock state is a **node**
* Each valid move is an **edge**
* Solve using **Breadth-First Search (BFS)**

Time Complexity: **O(10⁴)** (all possible states)

---

## **Execution Time Limit**

**10 seconds**