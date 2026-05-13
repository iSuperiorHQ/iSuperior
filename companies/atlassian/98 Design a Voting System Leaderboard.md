# **Problem 98: Design a Voting System / Leaderboard**

**Company:** Atlassian

**Category:** Low-Level Design (LLD) / Machine Coding

**Difficulty:** Hard

---

# **Problem Description**

A large-scale online competition platform allows millions of users to vote for candidates in real time.

The platform requires an in-memory leaderboard system capable of:

* accepting votes dynamically
* updating candidate rankings instantly
* retrieving top-performing candidates efficiently
* preventing duplicate voting abuse
* handling large-scale concurrent traffic

Your task is to design and implement a modular, object-oriented voting system capable of maintaining a live leaderboard.

The system should support efficient updates and fast retrieval of the top `K` candidates at any moment.

---

# **Functional Requirements**

The voting system should support:

* registering candidates
* casting votes
* updating vote counts
* retrieving leaderboard rankings
* duplicate vote validation
* efficient top `K` retrieval
* real-time leaderboard updates

---

# **Voting Rules**

## Candidate Registration

Candidates must be registered before receiving votes.

Each candidate has:

* unique candidate ID
* candidate name
* total vote count

---

## Voting Rules

* Each user may vote only once for a given candidate
* A user may vote for multiple different candidates
* Duplicate votes for the same candidate must be ignored

Example:

```text id="m2v8zk"
User 101 votes for Candidate A twice
```

Only the first vote is counted.

---

## Invalid Candidate Handling

If a vote is cast for a non-existent candidate:

```text id="x7m1qa"
the vote should be ignored
```

and leaderboard state must remain unchanged.

---

# **Leaderboard Rules**

Candidates are ranked by:

1. Higher vote count first
2. Lexicographically smaller candidate name in case of tie
3. Smaller candidate ID if names are identical

---

# **Task**

Design a voting system supporting the following operations:

| Operation                           | Description              |
| ----------------------------------- | ------------------------ |
| `registerCandidate(id, name)`       | Registers candidate      |
| `castVote(userId, candidateId)`     | Records vote             |
| `getVotes(candidateId)`             | Returns total votes      |
| `topK(k)`                           | Returns top K candidates |
| `hasUserVoted(userId, candidateId)` | Checks duplicate vote    |

---

# **Input Format**

First line contains integer:

```text id="u3m8qp"
C
```

representing number of candidates.

Next `C` lines contain:

```text id="f9m1zk"
candidateId candidateName
```

Next line contains integer:

```text id="r2m8vx"
Q
```

representing total operations.

Next `Q` lines contain one of the following commands:

---

## Vote Command

```text id="n7m2qa"
VOTE userId candidateId
```

---

## Vote Count Query

```text id="p4m9xp"
COUNT candidateId
```

---

## Top K Query

```text id="v1m8zk"
TOP K
```

---

# **Output Format**

For every:

* `COUNT`
* `TOP`

query print corresponding result.

---

## COUNT Output

Print total vote count.

---

## TOP Output

Print candidates in ranking order:

```text id="g8m2vx"
candidateName(votes)
```

space-separated.

---

# **Constraints**

* **1 ≤ C ≤ 10⁵**
* **1 ≤ Q ≤ 10⁵**
* Candidate names contain lowercase English letters
* **1 ≤ K ≤ C**

---

# **Sample Input 1**

```text id="x2m1qa"
3
1 alice
2 bob
3 charlie
9
VOTE 101 1
VOTE 102 2
VOTE 103 1
VOTE 101 1
COUNT 1
TOP 2
VOTE 104 2
VOTE 105 2
TOP 3
```

---

# **Sample Output 1**

```text id="m9v2zk"
2
alice(2) bob(1)
bob(3) alice(2) charlie(0)
```

---

# **Explanation**

Duplicate vote:

```text id="k4m8qp"
VOTE 101 1
```

appears twice.

Second vote is ignored.

Current votes:

| Candidate | Votes |
| --------- | ----- |
| alice     | 2     |
| bob       | 3     |
| charlie   | 0     |

Leaderboard:

```text id="u7m1xp"
bob > alice > charlie
```

---

# **Sample Input 2**

```text id="m4k8qa"
2
10 tom
20 jerry
7
VOTE 1 10
VOTE 2 20
VOTE 3 20
COUNT 20
TOP 1
VOTE 2 20
TOP 2
```

---

# **Sample Output 2**

```text id="v8m2zk"
2
jerry(2)
jerry(2) tom(1)
```

---

# **Explanation**

Duplicate vote:

```text id="x1m9vx"
VOTE 2 20
```

is ignored during second occurrence.

---

# **Sample Input 3**

```text id="z7m2qp"
3
1 adam
2 alex
3 brian
6
VOTE 10 1
VOTE 11 2
TOP 3
VOTE 12 2
TOP 2
COUNT 3
```

---

# **Sample Output 3**

```text id="u4m8zk"
adam(1) alex(1) brian(0)
alex(2) adam(1)
0
```

---

# **Explanation**

Initially:

```text id="k2m1qa"
adam
alex
```

both have:

```text id="r7m2zk"
1 vote
```

Tie resolved lexicographically:

```text id="u1m8xp"
adam < alex
```

After additional vote:

```text id="m4k8qa"
alex
```

moves ahead.

---

# **Object-Oriented Design Expectations**

Recommended classes:

| Class             | Responsibility             |
| ----------------- | -------------------------- |
| `VotingSystem`    | Core leaderboard manager   |
| `Candidate`       | Stores candidate details   |
| `VoteManager`     | Duplicate vote validation  |
| `Leaderboard`     | Ranking maintenance        |
| `UserVoteTracker` | Tracks user voting history |

---

# **Recommended Data Structures**

| Structure        | Purpose                         |
| ---------------- | ------------------------------- |
| `HashMap`        | Candidate lookup                |
| `HashSet`        | Duplicate vote prevention       |
| `TreeSet`        | Continuously sorted leaderboard |
| `Priority Queue` | Alternative top K retrieval     |

---

# **Efficient Strategy**

For every vote:

1. Validate candidate existence
2. Check duplicate voting
3. Update vote count
4. Rebalance leaderboard structure

For:

```text id="v8m2zk"
TOP K
```

retrieve highest-ranked candidates efficiently.

---

# **Important Edge Cases**

Your implementation should correctly handle:

* duplicate votes
* invalid candidate IDs
* ties in vote count
* candidates with zero votes
* large `K` queries
* repeated leaderboard requests

---

# **Expected Complexity**

## HashMap + Ordered Leaderboard Design

### castVote

* **Time Complexity:** `O(log C)`

Where:

* `C` = number of candidates

Leaderboard reordering may require balanced tree updates.

---

### COUNT

* **Time Complexity:** `O(1)`

---

### TOP K

* **Time Complexity:** `O(K)`

when the leaderboard is continuously maintained in sorted order.

---

### Space Complexity

* **O(C + V)**

Where:

* `C` = number of candidates
* `V` = unique user-candidate vote pairs stored

---

# **Scalability Discussion**

Expected interview discussion points:

* distributed vote aggregation
* Redis sorted sets
* eventual consistency
* vote deduplication across servers
* real-time streaming updates
* sharded leaderboards

---

# **Bonus Follow-Up Questions**

Interviewers may ask:

* How would you support vote removal?
* How would you prevent bot voting?
* How would you scale globally?
* How would you support time-based leaderboards?
* How would you persist leaderboard snapshots?

---

# **Execution Time Limit**

**10 seconds**