# **Problem 1062: Advanced Password Validation with Strict Constraints**

**Company:** Accenture

**Topic:** Strings / Validation

---

## **Problem Description**

A secure authentication system enforces strict password policies to ensure strong user credentials.

You are given a password string. Your task is to validate whether it satisfies **all security rules**.

---

## **Validation Rules**

A password is considered **valid** only if it satisfies all of the following conditions:

1. **Length Constraint**

   * Minimum length = **8 characters**
   * Maximum length = **32 characters**

2. **Character Requirements**

   * Must contain **at least one uppercase letter (A–Z)**
   * Must contain **at least one lowercase letter (a–z)**
   * Must contain **at least one digit (0–9)**
   * Must contain **at least one special character** from:

```text
! @ # $ % ^ & * ( ) - +
```

3. **No Repeated Consecutive Characters**

   * No character should appear **3 or more times consecutively**

4. **No Spaces Allowed**

   * Password must not contain whitespace

---

## **Task**

Return:

* **"Valid"** → if the password satisfies all conditions
* **"Invalid"** → otherwise

---

## **Input Format**

* A single string representing the password

---

## **Constraints**

* **1 ≤ length ≤ 100**

---

## **Output Format**

* Print **Valid** or **Invalid**

---

## **Sample Input 1**

```text
Abc@1234
```

---

## **Sample Output 1**

```text
Valid
```

---

## **Explanation**

* Length ≥ 8
* Contains uppercase, lowercase, digit, special character
* No invalid repetition
* No spaces

---

## **Sample Input 2**

```text
abc12345
```

---

## **Sample Output 2**

```text
Invalid
```

---

## **Explanation**

* Missing uppercase letter
* Missing special character

---

## **Sample Input 3**

```text
AAAabc@12
```

---

## **Sample Output 3**

```text
Invalid
```

---

## **Explanation**

* Contains **AAA** → repeated character more than twice consecutively

---

## **Sample Input 4**

```text
Ab@1
```

---

## **Sample Output 4**

```text
Invalid
```

---

## **Explanation**

* Length less than 8

---

## **Key Insight**

* Can be solved using:

  * **Regex + manual checks**
  * OR full manual traversal for better control
* Important to validate:

  * Character categories
  * Consecutive repetition
  * Length constraints

---

## **What they check:**

* Strong understanding of **string validation logic**
* Ability to combine **multiple constraints**
* Regex knowledge (optional but expected)
* Edge case handling

---

## **Execution Time Limit**

**10 seconds**