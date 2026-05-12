# **Problem 1093: Compare Version Numbers**

**Company:** Adobe

**Topic:** String Parsing / Math

**Difficulty:** Medium

---

## **Problem Description**

A distributed software deployment platform maintains multiple application builds identified using hierarchical version numbers.

Each version string consists of numeric revisions separated by:

```text id="m2v8zk"
.
```

Example:

```text id="x7m1qa"
1.0.12
2.5
10.4.7.9
```

During deployment validation, the system must determine which software version is newer.

However, version comparison contains several complexities:

* Revision lengths may differ
* Leading zeroes may exist
* Missing revisions should be treated as zero
* Versions may contain trailing zero revisions

Your task is to accurately compare two version strings.

---

## **Task**

Given two version strings:

```text id="u3m8qp"
version1
version2
```

compare them revision-by-revision.

Return:

| Result | Meaning                 |
| ------ | ----------------------- |
| `1`    | version1 > version2     |
| `-1`   | version1 < version2     |
| `0`    | both versions are equal |

---

## **Version Comparison Rules**

### Rule 1 — Dot-Separated Revisions

Each version contains numeric sections separated by dots.

Example:

```text id="f9m1zk"
1.2.10
```

contains revisions:

```text id="r2m8vx"
1, 2, 10
```

---

### Rule 2 — Leading Zeroes Are Ignored

Example:

```text id="n7m2qa"
001
```

is treated as:

```text id="p4m9xp"
1
```

---

### Rule 3 — Missing Revisions Become Zero

Example:

```text id="v1m8zk"
1.0
```

equals:

```text id="g8m2vx"
1.0.0.0
```

because absent revisions are considered:

```text id="x2m1qa"
0
```

---

### Rule 4 — Compare Sequentially

Compare revisions from left to right.

At the first differing revision:

* larger number → larger version

If all revisions match:

```text id="m9v2zk"
versions are equal
```

---

### Rule 5 — Valid Revision Format

Every revision contains at least one digit.

Invalid formats such as:

```text id="k4m8qp"
1..0
.1
1.
```

are not allowed.

---

## **Input Format**

* First line: string **version1**
* Second line: string **version2**

---

## **Constraints**

* **1 ≤ length(version1), length(version2) ≤ 10⁵**

* Versions contain:

  * digits
  * dots (`.`)

* Each revision fits within 64-bit signed integer range

---

## **Output Format**

Print:

```text id="u7m1xp"
1
```

OR

```text id="m4k8qa"
-1
```

OR

```text id="v8m2zk"
0
```

---

## **Sample Input 1**

```text id="x1m9vx"
1.01
1.001
```

---

## **Sample Output 1**

```text id="z7m2qp"
0
```

---

## **Explanation**

Both versions normalize to:

```text id="u4m8zk"
1.1
```

Hence both are equal.

---

## **Sample Input 2**

```text id="k2m1qa"
1.0
1.0.0
```

---

## **Sample Output 2**

```text id="r7m2zk"
0
```

---

## **Explanation**

Trailing missing revisions are treated as:

```text id="u1m8xp"
0
```

Thus:

```text id="m4k8qa"
1.0 = 1.0.0
```

---

## **Sample Input 3**

```text id="v8m2zk"
1.0.5
1.0.3
```

---

## **Sample Output 3**

```text id="x1m9vx"
1
```

---

## **Explanation**

Compare revisions sequentially:

```text id="z7m2qp"
1 = 1
0 = 0
5 > 3
```

Hence:

```text id="u4m8zk"
version1 > version2
```

---

## **Sample Input 4**

```text id="k2m1qa"
7.5.2.4
7.5.3
```

---

## **Sample Output 4**

```text id="r7m2zk"
-1
```

---

## **Explanation**

Compare revisions:

```text id="u1m8xp"
7 = 7
5 = 5
2 < 3
```

Thus:

```text id="m4k8qa"
version1 < version2
```

---

## **Sample Input 5**

```text id="v8m2zk"
3.10.1
3.2.20
```

---

## **Sample Output 5**

```text id="x1m9vx"
1
```

---

## **Explanation**

Numeric comparison must be used:

```text id="z7m2qp"
10 > 2
```

Hence:

```text id="u4m8zk"
3.10.1 > 3.2.20
```

---

## **String Parsing Insight**

Parse revisions incrementally using pointers.

For every revision:

1. Extract numeric segment
2. Ignore leading zeroes
3. Convert to integer
4. Compare corresponding revisions

If one version ends early:

```text id="k2m1qa"
missing revisions = 0
```

---

## **Efficient Strategy**

Maintain two pointers:

```text id="r7m2zk"
i → version1
j → version2
```

Process one revision at a time until both strings are fully traversed.

---

## **Expected Complexity**

### Single Pass Parsing

* **Time Complexity:** `O(N + M)`
* **Space Complexity:** `O(1)`

Where:

* `N` = length of version1
* `M` = length of version2

---

## **Execution Time Limit**

**10 seconds**