# **Problem 1033: RPG Monster Game – Maximize Defeated Monsters**

**Company:** Infosys

**Topic:** Greedy / Sorting

---

## **Problem Statement**

You are developing a feature for an RPG game where a player must defeat monsters to gain experience and progress through levels.

The player starts with an initial **experience value `E`**.

There are **N monsters** in the game. Each monster is described by:

* **Minimum experience required** to fight the monster
* **Experience gained** after defeating the monster

---

### **Objective**

Determine the **maximum number of monsters** the player can defeat.

---

### **Game Rules**

* A monster can only be defeated if the player’s current experience **is greater than or equal to** the monster’s required experience.
* After defeating a monster, the player’s experience **increases by the reward value**.
* Each monster can be defeated **only once**.
* The player can choose to fight monsters in **any order**.

---

## **Input Format**

* The **first line** contains an integer **N** — number of monsters
* The **second line** contains an integer **E** — initial experience
* The next **N lines** each contain two integers:

```text
required_experience reward_experience
```

---

## **Constraints**

* **1 ≤ N ≤ 10⁵**
* **0 ≤ E ≤ 10⁹**
* **0 ≤ required_experience, reward_experience ≤ 10⁹**

---

## **Output Format**

Print a single integer representing the **maximum number of monsters the player can defeat**.

---

## **Sample Input**

```text
6
10
5 4
9 2
12 6
15 10
8 3
20 5
```

---

## **Sample Output**

```text
5
```

---

## **Explanation**

Initial experience = **10**

Reorder monsters optimally:

```text
(5,4), (8,3), (9,2), (12,6), (15,10), (20,5)
```

Step-by-step:

* Defeat (5,4) → E = 14
* Defeat (8,3) → E = 17
* Defeat (9,2) → E = 19
* Defeat (12,6) → E = 25
* Defeat (15,10) → E = 35

Now 5 monsters are defeated.

---

## **Key Insight**

* Sort monsters by **required experience**
* Always pick monsters that are **currently defeatable**
* Greedy approach ensures maximum progression

---

## **Execution Time Limit**

**10 seconds**