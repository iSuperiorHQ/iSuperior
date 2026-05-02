# **Problem 1060: Count Pattern Occurrences Using Efficient String Matching**

**Company:** Accenture

**Topic:** Strings / KMP Basics

---

## **Problem Description**

In a log analysis system, large text streams must be scanned efficiently to detect repeated patterns.

You are given:

* A **text string** `T`
* A **pattern string** `P`

Your task is to determine how many times the pattern `P` appears in the text `T`.

---

## **Important Requirement**

* Pattern occurrences must be counted **including overlapping matches**
* The solution must be optimized for large inputs
* A naive **O(N × M)** solution may not pass all test cases

---

## **Task**

Implement an efficient algorithm to return the **total number of occurrences** of pattern `P` in text `T`.

---

## **Input Format**

* First line: string **T** (text)
* Second line: string **P** (pattern)

---

## **Constraints**

* **1 ≤ |T| ≤ 10⁶**
* **1 ≤ |P| ≤ 10⁵**
* Both strings contain only lowercase English letters

---

## **Output Format**

* Print a single integer — the total number of occurrences

---

## **Sample Input 1**

```text id="in1"
T: ababcabcab
P: abc
```

---

## **Sample Output 1**

```text id="out1"
2
```

---

## **Explanation**

Occurrences of **"abc"** in text:

```text id="exp1"
ab[abc]abcab
     [abc]
```

Total = **2**

---

## **Sample Input 2 (Overlapping Case)**

```text id="in2"
T: aaaa
P: aa
```

---

## **Sample Output 2**

```text id="out2"
3
```

---

## **Explanation**

Overlapping matches:

```text id="exp2"
[aa]aa
 a[aa]a
  aa[aa]
```

Total = **3**

---

## **Sample Input 3**

```text id="in3"
T: abcdef
P: gh
```

---

## **Sample Output 3**

```text id="out3"
0
```

---

## **Key Insight**

* Naive approach → **O(N × M)** (may fail for large inputs)
* Optimized approach → **KMP (Knuth-Morris-Pratt)**

  * Preprocess pattern using **LPS (Longest Prefix Suffix array)**
  * Time Complexity: **O(N + M)**

---

## **What they check:**

* Understanding of **pattern matching algorithms**
* Handling **overlapping occurrences**
* Ability to optimize from brute-force to **KMP**
* Working with large input efficiently

---

## **Execution Time Limit**

**10 seconds**