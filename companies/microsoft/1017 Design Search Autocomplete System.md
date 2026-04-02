# **Problem 1017: Design Search Autocomplete System**

**Company:** Microsoft

**Topic:** Trie / Design / Heap / Hash Map

---

## **Problem Statement**

Design a system that provides **real-time search suggestions (autocomplete)** as a user types a query.

You are given:

* A list of **historical search queries (sentences)**
* An array of corresponding **frequencies**, representing how many times each sentence has been searched

Your task is to design an **AutocompleteSystem** that supports efficient querying.

---

## **Functional Requirements**

You need to implement the following operations:

### **Constructor**

```text
AutocompleteSystem(sentences, times)
```

* Initializes the system with historical data.
* `sentences[i]` has been searched `times[i]` times.

---

### **Input Function**

```text
input(c)
```

* Each call inputs a **single character `c`**.

* If `c != '#'`:

  * Return the **top 3 most frequent sentences** that match the current prefix.
  * Sort results by:

    1. **Highest frequency first**
    2. If tie → **lexicographically smaller sentence first**

* If `c == '#'`:

  * Treat the current input as a **complete sentence**.
  * Add it to the system (or update frequency).
  * Return an **empty list**.

---

## **Important Rules**

* Matching should be **prefix-based**.
* The system must be efficient for **large datasets**.
* Space and time optimization is expected (typical solution uses **Trie + Heap / Sorting**).

---

## **Input Format**

* The **first line** contains integer **n** (number of sentences).
* The **second line** contains **n sentences**.
* The **third line** contains **n integers** (frequencies).
* The next lines contain characters representing **input stream**.

---

## **Constraints**

* **1 ≤ n ≤ 10⁴**
* Total characters across all sentences ≤ **10⁵**
* Each sentence consists of lowercase letters and spaces
* At most **10⁵ input calls**

---

## **Output Format**

For every **input(c)** call (except `#`), return a list of **top 3 matching sentences**.

---

## **Sample Input**

```text
4
i love you
island
ironman
i love leetcode
5 3 2 2
i
 
a
#
i
 
l
#
```

---

## **Sample Output**

```text
["i love you","island","i love leetcode"]
["i love you","i love leetcode"]
[]
[]
["i love you","island","i love leetcode"]
["i love you","i love leetcode"]
[]
```

---

## **Explanation**

* After typing `"i"` → suggestions based on prefix `"i"`
* After typing `"i "` → suggestions update
* After typing `"#"` → sentence `"i a"` is stored
* Future queries reflect updated frequency

---

## **Key Insight**

To efficiently support queries:

* Use a **Trie (Prefix Tree)** to store sentences
* Maintain **frequency counts**
* Use **sorting or a heap** to retrieve top 3 results quickly

---

## **Execution Time Limit**

**10 seconds**