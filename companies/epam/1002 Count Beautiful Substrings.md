# **Problem 1002: Count Beautiful Substrings**

**Company:** EPAM

---

## **Problem Statement**

Davis loves playing with strings. So one day his friend Karen came with two strings **s** and **t** both consisting of only lowercase English letters. She asked him to count the number of different **beautiful substrings** present in **s**.

According to her, a substring is **beautiful** if we can make it equal to **t** by removing some characters from it (possibly zero) and then by rearranging the remaining substring.

Davis being expert in solving problems on string, gives the answer quickly and correctly. One more thing he loves is asking others to do the same things which he loves doing. This time he is asking you to solve this problem. Do the needful otherwise he will feel lonely.

**The answer may be large, so you must return the output as the answer modulo 1000000007.**

**NOTE:** Two substrings of a string are different if either their starting indices or their ending indices or both (starting as well as ending indices) are different.

---

## **Input Format**

* **1st line** contains string **s**.
* **2nd line** contains string **t**.

---

## **Constraints**

* **1 <= |s| <= 10^5**
* **1 <= |t| <= 10^5**

---

## **Output Format**

Output should contain an integer denoting the number of different **beautiful substrings** of string **s**.

---

## **Sample Testcases**

### **Input**

```
abcba
ab
```

### **Output**

```
7
```

---

## **Explanation**

The good substrings are:

* **abcba → ab**
* **abcba → abc → ab**
* **abcba → abcb → ab**
* **abcba → abcba → ab**
* **abcba → bcba → ba → ab**
* **abcba → cba → ba → ab**
* **abcba → ba → ab**

Therefore, the output will be:

```
(7 % 1000000007) = 7
```

---

## **Sample Input**

```
aab
ab
```

---

## **Sample Output**

```
2
```

---

## **Explanation**

The good substrings are those substrings of **s** which can be transformed into **t = "ab"** by removing characters and rearranging.

Total such substrings = **2**.