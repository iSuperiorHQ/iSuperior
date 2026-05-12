# **Problem 1092: String to Integer (atoi)**

**Company:** Adobe

**Topic:** String Parsing

**Difficulty:** Medium

---

## **Problem Description**

A distributed transaction processing system receives numeric values as raw text packets from multiple external services.

Before performing financial computations, the system must safely convert incoming string data into a valid signed 32-bit integer.

However, the input stream may contain:

* Leading whitespaces
* Optional sign characters
* Non-numeric trailing characters
* Overflow-producing values
* Invalid formatting patterns

Your task is to implement a robust parser that converts a string into a valid integer while strictly following 32-bit signed integer constraints.

---

## **Task**

Given a string `S`, convert it into a signed 32-bit integer following the parsing rules below.

---

## **Parsing Rules**

### Rule 1 — Ignore Leading Whitespaces

Skip all leading spaces before processing begins.

Example:

```text id="m2v8zk"
"    42"
```

→ parsed value:

```text id="x7m1qa"
42
```

---

### Rule 2 — Optional Sign

The first non-space character may be:

* `+` → positive number
* `-` → negative number

If no sign exists, assume positive.

Only one optional sign is allowed.

If multiple consecutive signs appear, parsing fails.

Examples:

```text id="u3m8qp"
"+-12" → 0
"--5" → 0
```

A sign must be immediately followed by at least one digit.

---

### Rule 3 — Read Continuous Digits

Parse digits continuously until:

* a non-digit character is encountered
  OR
* end of string is reached

Example:

```text id="f9m1zk"
"4193 with words"
```

→ parsed integer:

```text id="r2m8vx"
4193
```

---

### Rule 4 — Invalid Beginning

If parsing cannot begin with a valid digit or sign-digit sequence, return:

```text id="n7m2qa"
0
```

Example:

```text id="p4m9xp"
"words and 987"
```

→ result:

```text id="v1m8zk"
0
```

---

### Rule 5 — 32-bit Overflow Handling

Clamp the result within signed 32-bit integer range:

```text id="g8m2vx"
[-2147483648, 2147483647]
```

If value exceeds upper bound:

```text id="x2m1qa"
2147483647
```

If value exceeds lower bound:

```text id="m9v2zk"
-2147483648
```

---

## **Input Format**

* First line: string **S**

---

## **Constraints**

* **1 ≤ |S| ≤ 10⁵**
* String may contain:

  * spaces
  * digits
  * lowercase letters
  * `+`
  * `-`
  * special characters

---

## **Output Format**

Print the parsed integer.

---

## **Sample Input 1**

```text id="k4m8qp"
42
```

---

## **Sample Output 1**

```text id="u7m1xp"
42
```

---

## **Explanation**

Valid numeric string parsed directly.

---

## **Sample Input 2**

```text id="m4k8qa"
   -42
```

---

## **Sample Output 2**

```text id="v8m2zk"
-42
```

---

## **Explanation**

Leading spaces ignored.

Negative sign processed successfully.

---

## **Sample Input 3**

```text id="x1m9vx"
4193 with words
```

---

## **Sample Output 3**

```text id="z7m2qp"
4193
```

---

## **Explanation**

Parsing stops when first non-digit character:

```text id="u4m8zk"
space
```

is encountered.

---

## **Sample Input 4**

```text id="k2m1qa"
words and 987
```

---

## **Sample Output 4**

```text id="r7m2zk"
0
```

---

## **Explanation**

Input does not begin with a valid numeric sequence.

Hence parsing fails.

---

## **Sample Input 5**

```text id="u1m8xp"
91283472332
```

---

## **Sample Output 5**

```text id="m4k8qa"
2147483647
```

---

## **Explanation**

Parsed value exceeds:

```text id="v8m2zk"
INT_MAX
```

Hence result is clamped to:

```text id="x1m9vx"
2147483647
```

---

## **Sample Input 6**

```text id="z7m2qp"
-91283472332
```

---

## **Sample Output 6**

```text id="u4m8zk"
-2147483648
```

---

## **Explanation**

Parsed value exceeds negative 32-bit boundary.

Hence result is clamped to:

```text id="k2m1qa"
-2147483648
```

---

## **Parsing Insight**

The parser processes the string sequentially:

1. Skip leading spaces
2. Detect optional sign
3. Read digits continuously
4. Stop at first invalid character
5. Check overflow before every digit insertion

---

## **Overflow Detection Logic**

Before appending next digit:

Check whether:

```text id="r7m2zk"
currentValue > INT_MAX / 10
```

OR:

```text id="u1m8xp"
currentValue == INT_MAX / 10
```

and next digit exceeds allowed boundary.

This prevents integer overflow during computation.

---

## **Efficient Strategy**

Use a single linear traversal with state tracking:

Maintain:

```text id="m4k8qa"
index
sign
result
```

Update result digit-by-digit while validating bounds.

---

## **Expected Complexity**

### Single Pass String Parsing

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(1)`

Where:

* `N` = length of input string

---

## **Execution Time Limit**

**10 seconds**