# **Problem 1053: Dictionary-Based Password Attack Simulation**

**Company:** Cognizant

**Topic:** Backtracking / Strings

---

## **Problem Description**

In a cybersecurity system, a password is entered through a **numeric keylogger**, where each digit corresponds to a set of possible characters (similar to a mobile keypad).

An attacker is attempting a **dictionary-based password attack** by generating all possible character combinations from the numeric input and checking them against a known list of valid passwords (dictionary).

---

## **Key Mapping**

Each digit maps to characters as follows:

```text
2 → abc
3 → def
4 → ghi
5 → jkl
6 → mno
7 → pqrs
8 → tuv
9 → wxyz
```

Digits **0 and 1 do not map to any characters**.

---

## **Task**

* Given a numeric string and a list of valid passwords:

  1. Generate all possible combinations using keypad mapping
  2. Check which generated combinations exist in the dictionary
  3. Return all matching valid passwords

---

## **Input Format**

* First line: a string **digits** (numeric input)
* Second line: integer **n** (number of dictionary words)
* Next **n lines**: dictionary words

---

## **Constraints**

* **1 ≤ length of digits ≤ 10**
* **1 ≤ n ≤ 10⁴**
* Dictionary words consist of lowercase English letters

---

## **Output Format**

* Print all matching valid passwords in **lexicographical order**
* If no match is found, print **"No match found"**

---

## **Sample Input**

```text
23
5
ad
ae
bd
cf
xyz
```

---

## **Sample Output**

```text
ad
ae
bd
cf
```

---

## **Explanation**

Digits = **"23"**

Possible combinations:

```text
ad, ae, af, bd, be, bf, cd, ce, cf
```

Matching dictionary words:

```text
ad, ae, bd, cf
```

---

## **What they check:**

* Backtracking (generating combinations)
* Efficient lookup using **Hash Set**
* String generation and recursion
* Handling edge cases like invalid digits

---

## **Execution Time Limit**

**10 seconds**