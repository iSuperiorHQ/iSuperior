# **Problem 1090: Valid Palindrome with One Deletion**

**Company:** Adobe

**Topic:** Two Pointers

**Difficulty:** Easy / Medium

---

## **Problem Description**

A document verification system checks whether encrypted textual identifiers preserve symmetric integrity.

A string is considered:

```text id="m2v8zk"
Palindrome Valid
```

if it reads the same from:

* Left to right
* Right to left

However, due to transmission corruption, at most:

```text id="x7m1qa"
One Character
```

may be incorrectly inserted into the string.

Your task is to determine whether the string can become a valid palindrome after deleting at most one character.

---

## **Task**

Given a lowercase string `S`, determine whether it can be transformed into a palindrome by removing:

* zero characters
  OR
* exactly one character

Return:

```text id="u3m8qp"
true
```

if possible.

Otherwise return:

```text id="f9m1zk"
false
```

---

## **Important Notes**

* Deletion can occur at any index
* Only one deletion is allowed
* Empty strings formed after deletion are considered valid palindromes

---

## **Input Format**

* First line: string **S**

---

## **Constraints**

* **1 ≤ |S| ≤ 10⁵**
* String contains lowercase English letters only

---

## **Output Format**

Print:

```text id="r2m8vx"
true
```

or

```text id="n7m2qa"
false
```

---

## **Sample Input 1**

```text id="p4m9xp"
abca
```

---

## **Sample Output 1**

```text id="v1m8zk"
true
```

---

## **Explanation**

Delete character:

```text id="g8m2vx"
c
```

Resulting string:

```text id="x2m1qa"
aba
```

which is a palindrome.

---

## **Sample Input 2**

```text id="m9v2zk"
raceacar
```

---

## **Sample Output 2**

```text id="k4m8qp"
true
```

---

## **Explanation**

Delete character:

```text id="u7m1xp"
a
```

Resulting string:

```text id="m4k8qa"
racecar
```

which is a palindrome.

---

## **Sample Input 3**

```text id="v8m2zk"
abcdef
```

---

## **Sample Output 3**

```text id="x1m9vx"
false
```

---

## **Explanation**

No single deletion can make the string symmetric.

---

## **Sample Input 4**

```text id="z7m2qp"
deeee
```

---

## **Sample Output 4**

```text id="u4m8zk"
true
```

---

## **Explanation**

Delete character:

```text id="k2m1qa"
d
```

Resulting string:

```text id="r7m2zk"
eeee
```

which is a palindrome.

---

## **Two Pointer Insight**

Maintain:

```text id="u1m8xp"
leftPointer
rightPointer
```

Compare characters from both ends.

### Case 1

If characters match:

```text id="m4k8qa"
Move inward
```

### Case 2

If mismatch occurs:

Attempt either:

* Skip left character
  OR
* Skip right character

Then verify whether the remaining substring forms a palindrome.

Only one mismatch correction is allowed.

---

## **Efficient Strategy**

At the first mismatch:

Check:

```text id="v8m2zk"
isPalindrome(left+1, right)
```

OR

```text id="x1m9vx"
isPalindrome(left, right-1)
```

If either succeeds:

```text id="z7m2qp"
true
```

Otherwise:

```text id="u4m8zk"
false
```

---

## **Expected Complexity**

### Two Pointer Traversal

* **Time Complexity:** `O(N)`
* **Space Complexity:** `O(1)`

Where:

* `N` = length of string

---

## **Execution Time Limit**

**10 seconds**