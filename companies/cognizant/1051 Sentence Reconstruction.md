# **Problem 1051: Sentence Reconstruction with Standard Formatting**

**Company:** Cognizant

**Topic:** Strings / Parsing

---

## **Problem Description**

You are given a sentence that may contain **extra spaces**, inconsistent formatting, and incorrect capitalization.

Your task is to **reconstruct the sentence** by applying standard formatting rules.

---

## **Formatting Rules**

1. Remove **leading and trailing spaces**
2. Replace multiple spaces between words with a **single space**
3. Convert the **first character of the sentence to uppercase**
4. Convert all remaining characters to **lowercase**

---

## **Task**

Given an input string, return the **properly formatted sentence** after applying all rules.

---

## **Input Format**

* A single line containing the input sentence

---

## **Constraints**

* **1 ≤ length of string ≤ 10⁵**
* The string may contain uppercase letters, lowercase letters, and spaces

---

## **Output Format**

* Print the **reconstructed sentence**

---

## **Sample Input 1**

```text id="n8r2qa"
   hELLo    WoRLD   
```

---

## **Sample Output 1**

```text id="x4m9zt"
Hello world
```

---

## **Explanation**

* Removed extra spaces
* Converted first letter to uppercase
* Converted remaining letters to lowercase

---

## **Sample Input 2**

```text id="q7m3lp"
   tHiS   IS    a    TeST   
```

---

## **Sample Output 2**

```text id="k2x8vd"
This is a test
```

---

## **What they check:**

* Proper **string trimming and splitting**
* Handling **multiple spaces correctly**
* Correct **case transformation logic**
* Edge cases like empty or single-word input

---

## **Execution Time Limit**

**10 seconds**