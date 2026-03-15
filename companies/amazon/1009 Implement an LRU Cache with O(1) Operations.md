# **Problem 1009: Implement an LRU Cache with O(1) Operations**

**Company:** Amazon

**Topic:** Linked List & Hash Map

---

## **Problem Statement**

Design a data structure that follows the constraints of a **Least Recently Used (LRU) Cache**.

Implement the **LRUCache** class with the following operations:

* **get(key)** → Returns the value of the key if the key exists in the cache, otherwise return **-1**.
* **put(key, value)** → Update the value of the key if it exists. Otherwise, add the key-value pair to the cache.

If the cache reaches its **capacity**, it should **remove the least recently used item** before inserting a new item.

Both operations must run in **O(1) time complexity**.

---

## **Input Format**

* The **first line** contains an integer **capacity**.
* The next lines contain operations:

```
put key value
get key
```

---

## **Constraints**

* **1 ≤ capacity ≤ 10⁴**
* **0 ≤ key ≤ 10⁵**
* **0 ≤ value ≤ 10⁵**
* At most **10⁵ operations**

---

## **Output Format**

For every **get operation**, output the returned value.

---

## **Sample Input**

```
2
put 1 1
put 2 2
get 1
put 3 3
get 2
put 4 4
get 1
get 3
get 4
```

---

## **Sample Output**

```
1
-1
-1
3
4
```

---

## **Explanation**

Cache capacity = **2**

Operations performed according to **LRU policy**.

---

## **Execution Time Limit**

**10 seconds**