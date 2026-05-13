# **Problem 97: Design a File System**

**Company:** Atlassian

**Category:** Low-Level Design (LLD) / Machine Coding

**Difficulty:** Hard

---

# **Problem Description**

A cloud storage platform needs to implement a hierarchical virtual file system similar to modern operating systems.

The system must support:

* nested directories
* file creation
* file storage
* path traversal
* directory size calculation
* efficient lookup operations

Every directory may contain:

* subdirectories
* files

Every file has:

* unique name within its directory
* file size in bytes

Your task is to design and implement a modular, object-oriented file system capable of efficiently managing hierarchical storage operations.

---

# **Functional Requirements**

The file system should support:

* creating directories recursively
* adding files to directories
* retrieving directory contents
* calculating total directory size
* handling invalid paths
* efficient path traversal

---

# **Definitions**

## File

A file contains:

* file name
* file size

Example:

```text id="m2v8zk"
/documents/report.pdf
size = 120
```

---

## Directory

A directory may contain:

* files
* subdirectories

Directory size is defined as:

```text id="x7m1qa"
sum of:
- all files inside current directory
- all files inside nested subdirectories
```

---

# **Task**

Design a file system supporting the following operations:

| Operation             | Description                         |
| --------------------- | ----------------------------------- |
| `mkdir(path)`         | Create directory recursively        |
| `addFile(path, size)` | Add or update file with size        |
| `ls(path)`            | List contents lexicographically     |
| `getSize(path)`       | Return total size of file/directory |
| `exists(path)`        | Check whether path exists           |

---

# **Path Rules**

* Root directory is:

```text id="u3m8qp"
/
```

* Paths use Unix-style format:

```text id="f9m1zk"
/home/user/docs
```

* File and directory names contain:

  * lowercase letters
  * digits
  * underscores
  * dots

---

# **File Handling Rules**

If a file already exists at a given path:

```text id="r2m8vx"
its size should be updated
```

instead of creating a duplicate file.

---

# **Listing Rules**

If:

```text id="n7m2qa"
ls(path)
```

is called on:

* a directory → print all child entries lexicographically
* a file → print only the file name

---

# **Input Format**

First line contains integer:

```text id="p4m9xp"
Q
```

representing total operations.

Next `Q` lines contain one of the following commands:

---

## Directory Creation

```text id="v1m8zk"
mkdir path
```

---

## File Creation

```text id="g8m2vx"
addFile path size
```

Example:

```text id="x2m1qa"
addFile /docs/a.txt 120
```

---

## List Directory

```text id="m9v2zk"
ls path
```

---

## Size Query

```text id="k4m8qp"
getSize path
```

---

## Existence Check

```text id="u7m1xp"
exists path
```

---

# **Output Format**

For every:

* `ls`
* `getSize`
* `exists`

operation print corresponding result.

---

## ls Output

Print directory contents in lexicographical order.

---

## exists Output

Print:

```text id="m4k8qa"
true
```

or

```text id="v8m2zk"
false
```

---

# **Constraints**

* **1 ≤ Q ≤ 10⁵**
* Total path length across all operations ≤ `10⁶`
* **1 ≤ file size ≤ 10⁹**

---

# **Sample Input 1**

```text id="x1m9vx"
8
mkdir /docs
addFile /docs/a.txt 100
addFile /docs/b.txt 200
mkdir /docs/images
addFile /docs/images/pic.png 300
ls /docs
getSize /docs
exists /docs/a.txt
```

---

# **Sample Output 1**

```text id="z7m2qp"
a.txt b.txt images
600
true
```

---

# **Explanation**

Directory:

```text id="u4m8zk"
/docs
```

contains:

Files:

```text id="k2m1qa"
a.txt → 100
b.txt → 200
```

Subdirectory:

```text id="r7m2zk"
images
```

Containing:

```text id="u1m8xp"
pic.png → 300
```

Total size:

```text id="m4k8qa"
100 + 200 + 300 = 600
```

---

# **Sample Input 2**

```text id="v8m2zk"
7
mkdir /a/b/c
addFile /a/b/c/file.txt 50
exists /a/b
exists /a/b/c/file.txt
getSize /a
ls /a/b
getSize /invalid
```

---

# **Sample Output 2**

```text id="x1m9vx"
true
true
50
c
INVALID PATH
```

---

# **Explanation**

Recursive directory creation automatically creates:

```text id="z7m2qp"
/a
/a/b
/a/b/c
```

File:

```text id="u4m8zk"
file.txt
```

contributes size:

```text id="k2m1qa"
50
```

through all parent directories.

---

# **Sample Input 3**

```text id="r7m2zk"
6
mkdir /music
addFile /music/song.mp3 400
ls /music
getSize /music/song.mp3
exists /music/video.mp4
ls /invalid
```

---

# **Sample Output 3**

```text id="u1m8xp"
song.mp3
400
false
INVALID PATH
```

---

# **Explanation**

File:

```text id="m4k8qa"
song.mp3
```

exists directly inside:

```text id="v8m2zk"
/music
```

Querying invalid paths should return:

```text id="x1m9vx"
INVALID PATH
```

---

# **Object-Oriented Design Expectations**

Recommended classes:

| Class        | Responsibility                |
| ------------ | ----------------------------- |
| `FileSystem` | Core filesystem manager       |
| `Directory`  | Stores subdirectories/files   |
| `File`       | Represents file metadata      |
| `Node`       | Common filesystem abstraction |
| `PathParser` | Handles path tokenization     |

---

# **Recommended Data Structures**

| Structure             | Purpose                 |
| --------------------- | ----------------------- |
| `HashMap`             | Fast child lookup       |
| `TreeMap` / Sorting   | Lexicographical listing |
| `Trie-like hierarchy` | Path traversal          |

---

# **Efficient Strategy**

For every path:

1. Split path by:

```text id="z7m2qp"
/
```

2. Traverse directory hierarchy
3. Create missing nodes when required
4. Maintain file sizes recursively

For:

```text id="u4m8zk"
getSize
```

either:

* compute recursively
  OR
* cache subtree sizes for optimization

---

# **Important Edge Cases**

Your implementation should correctly handle:

* duplicate directory creation
* file size updates
* invalid paths
* querying root directory
* deeply nested directories
* empty directories
* listing file paths directly

---

# **Expected Complexity**

## HashMap-Based Hierarchical Design

### mkdir / addFile / exists

* **Time Complexity:** `O(P)`

Where:

* `P` = number of path components

---

### ls

* **Time Complexity:** `O(K log K)`

Where:

* `K` = number of entries inside directory

---

### getSize

#### Recursive Calculation

* **Time Complexity:** `O(N)`

Where:

* `N` = total nodes inside subtree

#### Cached Subtree Sizes

* **Time Complexity:** `O(P)`

after maintaining incremental updates.

---

### Space Complexity

* **O(N)**

Where:

* `N` = total files and directories stored

---

# **Bonus Follow-Up Questions**

Interviewers may ask:

* How would you support file deletion?
* How would you implement permissions?
* How would you handle concurrent modifications?
* How would you support symbolic links?
* How would you persist filesystem metadata?

---

# **Execution Time Limit**

**10 seconds**