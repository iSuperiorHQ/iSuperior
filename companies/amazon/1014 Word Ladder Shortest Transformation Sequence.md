# **Problem 1014: Word Ladder Shortest Transformation Sequence**

**Company:** Amazon

**Topic:** Graph / BFS

---

## **Problem Statement**

You are given two words:

* **beginWord**
* **endWord**

and a dictionary **wordList**.

A transformation sequence from **beginWord** to **endWord** must follow these rules:

* Only **one letter can be changed at a time**.
* Each transformed word must exist in **wordList**.

Return the **length of the shortest transformation sequence** from **beginWord to endWord**.

If no such sequence exists, return **0**.

---

## **Input Format**

* The **first line** contains **beginWord**
* The **second line** contains **endWord**
* The **third line** contains integer **n** (size of wordList)
* The next **n lines** contain words in the dictionary.

---

## **Constraints**

* **1 ≤ n ≤ 5000**
* Each word has the **same length**
* Words consist of **lowercase letters**

---

## **Output Format**

Return an integer representing the **length of the shortest transformation sequence**.

---

## **Sample Input**

```
hit
cog
6
hot
dot
dog
lot
log
cog
```

---

## **Sample Output**

```
5
```

---

## **Explanation**

The shortest transformation sequence is:

```
hit → hot → dot → dog → cog
```

Length = **5**

---

## **Execution Time Limit**

**10 seconds**