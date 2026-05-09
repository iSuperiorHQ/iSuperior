# **Problem 1074: Largest Notorious Student Group**

**Company:** Capgemini

**Topic:** Strings / Sliding Window

---

## **Problem Description**

A university disciplinary system tracks student behavior using encoded character records.

Each character in a string represents a specific student trait:

* `'N'` → Notorious student
* `'G'` → Good student

The administration wants to identify the largest continuous group of notorious students that can exist after allowing at most `K` behavioral corrections.

A correction means converting a `'G'` student into an `'N'` student.

Your task is to determine the maximum possible size of a contiguous group containing only notorious students after performing at most `K` corrections.

---

## **Task**

Given:

* A string `S`
* An integer `K`

Return the maximum length of a contiguous substring that can contain only `'N'` characters after at most `K` conversions.

---

## **Input Format**

* First line: string **S**
* Second line: integer **K**

---

## **Constraints**

* **1 ≤ |S| ≤ 10⁵**
* `S` contains only:

```text id="v1m8zk"
'N' and 'G'
```

* **0 ≤ K ≤ |S|**

---

## **Output Format**

Print a single integer — the maximum possible group size.

---

## **Sample Input 1**

```text id="k7m2qa"
NNGNGNN
1
```

---

## **Sample Output 1**

```text id="m2v9xp"
4
```

---

## **Explanation**

Convert one `'G'` inside:

```text id="x8m1zk"
NNGNGNN
  ↑
```

Possible transformed segment:

```text id="p4m2vx"
NNNNGNN
```

Largest continuous notorious group:

```text id="r9m8qa"
NNNN
```

Length = **4**

---

## **Sample Input 2**

```text id="u3m1zk"
GNGNNGGN
2
```

---

## **Sample Output 2**

```text id="f8m2xp"
5
```

---

## **Explanation**

Convert two `'G'` characters:

```text id="n7m9qa"
G N G N N G G N
  ↑       ↑
```

One possible transformed string:

```text id="z2m8vx"
G N N N N N G N
```

Largest continuous notorious group:

```text id="q1m2zk"
NNNNN
```

Length = **5**

---

## **Sample Input 3**

```text id="m8v1qa"
GGGG
2
```

---

## **Sample Output 3**

```text id="x2m9xp"
2
```

---

## **Explanation**

At most two students can be corrected:

```text id="k4m8qa"
GGGG → NNGG
```

Largest notorious segment length = **2**

---

## **Sample Input 4**

```text id="v7m2zk"
NNNNN
0
```

---

## **Sample Output 4**

```text id="a1m8vx"
5
```

---

## **Explanation**

No corrections are needed since all students are already notorious.

---

## **Optimized Approach**

Use the **Sliding Window Technique**:

1. Expand the window while counting `'G'` characters
2. If count of `'G'` exceeds `K`:

   * Shrink the window from the left
3. Track the maximum valid window length

---

## **Expected Complexity**

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(1)`

---

## **Execution Time Limit**

**10 seconds**
