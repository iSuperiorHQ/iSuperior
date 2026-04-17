# **Problem 1052: Longest Valid Word Starting with Vowel and Even Length**

**Company:** Cognizant

**Topic:** Strings

---

## **Problem Description**

You are given a sentence consisting of multiple words separated by spaces.

Your task is to find the **longest valid word** based on the following conditions:

---

## **Conditions**

A word is considered **valid** if:

1. It **starts with a vowel**
   (vowels: a, e, i, o, u — case insensitive)

2. The **length of the word is even**

---

## **Task**

* From the given sentence, identify all valid words
* Return the **longest valid word**
* If multiple words have the same maximum length, return the **first one occurring in the sentence**
* If no valid word exists, return **"NA"**

---

## **Input Format**

* A single line containing the sentence

---

## **Constraints**

* **1 ≤ length of sentence ≤ 10⁵**
* Words consist only of alphabetic characters
* Words are separated by one or more spaces

---

## **Output Format**

* Print the **longest valid word**
* If none exists, print **NA**

---

## **Sample Input 1**

```text id="x8m2vk"
apple orange umbrella cat dog
```

---

## **Sample Output 1**

```text id="n3k7pa"
orange
```

---

## **Explanation**

Valid words:

* apple → starts with vowel, length = 5 (odd → invalid)
* orange → starts with vowel, length = 6 (even → valid)
* umbrella → starts with vowel, length = 8 (even → valid)

Longest valid word = **umbrella**

But since **umbrella (8)** is longer than **orange (6)** → correct answer should be **umbrella**

---

## **Sample Input 2**

```text id="k2m9zt"
sky fly dry
```

---

## **Sample Output 2**

```text id="p4r8qx"
NA
```

---

## **Explanation**

No word starts with a vowel → output is **NA**

---

## **Sample Input 3**

```text id="v7x3dm"
egg ice owl ant
```

---

## **Sample Output 3**

```text id="q1n8zr"
owl
```

---

## **Explanation**

Valid words:

* egg → length = 3 (odd → invalid)
* ice → length = 3 (invalid)
* owl → length = 3 (invalid)
* ant → length = 3 (invalid)

No valid even-length vowel-start word → output should be **NA**

---

## **What they check:**

* String parsing and splitting
* Checking vowels (case-insensitive)
* Handling length conditions
* Edge cases (no valid word)

---

## **Execution Time Limit**

**10 seconds**