# **Problem 1016: 4 Keys Keyboard Sequence Optimization**

**Company:** Microsoft

**Topic:** Dynamic Programming

---

## **Problem Statement**

You are given a special keyboard with **only four keys**:

1. **Key 1:** Prints a single character `'A'` on the screen.
2. **Key 2 (Ctrl + A):** Selects all the characters currently on the screen.
3. **Key 3 (Ctrl + C):** Copies the selected characters to the clipboard.
4. **Key 4 (Ctrl + V):** Pastes the copied characters from the clipboard onto the screen.

---

### **Task**

You are given an integer **N**, representing the total number of key presses allowed.

Your goal is to determine the **maximum number of `'A'` characters** that can be printed on the screen using **exactly N key presses**.

---

### **Important Rules**

* Initially, the screen is empty.
* The clipboard is also empty.
* You can only paste (**Ctrl + V**) if something has already been copied.
* The sequence **Ctrl + A → Ctrl + C → Ctrl + V** is typically used to multiply characters efficiently.
* You must use **exactly N key presses**.

---

## **Input Format**

* A single integer **N**, representing the number of key presses.

---

## **Constraints**

* **1 ≤ N ≤ 100**

---

## **Output Format**

Return a single integer representing the **maximum number of 'A's** that can be printed.

---

## **Sample Input 1**

```
3
```

---

## **Sample Output 1**

```
3
```

---

## **Explanation**

Press `'A'` three times:

```
A → AA → AAA
```

---

## **Sample Input 2**

```
7
```

---

## **Sample Output 2**

```
9
```

---

## **Explanation**

Optimal sequence:

```
A → A → A → Ctrl+A → Ctrl+C → Ctrl+V → Ctrl+V
```

Steps:

* After 3 presses: **AAA**
* Copy and paste twice → **AAA + AAA + AAA = 9**

---

## **Key Insight**

Instead of typing `'A'` repeatedly, it is optimal to:

* Build some characters
* Then use **copy-paste operations** to multiply them

This problem requires identifying the **best breakpoint** where copying gives maximum gain.

---

## **Execution Time Limit**

**10 seconds**