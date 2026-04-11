# **Problem 1042: Alice & Bob Typewriter – Validate String Equivalence**

**Company:** TCS

**Topic:** Strings / Stack

---

## **Problem Statement**

Alice and Bob are typing messages on their typewriters. However, their keyboards have a special key:

* The character **'#'** represents a **backspace**, meaning it deletes the previous character (if any).

Both Alice and Bob type their strings independently.

---

## **Task**

Given two strings **s** and **t**, determine whether they are **equal after processing all backspaces**.

---

## **Backspace Rules**

* If the current character is **'#'**, remove the **last valid character** (if any)
* If there is **no character to delete**, ignore the backspace
* All other characters are appended normally

---

## **Input Format**

* The **first line** contains string **s** (Alice’s input)
* The **second line** contains string **t** (Bob’s input)

---

## **Constraints**

* **1 ≤ |s|, |t| ≤ 10⁵**
* Strings contain **lowercase letters and '#' only**

---

## **Output Format**

* Print **true** if both strings are equal after processing
* Otherwise, print **false**

---

## **Sample Input 1**

```text id="q7v2xp"
ab#c
ad#c
```

---

## **Sample Output 1**

```text id="n5r8ty"
true
```

---

## **Explanation**

Process both strings:

```text id="k9x2mw"
"ab#c" → "ac"
"ad#c" → "ac"
```

Both are equal → **true**

---

## **Sample Input 2**

```text id="r4m7qa"
a##c
#a#c
```

---

## **Sample Output 2**

```text id="b8t3zn"
true
```

---

## **Explanation**

```text id="v2k8ps"
"a##c" → "c"
"#a#c" → "c"
```

---

## **Sample Input 3**

```text id="x1z9dl"
a#c
b
```

---

## **Sample Output 3**

```text id="p6q3vt"
false
```

---

## **Explanation**

```text id="d4m8wr"
"a#c" → "c"
"b" → "b"
```

Strings are different → **false**

---

## **Key Insight**

* Use a **stack** (or simulate using string builder):

  * Push characters
  * Pop when encountering '#'
* Alternatively, solve using **two pointers from the end** (optimized approach)

Time Complexity: **O(n)**
Space Complexity: **O(n)**

---

## **Execution Time Limit**

**10 seconds**