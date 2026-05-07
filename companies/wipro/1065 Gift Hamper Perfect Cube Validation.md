# **Problem 1065: Gift Hamper Perfect Cube Validation**

**Company:** Wipro

**Topic:** Math / Number Theory

---

## **Problem Description**

A shopping platform creates premium gift hampers based on the total value of products purchased by a customer.

For a hamper to qualify for a special reward, the total purchase amount must form a **perfect cube**.

You are given the prices of all purchased products. Your task is to:

1. Calculate the total sum of all product prices
2. Determine whether the total sum is a perfect cube
3. If it is a perfect cube:

   * Print `"Yes"`
4. Otherwise:

   * Print `"No"` and the minimum positive integer amount that must be added to make the total sum become the next nearest perfect cube

---

## **Definition**

A number is called a perfect cube if it can be written as:

```text
x³
```

for some integer `x`.

Examples:

```text
1 = 1³
8 = 2³
27 = 3³
64 = 4³
```

---

## **Input Format**

* First line: integer **n** — number of purchased products
* Second line: **n integers** representing product prices

---

## **Constraints**

* **1 ≤ n ≤ 10⁵**
* **1 ≤ price[i] ≤ 10⁶**

---

## **Output Format**

* If the sum is a perfect cube, print:

```text
Yes
```

* Otherwise print:

```text
No
<minimum_amount>
```

---

## **Sample Input 1**

```text
3
1 8 18
```

---

## **Sample Output 1**

```text
Yes
```

---

## **Explanation**

```text
Total Sum = 1 + 8 + 18 = 27
27 = 3³
```

Hence the output is:

```text
Yes
```

---

## **Sample Input 2**

```text
3
5 10 20
```

---

## **Sample Output 2**

```text
No
29
```

---

## **Explanation**

```text
Total Sum = 35
```

Nearest perfect cube greater than 35:

```text
64 = 4³
```

Required amount:

```text
64 - 35 = 29
```

---

## **Sample Input 3**

```text
5
2 2 2 2 2
```

---

## **Sample Output 3**

```text
No
17
```

---

## **Explanation**

```text
Total Sum = 10
```

Next perfect cube:

```text
27 = 3³
```

Required amount:

```text
27 - 10 = 17
```

---

## **Key Insight**

* Compute total sum
* Find integer cube root:

```text
k = floor(cuberoot(sum))
```

* Check:

```text
k³ == sum
```

* Otherwise compute:

```text
(k+1)³ - sum
```

---

## **What they check:**

* Mathematical reasoning
* Perfect cube validation
* Precision handling for cube roots
* Large input efficiency

---

## **Execution Time Limit**

**10 seconds**