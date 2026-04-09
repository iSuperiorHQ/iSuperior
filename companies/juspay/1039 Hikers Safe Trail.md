# **Problem 1039: Hikers Safe Trail**

**Company:** Juspay

---

## **Problem Description**

In the mountainous region of Montvalley, a hiker named Alex is planning to explore the beautiful hiking trails. The region's trail network is structured as a rooted tree with n nodes, with the main camp located at node 1. This camp also serves as the starting point for all trails.

The trails in the region are known to have dangerous cliff sections. Each node on the tree represents a point along a trail and can either be safe or dangerous. The leaves of the tree (nodes with no further connections) represent scenic viewpoints, which are Alex's desired destinations.

However, Alex is cautious and will avoid any viewpoint if the path from the main camp to that viewpoint contains more than m consecutive dangerous cliff sections.

Your task is to help Alex count the number of viewpoints (leaf nodes) he can safely visit.

---

## **Input**

The input consists of:

1. The first line contains two integers, n and m (2 ≤ n ≤ 100,000, 1 ≤ m ≤ n) — the number of nodes in the tree and the maximum number of consecutive dangerous sections Alex is willing to traverse.

2. The second line contains n integers, s₁, s₂, ..., sₙ, where each sᵢ is either:

   * 0 → the node is safe
   * 1 → the node is dangerous

3. The next n-1 lines each contain two integers xᵢ and yᵢ (1 ≤ xᵢ, yᵢ ≤ n, xᵢ ≠ yᵢ), representing an edge between nodes xᵢ and yᵢ.

It is guaranteed that the edges form a tree structure.

---

## **Output**

* Output a single integer — the number of viewpoints (leaf nodes) where the path from the main camp (node 1) contains at most m consecutive dangerous sections.

---

## **Sample Input**

```text
7 3
1 1 1 1 1 0 1
1 2
1 3
2 4
3 5
5 6
6 7
```

---

## **Sample Output**

```text
2
```