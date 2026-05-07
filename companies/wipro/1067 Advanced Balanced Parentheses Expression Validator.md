# **Problem 1067: Advanced Balanced Parentheses Expression Validator**

**Company:** Wipro

**Topic:** Stack / Strings / Expression Parsing

---

## **Problem Description**

A compiler validation engine is designed to analyze mathematical and programming expressions before execution.

One of the critical validation steps is checking whether all brackets in an expression are:

* Properly opened and closed
* Correctly nested
* Mathematically balanced

You are given an expression containing:

* Parentheses: `(` `)`
* Curly braces: `{` `}`
* Square brackets: `[` `]`
* Alphabets, digits, operators, and spaces

Your task is to determine whether the complete expression is **structurally valid**.

---

## **Validation Rules**

An expression is considered **balanced** if:

1. Every opening bracket has a corresponding closing bracket
2. Brackets close in the correct order
3. No closing bracket appears before its matching opening bracket
4. Different bracket types must be nested correctly

---

## **Examples of Valid Expressions**

```text id="0o1n5w"
(a+b) * [c-d]
{[()]}
((A+B) * (C-D))
```

---

## **Examples of Invalid Expressions**

```text id="c5n53g"
([)]
((())
{[}]
```

---

## **Task**

Implement a validator that returns whether the given expression is balanced or not.

---

## **Input Format**

* A single string representing the mathematical expression

---

## **Constraints**

* **1 ≤ length of expression ≤ 10⁶**
* Expression may contain:

  * Uppercase/lowercase letters
  * Digits
  * Spaces
  * Mathematical operators
  * Brackets

---

## **Output Format**

Print:

```text id="5m45y2"
Balanced
```

if the expression is valid.

Otherwise print:

```text id="kx8qte"
Not Balanced
```

---

## **Sample Input 1**

```text id="84pw7u"
{[(a+b) * (x+y)] + 7}
```

---

## **Sample Output 1**

```text id="5ecynq"
Balanced
```

---

## **Explanation**

```text id="lfu26i"
All opening brackets are correctly matched and properly nested.
```

---

## **Sample Input 2**

```text id="7v9wmf"
([)]
```

---

## **Sample Output 2**

```text id="3r2hca"
Not Balanced
```

---

## **Explanation**

```text id="gr5aeh"
'(' is incorrectly closed by ']'
```

Bracket nesting order is invalid.

---

## **Sample Input 3**

```text id="t1rxq0"
((A+B) * [C-D]
```

---

## **Sample Output 3**

```text id="ps5ejj"
Not Balanced
```

---

## **Explanation**

```text id="aymckv"
One opening bracket remains unmatched.
```

---

## **Sample Input 4**

```text id="r3shtn"
{[()()]}[{}]
```

---

## **Sample Output 4**

```text id="n22f3d"
Balanced
```

---

## **Key Insight**

A **Stack** is the optimal data structure for this problem:

* Push opening brackets
* On encountering a closing bracket:

  * Check top of stack
  * Validate matching pair
  * Pop if valid
* Expression is balanced only if stack becomes empty at the end

---

## **Expected Complexity**

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(N)`

Efficient handling is required for very large expressions.

---

## **What they check:**

* Proper use of **Stack data structure**
* Expression parsing ability
* Correct nesting validation
* Edge case handling:

  * Empty stack access
  * Deep nesting
  * Mixed bracket types

---

## **Execution Time Limit**

**10 seconds**