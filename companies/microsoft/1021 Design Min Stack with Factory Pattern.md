# **Problem 1021: Design Min Stack with Factory Pattern**

**Company:** Microsoft

**Topic:** Stack / Design Pattern (Factory) / OOP

---

## **Problem Statement**

Design a stack data structure that supports standard stack operations along with retrieving the **minimum element in constant time (O(1))**.

In addition, you must implement the stack using the **Factory Design Pattern**, allowing the system to create different types of stack implementations dynamically.

---

## **Functional Requirements**

You need to support the following operations:

* **push(x)** → Push element **x** onto the stack
* **pop()** → Removes the element on top of the stack
* **top()** → Returns the top element
* **getMin()** → Returns the **minimum element** in the stack

All operations must run in **O(1) time complexity**.

---

## **Factory Requirement**

Implement a **StackFactory** that can create different stack types:

### Example Stack Types

* **MinStack** → Supports `getMin()` in O(1)
* **SimpleStack** → Basic stack without min tracking

---

### Factory Method Example

```text id="q1n8rs"
createStack(type)
```

* If type = `"min"` → return MinStack instance
* If type = `"simple"` → return SimpleStack instance

---

## **Input Format**

* The first line contains a string **type** (`"min"` or `"simple"`)
* The next lines contain operations:

```text id="3u9a6h"
push x
pop
top
getMin
```

---

## **Constraints**

* **1 ≤ number of operations ≤ 10⁵**
* **-10⁹ ≤ x ≤ 10⁹**

---

## **Output Format**

* For each **top()** or **getMin()** operation, print the result.

---

## **Sample Input**

```text id="bz5f2x"
min
push 5
push 2
push 8
getMin
pop
getMin
top
```

---

## **Sample Output**

```text id="k4w8a1"
2
2
2
```

---

## **Explanation**

Operations:

* push(5) → stack = [5]

* push(2) → stack = [5,2]

* push(8) → stack = [5,2,8]

* getMin() → **2**

* pop() → removes 8

* getMin() → **2**

* top() → **2**

---

## **Key Insight**

To achieve **O(1) getMin()**, maintain:

* A **second stack** that keeps track of minimum values
  OR
* Store pairs `{value, currentMin}` in stack

Factory Pattern:

* Separates **object creation logic**
* Makes system **extensible and scalable**

---

## **Execution Time Limit**

**10 seconds**