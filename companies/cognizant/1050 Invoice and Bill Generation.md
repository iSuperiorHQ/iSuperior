# **Problem 1050: Dynamic Invoice and Bill Generation**

**Company:** Cognizant

**Topic:** Arrays / Formatting

---

## **Problem Description**

You are developing a billing system for a retail store. The system must generate a properly formatted invoice based on purchased items.

Each item has:

* **Item Name**
* **Quantity Purchased**
* **Price per Unit**

The system should calculate totals and generate a clean invoice format.

---

## **Task**

Given the details of items purchased:

1. Calculate the **total cost for each item**
2. Calculate the **overall total bill amount**
3. Display the invoice in a structured format

---

## **Input Format**

* The first line contains an integer **n** — number of items
* The next **n lines** each contain:

```text id="6y9q3k"
item_name quantity price
```

---

## **Constraints**

* **1 ≤ n ≤ 1000**
* **1 ≤ quantity ≤ 100**
* **1 ≤ price ≤ 10⁵**

---

## **Output Format**

Print the invoice in the following format:

* Each line should display:

```text id="n8r2xp"
ItemName Quantity Price TotalPrice
```

* The last line should display:

```text id="q3t7zl"
Total Amount: <sum>
```

---

## **Sample Input**

```text id="p2x8qm"
3
Apple 2 50
Milk 1 40
Bread 3 20
```

---

## **Sample Output**

```text id="x7m4kr"
Apple 2 50 100
Milk 1 40 40
Bread 3 20 60
Total Amount: 200
```

---

## **Explanation**

* Apple → 2 × 50 = 100
* Milk → 1 × 40 = 40
* Bread → 3 × 20 = 60

Total = **100 + 40 + 60 = 200**

---

## **What they check:**

* Correct **input parsing (strings + integers)**
* Proper **calculation of totals**
* Clean **output formatting**
* Handling multiple records using arrays

---

## **Execution Time Limit**

**10 seconds**