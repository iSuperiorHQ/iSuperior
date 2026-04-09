# **Problem 1040: Parking Lot Arrangement**

**Company:** Juspay

---

## **Problem Description**

You are managing a parking lot with n linear parking spaces. Due to a random arrangement, the cars are parked at scattered locations within the lot. Your task is to rearrange the cars so they occupy consecutive parking spaces to optimize parking efficiency.

---

## **Input**

* The first line contains an integer n, the number of cars currently in the parking lot.

* The next line contains n unique integers, representing the current positions of the cars in the lot. These positions are unique.

---

## **Output**

* Print a single integer: the minimum number of moves required to group all the cars into consecutive parking spaces.

---

## **Constraints**

* **1 ≤ n ≤ 100,000**
* Each position is a non-negative integer fitting within a 32-bit signed integer range.

---

## **Explanation**

Initial Positions:

```text id="5m3zqv"
[7, 9, 10, 13]
```

Step 1: Move the car from position 7 to position 8. (1 move)
Step 2: Move the car from position 13 to position 11. (1 move)

Resulting Positions:

```text id="p2n8ra"
[8, 9, 10, 11]
```

These are consecutive parking spaces.

Number of Moves: This arrangement was achieved in **2 moves**.

---

## **Sample Input**

```text id="6k9rzt"
4
3 5 7 9
```

---

## **Sample Output**

```text id="n2x4qj"
2
```