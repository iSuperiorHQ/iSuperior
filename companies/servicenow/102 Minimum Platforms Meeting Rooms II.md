# **Problem 102: Minimum Platforms (Meeting Rooms II)**

**Company:** ServiceNow

**Category:** Greedy / Sorting / Two Pointers

**Difficulty:** Medium

---

# **Problem Description**

A busy railway junction handles hundreds of train arrivals and departures every day.

To avoid scheduling conflicts, the station administration must determine the minimum number of railway platforms required so that:

* no train waits for a platform
* no two trains occupy the same platform simultaneously

Each train has:

* an arrival time
* a departure time

A platform becomes free only after the train departs.

Your task is to calculate the minimum number of platforms required to manage all train schedules without overlap.

This problem is equivalent to the famous:

```text id="m2v8zk"
Meeting Rooms II
```

interval scheduling problem.

---

# **Task**

Given arrival and departure times of `N` trains, determine the minimum number of platforms required so that no train has to wait.

---

# **Platform Allocation Rules**

* If two trains overlap in time, separate platforms are required

* A train arriving exactly when another train departs:

```text id="x7m1qa"
does NOT require an additional platform
```

because the departing train frees the platform immediately.

---

# **Input Format**

First line contains integer:

```text id="u3m8qp"
N
```

representing total trains.

Second line contains:

```text id="f9m1zk"
N space-separated integers
```

representing arrival times.

Third line contains:

```text id="r2m8vx"
N space-separated integers
```

representing departure times.

---

# **Time Representation**

Times are represented in:

```text id="n7m2qa"
24-hour HHMM integer format
```

Examples:

| Time   | Meaning  |
| ------ | -------- |
| `930`  | 09:30 AM |
| `1545` | 03:45 PM |

---

# **Output Format**

Print a single integer representing:

```text id="p4m9xp"
minimum platforms required
```

---

# **Constraints**

* **1 ≤ N ≤ 10⁶**
* `0000 ≤ arrival[i] ≤ departure[i] ≤ 2359`

---

# **Sample Input 1**

```text id="v1m8zk"
6
900 940 950 1100 1500 1800
910 1200 1120 1130 1900 2000
```

---

# **Sample Output 1**

```text id="g8m2vx"
3
```

---

# **Explanation**

At time:

```text id="x2m1qa"
1100
```

three trains are simultaneously present:

| Train   | Interval    |
| ------- | ----------- |
| Train 2 | 940 → 1200  |
| Train 3 | 950 → 1120  |
| Train 4 | 1100 → 1130 |

Thus:

```text id="m9v2zk"
3 platforms
```

are required.

---

# **Sample Input 2**

```text id="k4m8qp"
4
900 1000 1100 1200
930 1030 1130 1230
```

---

# **Sample Output 2**

```text id="u7m1xp"
1
```

---

# **Explanation**

No train intervals overlap.

A single platform is sufficient.

---

# **Sample Input 3**

```text id="m4k8qa"
5
900 905 910 915 920
930 935 940 945 950
```

---

# **Sample Output 3**

```text id="v8m2zk"
5
```

---

# **Explanation**

At time:

```text id="x1m9vx"
920
```

all five trains are simultaneously present at the station.

Thus each train requires a separate platform.

---

# **Sample Input 4**

```text id="z7m2qp"
3
900 1000 1030
1000 1030 1100
```

---

# **Sample Output 4**

```text id="u4m8zk"
1
```

---

# **Explanation**

Train arrivals exactly match previous departures.

Since platforms free immediately after departure:

```text id="k2m1qa"
no extra platform is needed
```

---

# **Naive Approach**

For every train:

1. Compare with all other trains
2. Count overlapping intervals
3. Track maximum overlap

---

## **Complexity of Naive Solution**

### Time Complexity

* **O(N²)**

This becomes inefficient for very large inputs.

---

# **Optimized Greedy Approach**

Sort:

* arrival times
* departure times

independently.

Use two pointers to simulate platform allocation efficiently.

---

# **Efficient Strategy**

1. Sort arrival array
2. Sort departure array
3. Use two pointers:

   * `i` → arrivals
   * `j` → departures

---

## **Platform Allocation Logic**

* If:

```text id="r7m2zk"
arrival[i] < departure[j]
```

a new train arrives before the earliest departure.

Increase platforms.

---

* Otherwise:

```text id="u1m8xp"
arrival[i] >= departure[j]
```

a platform becomes free first.

Decrease active platforms.

---

Track maximum simultaneously active platforms.

---

# **Recommended Data Structures**

| Structure      | Purpose                       |
| -------------- | ----------------------------- |
| `Array`        | Store arrival/departure times |
| `Sorting`      | Chronological processing      |
| `Two Pointers` | Efficient overlap tracking    |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* identical arrival times
* identical departure times
* arrival equals departure
* fully overlapping schedules
* completely disjoint schedules
* single train input

---

# **Expected Complexity**

## Sorting + Two Pointer Solution

### Time Complexity

* **O(N log N)**

due to sorting.

---

### Space Complexity

* **O(1)** auxiliary space excluding sorting overhead.

---

# **Example Walkthrough**

Arrivals:

```text id="m4k8qa"
[900, 940, 950, 1100, 1500, 1800]
```

Departures:

```text id="v8m2zk"
[910, 1120, 1130, 1200, 1900, 2000]
```

Processing timeline:

| Event        | Platforms Active |
| ------------ | ---------------- |
| 900 Arrives  | 1                |
| 910 Departs  | 0                |
| 940 Arrives  | 1                |
| 950 Arrives  | 2                |
| 1100 Arrives | 3                |
| 1120 Departs | 2                |

Maximum active platforms:

```text id="x1m9vx"
3
```

---

# **Alternative Approaches**

Interviewers may also discuss:

* Min Heap solution
* Sweep Line Algorithm
* Meeting Rooms scheduling
* Interval overlap counting

---

# **Follow-Up Variants**

Interviewers may ask:

* Return actual platform assignments
* Minimize waiting time
* Handle dynamic train updates
* Support real-time scheduling
* Merge interval optimizations

---

# **Execution Time Limit**

**5 seconds**