# **Problem 1044: Grocery Store Discount**

**Company:** TCS

**Topic:** Conditions / Math

---

## **Problem Description**

A grocery store gives discount based on purchase amount:

* Amount < 1000 → 5% discount
* Amount ≥ 1000 and ≤ 5000 → 10% discount
* Amount > 5000 → 15% discount

Print the final payable amount after discount

---

## **Example 1**

### **Input:**

```
1200
```

### **Step-by-step calculation:**

1200 falls between 1000 and 5000 → 10% discount

10% of 1200 = 120
Final Amount = 1200 - 120 = 1080

**Output:** 1080

---

## **Example 2**

### **Input:**

```
600
```

### **Step-by-step calculation:**

600 is less than 1000 → 5% discount

5% of 600 = 30
Final Amount = 600 - 30 = 570

**Output:** 570

---

## **What they check:**

* Correct condition ranges (very important)
* Percentage calculation
* Edge cases like 1000 and 5000