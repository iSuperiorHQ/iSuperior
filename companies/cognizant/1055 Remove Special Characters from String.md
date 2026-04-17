# **Problem 1055: Remove Special Characters from Alphanumeric String**

**Company:** Cognizant

**Topic:** Strings / Regex

---

## **Problem Description**

You are given a string that may contain **alphabets, digits, and special characters**.

Your task is to **remove all special characters** and retain only **alphanumeric characters** (letters and digits).

---

## **Task**

* Traverse the string
* Remove all characters that are **not letters (a–z, A–Z) or digits (0–9)**
* Return the cleaned string

---

## **Input Format**

* A single line containing the input string

---

## **Constraints**

* **1 ≤ length of string ≤ 10⁵**
* The string may contain letters, digits, spaces, and special symbols

---

## **Output Format**

* Print the **cleaned string** containing only alphanumeric characters

---

## **Sample Input 1**

```text id="c8m2xz"
a!b@c#123
```

---

## **Sample Output 1**

```text id="v3k9qp"
abc123
```

---

## **Explanation**

Special characters **!, @, #** are removed.

---

## **Sample Input 2**

```text id="m7x4zn"
hello_world@2024!
```

---

## **Sample Output 2**

```text id="r2p8kx"
helloworld2024
```

---

## **Explanation**

Special characters **_, @, !** are removed.

---

## **What they check:**

* String traversal and filtering
* Use of **regular expressions (optional)**
* Handling mixed character types
* Efficient processing for large inputs

---

## **Execution Time Limit**

**10 seconds**