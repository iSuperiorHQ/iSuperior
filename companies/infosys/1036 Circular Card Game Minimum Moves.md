# **Problem 1036: Circular Card Game – Minimum Moves to Reach Target**

**Company:** Infosys

**Topic:** Arrays / Math

---

## **Problem Statement**

You are playing a circular card game with **N cards** placed in a circle. Each card has a **unique integer value**.

You start at a given **current position**, and your goal is to reach a card with a specific **target value**.

---

## **Movement Rules**

* You can move:

  * **Left (anti-clockwise)** → move to the previous card
  * **Right (clockwise)** → move to the next card
* The array is **circular**, meaning:

  * Moving right from the last card goes to the first
  * Moving left from the first card goes to the last

Each move (left or right by one position) counts as **1 step**.

---

## **Task**

Find the **minimum number of moves** required to reach the card with the given **target value**.

---

## **Input Format**

* The **first line** contains integer **N** (number of cards)
* The **second line** contains **N integers** representing the circular array
* The **third line** contains integer **startIndex** (0-based index)
* The **fourth line** contains integer **targetValue**

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* All elements in the array are **distinct**
* **0 ≤ startIndex < N**

---

## **Output Format**

Return an integer representing the **minimum number of moves** required.

---

## **Sample Input**

```text id="v8n2tx"
7
10 20 30 40 50 60 70
3
10
```

---

## **Sample Output**

```text id="d2h7qa"
3
```

---

## **Explanation**

Array (circular):

```text id="z7p1k3"
[10, 20, 30, 40, 50, 60, 70]
```

Start at index **3** → value = **40**

Target = **10** (index 0)

### Move Left:

```text id="q8n2xy"
3 → 2 → 1 → 0  (3 moves)
```

### Move Right:

```text id="b6k9zt"
3 → 4 → 5 → 6 → 0  (4 moves)
```

Minimum = **3 moves**

---

## **Sample Input 2**

```text id="r5t3mz"
5
1 2 3 4 5
0
4
```

---

## **Sample Output 2**

```text id="k1c9dz"
2
```

---

## **Explanation**

Start at index **0**

Target = **4 (index 3)**

* Right moves → 3 steps
* Left moves → 2 steps

Minimum = **2**

---

## **Key Insight**

* Find the index of the **target value**
* Compute:

  * **Clockwise distance**
  * **Anti-clockwise distance**
* Answer = **minimum of the two**

Time Complexity: **O(N)**

---

## **Execution Time Limit**

**10 seconds**