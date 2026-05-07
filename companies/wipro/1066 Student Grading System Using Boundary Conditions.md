# **Problem 1066: Student Grading System Using Boundary Conditions**

**Company:** Wipro

**Topic:** Conditions / Switch Case / Logic Building

---

## **Problem Description**

A university examination system assigns grades to students based on their final marks. The grading logic must carefully handle **inclusive boundary ranges**, since even a one-mark mistake can result in an incorrect grade assignment.

You are given a student's marks. Your task is to determine the correct grade using proper conditional logic.

---

## **Grading Rules**

| Marks Range | Grade |
| ----------- | ----- |
| 90 – 100    | A     |
| 80 – 89     | B     |
| 70 – 79     | C     |
| 60 – 69     | D     |
| 50 – 59     | E     |
| Below 50    | F     |

---

## **Task**

Implement the grading system such that:

* All boundary values are handled correctly
* Invalid marks are detected
* The correct grade is returned for the given marks

---

## **Special Condition**

If the entered marks are:

* Less than **0**
* Greater than **100**

then print:

```text id="mddnd1"
Invalid Marks
```

---

## **Input Format**

* A single integer **marks**

---

## **Constraints**

* **-10 ≤ marks ≤ 110**

---

## **Output Format**

* Print the corresponding grade:

```text id="5rjptk"
A / B / C / D / E / F
```

* Or print:

```text id="64c38h"
Invalid Marks
```

for invalid input.

---

## **Sample Input 1**

```text id="g7bz2w"
95
```

---

## **Sample Output 1**

```text id="tbkv8s"
A
```

---

## **Explanation**

```text id="c0q21q"
95 lies in the range 90–100
```

Hence grade = **A**

---

## **Sample Input 2**

```text id="k72q5v"
59
```

---

## **Sample Output 2**

```text id="qzb1pk"
E
```

---

## **Explanation**

```text id="vif2rn"
59 lies in the range 50–59
```

Hence grade = **E**

---

## **Sample Input 3**

```text id="6wlu8l"
-5
```

---

## **Sample Output 3**

```text id="wmv5aa"
Invalid Marks
```

---

## **Explanation**

```text id="yw9w1h"
Marks cannot be negative
```

---

## **Sample Input 4**

```text id="9b3vv0"
100
```

---

## **Sample Output 4**

```text id="wzcazq"
A
```

---

## **Explanation**

```text id="7l6yfm"
100 is included in the A grade range
```

This checks proper handling of inclusive boundaries.

---

## **Key Insight**

* Carefully handle:

  * `>=` and `<=` conditions
  * Boundary values like:

```text id="lny5eo"
49, 50, 59, 60, 89, 90, 100
```

* Logic can be implemented using:

  * Nested if-else
  * Else-if ladder
  * Switch-case with grouped conditions

---

## **What they check:**

* Correct conditional logic
* Inclusive boundary handling
* Input validation
* Logical flow design

---

## **Execution Time Limit**

**10 seconds**