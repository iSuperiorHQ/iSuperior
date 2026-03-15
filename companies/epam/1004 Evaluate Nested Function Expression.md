# **Problem 1004: Evaluate Nested Function Expression**

**Company:** EPAM

---

## **Problem Statement**

You are given an expression as a string that may include **function calls**. Each function call is in the form:

```
funcName(arg1, arg2, ...)
```

The arguments can be **literals (numbers)** or **nested function calls**.

Your task is to **evaluate the expression and return the result**.

The function name can be one of the following **4 types**:

* **add(arg1, arg2)** : Adds **arg1** and **arg2** together.
  Example:

  ```
  add(2, 3) → 5
  ```

* **sub(arg1, arg2)** : Subtracts **arg2** from **arg1**.
  Example:

  ```
  sub(5, 2) → 3
  ```

* **mul(arg1, arg2)** : Multiplies **arg1** by **arg2**.
  Example:

  ```
  mul(3, 4) → 12
  ```

* **div(arg1, arg2)** : Performs **integer division** of **arg1** by **arg2**.
  Example:

  ```
  div(20, 4) → 5
  ```

---

## **Input Format**

* A **single line** containing the string **expr**.

---

## **Constraints**

* **1 <= expr.length < 1000**
* **1 <= arg1, arg2 <= 1000**

---

## **Output Format**

Return the **integer containing the value after the expression is evaluated**.

---

## **Evaluation Parameters**

### **Sample Input**

```
add(2, mul(3, 4))
```

### **Sample Output**

```
14
```

---

## **Explanation**

* **mul(3, 4)** evaluates to **12**
* **add(2, 12)** evaluates to **14**

---

## **Execution Time Limit**

**4 seconds**