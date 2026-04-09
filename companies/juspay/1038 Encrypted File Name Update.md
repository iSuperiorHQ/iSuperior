# **Problem 1038: Encrypted File Name Update**

**Company:** Juspay

---

## **Problem Description**

In a cloud storage system, files are assigned encrypted names consisting of lowercase English letters. When a file is updated, its encrypted name must also be updated following strict rules:

1. The new file name must be exactly k characters long.

2. The new file name can only include characters that are present in the original file name.

3. The new file name must be lexicographically larger than the original file name. This means it should come later than the original name if they were arranged in alphabetical order.

---

Given the original file name, find the smallest possible new file name of length k that satisfies these conditions.

---

## **Input**

* The first line contains two integers n and k (1≤ n, k≤ 100,000) the length of the original file name and the length of the new file name.

* The second line contains a string s of n lowercase letters representing the original file name.

---

## **Output**

* Output the smallest possible new file name of length k that meets the requirements.

---

## **Note**

* A string p is lexicographically smaller than string q if p comes before q in the dictionary. For example, "abc" is smaller than "abcd", and "abd" is smaller than "abe".

---

## **Sample Input**

```text
3 3
abc
```

---

## **Sample Output**

```text
aca
```