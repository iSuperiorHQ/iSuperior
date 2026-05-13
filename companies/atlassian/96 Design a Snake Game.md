# **Problem 96: Design a Snake Game**

**Company:** Atlassian

**Category:** Low-Level Design (LLD) / Machine Coding

**Difficulty:** Hard

---

# **Problem Description**

A gaming platform is developing an online multiplayer arcade engine and needs to implement the core mechanics of the classic:

```text id="m2v8zk"
Snake Game
```

The game operates on a 2D rectangular grid where:

* the snake moves continuously
* food appears dynamically on the board
* the snake grows after consuming food
* collisions terminate the game

Your task is to design and implement the complete backend game engine responsible for:

* snake movement
* body tracking
* food generation
* collision detection
* score management
* game state updates

The implementation should be modular, object-oriented, extensible, and optimized for real-time gameplay.

---

# **Game Rules**

## Initial State

* Snake starts at the top-left corner:

```text id="x7m1qa"
(0,0)
```

* Initial snake length:

```text id="u3m8qp"
1
```

* Initial movement direction:

```text id="f9m1zk"
RIGHT
```

---

# **Movement Rules**

At every move, the snake can move in one of four directions:

| Direction | Row Change | Column Change |
| --------- | ---------- | ------------- |
| `UP`      | -1         | 0             |
| `DOWN`    | +1         | 0             |
| `LEFT`    | 0          | -1            |
| `RIGHT`   | 0          | +1            |

---

# **Food Rules**

* Food appears at predefined coordinates
* When snake reaches food:

  * score increases by `1`
  * snake length increases
  * tail does not move for that turn

---

# **Collision Rules**

The game ends immediately if:

* snake hits boundary walls
  OR
* snake collides with itself

---

# **Task**

Design a Snake Game engine supporting the following operations:

| Operation                | Description                           |
| ------------------------ | ------------------------------------- |
| `move(direction)`        | Moves snake and returns current score |
| `generateFood(position)` | Places food on board                  |
| `isGameOver()`           | Returns game state                    |
| `getScore()`             | Returns current score                 |

---

# **Input Format**

First line contains:

```text id="r2m8vx"
rows cols
```

representing board dimensions.

Second line contains:

```text id="n7m2qa"
F
```

representing number of food positions.

Next `F` lines contain:

```text id="p4m9xp"
row col
```

food coordinates in order of appearance.

Next line contains:

```text id="v1m8zk"
M
```

representing total moves.

Next `M` lines contain one direction:

```text id="g8m2vx"
UP
DOWN
LEFT
RIGHT
```

---

# **Output Format**

For every move print:

* current score after move
  OR

```text id="x2m1qa"
GAME OVER
```

if collision occurs.

After game over, remaining moves should not be processed.

---

# **Constraints**

* **1 ≤ rows, cols ≤ 10⁴**
* **1 ≤ M ≤ 10⁵**
* **0 ≤ F ≤ 10⁵**

---

# **Sample Input 1**

```text id="m9v2zk"
3 3
2
0 1
0 2
5
RIGHT
RIGHT
DOWN
LEFT
UP
```

---

# **Sample Output 1**

```text id="k4m8qp"
1
2
2
2
GAME OVER
```

---

# **Explanation**

Initial snake:

```text id="u7m1xp"
[(0,0)]
```

Move 1:

```text id="m4k8qa"
RIGHT → (0,1)
```

Food consumed.

Score:

```text id="v8m2zk"
1
```

Snake:

```text id="x1m9vx"
[(0,1),(0,0)]
```

---

Move 2:

```text id="z7m2qp"
RIGHT → (0,2)
```

Food consumed again.

Score:

```text id="u4m8zk"
2
```

Snake:

```text id="k2m1qa"
[(0,2),(0,1),(0,0)]
```

---

Move 3:

```text id="r7m2zk"
DOWN → (1,2)
```

No food consumed.

Tail moves normally.

---

Move 4:

```text id="u1m8xp"
LEFT → (1,1)
```

Valid movement.

---

Move 5:

```text id="m4k8qa"
UP → (0,1)
```

Snake collides with its own body.

Game terminates.

---

# **Sample Input 2**

```text id="v8m2zk"
2 2
1
1 1
4
RIGHT
DOWN
LEFT
UP
```

---

# **Sample Output 2**

```text id="x1m9vx"
0
1
1
1
```

---

# **Explanation**

Initial snake:

```text id="z7m2qp"
[(0,0)]
```

Move 1:

```text id="u4m8zk"
RIGHT → (0,1)
```

No food consumed.

Score:

```text id="k2m1qa"
0
```

---

Move 2:

```text id="r7m2zk"
DOWN → (1,1)
```

Food consumed.

Snake grows.

Score:

```text id="u1m8xp"
1
```

---

Move 3:

```text id="m4k8qa"
LEFT → (1,0)
```

Tail moves normally.

Score remains:

```text id="v8m2zk"
1
```

---

Move 4:

```text id="x1m9vx"
UP → (0,0)
```

Tail has already moved away, so no collision occurs.

Score remains:

```text id="z7m2qp"
1
```

---

# **Sample Input 3**

```text id="u4m8zk"
2 3
0
4
RIGHT
RIGHT
RIGHT
DOWN
```

---

# **Sample Output 3**

```text id="k2m1qa"
0
0
GAME OVER
```

---

# **Explanation**

Third move attempts boundary crossing:

```text id="r7m2zk"
(0,3)
```

which lies outside board dimensions.

Game terminates immediately.

Remaining moves are ignored.

---

# **Recommended Data Structures**

| Structure    | Purpose                           |
| ------------ | --------------------------------- |
| `Deque`      | Efficient snake head/tail updates |
| `HashSet`    | O(1) self-collision detection     |
| `Queue/List` | Food management                   |

---

# **Object-Oriented Design Expectations**

Recommended classes:

| Class         | Responsibility           |
| ------------- | ------------------------ |
| `SnakeGame`   | Main game engine         |
| `Snake`       | Snake state and movement |
| `Board`       | Grid management          |
| `FoodManager` | Food generation          |
| `Position`    | Coordinate abstraction   |

---

# **Important Edge Cases**

Your implementation should correctly handle:

* moving into current tail position
* consecutive food consumption
* boundary collisions
* self-collision after growth
* empty food list
* large board sizes

---

# **Efficient Strategy**

Maintain:

* snake body in deque
* occupied cells in hash set
* food index pointer

For every move:

1. Compute next head position
2. Check wall collision
3. Remove tail temporarily (if not eating food)
4. Detect self-collision
5. Insert new head
6. Update score if food consumed

---

# **Expected Complexity**

## Optimized Deque + HashSet Design

### Time Complexity

* **O(1)** per move

---

### Space Complexity

* **O(S + F)**

Where:

* `S` = current snake length
* `F` = total food positions

---

# **Bonus Follow-Up Questions**

Interviewers may ask:

* How would you support multiplayer snakes?
* How would you persist game state?
* How would you implement pause/resume?
* How would you synchronize online gameplay?
* How would you render efficiently on frontend?

---

# **Execution Time Limit**

**10 seconds**