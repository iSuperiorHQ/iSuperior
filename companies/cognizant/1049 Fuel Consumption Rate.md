# **Problem 1049: Calculate Fuel Consumption Rate**

**Company:** Cognizant

**Topic:** Basic Math / Logic

---

## **Problem Description**

A vehicle’s fuel efficiency is measured based on the distance it travels and the amount of diesel it consumes.

You are given:

* The total **distance traveled (in kilometers)**
* The total **diesel consumed (in liters)**

Your task is to calculate the **fuel consumption rate** of the vehicle.

---

## **Task**

* Compute the fuel consumption rate using the formula:

```text id="6k1v9m"
Fuel Efficiency = Distance / Diesel
```

* Return the result with **exact precision up to 2 decimal places**

---

## **Input Format**

* The first line contains an integer **distance** (in kilometers)
* The second line contains an integer **diesel** (in liters)

---

## **Constraints**

* **1 ≤ distance ≤ 10⁶**
* **1 ≤ diesel ≤ 10⁶**

---

## **Output Format**

* Print the fuel efficiency (km per liter) up to **2 decimal places**

---

## **Sample Input 1**

```text id="9l2c5v"
150
5
```

---

## **Sample Output 1**

```text id="7h3m8x"
30.00
```

---

## **Explanation**

Distance = 150 km
Diesel = 5 liters

Fuel efficiency:

```text id="p4k2qz"
150 / 5 = 30.00 km/l
```

---

## **Sample Input 2**

```text id="u8x3np"
275
10
```

---

## **Sample Output 2**

```text id="w2m7qa"
27.50
```

---

## **Explanation**

Fuel efficiency:

```text id="a9k5rd"
275 / 10 = 27.50 km/l
```

---

## **What they check:**

* Correct **formula implementation**
* Proper **floating-point precision (2 decimal places)**
* Handling division correctly

---

## **Execution Time Limit**

**10 seconds**