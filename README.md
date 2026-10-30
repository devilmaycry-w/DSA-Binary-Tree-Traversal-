# Binary Tree Traversals & Search Algorithms

A comprehensive guide exploring how to navigate tree data structures using Depth-First Search (DFS) and Breadth-First Search (BFS), illustrated using everyday real-world computer file system analogies.

---

## 🗂️ The Core Analogy: Computer File System
To understand tree traversals, imagine a project directory structured on your computer hard drive:

```text
       [My Project]             <-- Root Node
      /            \
  [Source]       [Documents]    <-- Internal Nodes (Subfolders)
   /    \            /
FileA  FileB      FileC         <-- Leaf Nodes (Files)
```

---

## 🚀 Search Paradigms: DFS vs. BFS

All tree traversals are fundamentally driven by two primary search engines: **Depth-First Search (DFS)** and **Breadth-First Search (BFS)**.

### 1. Depth-First Search (DFS)
* **The Strategy:** Dives as deep as possible down a specific subfolder branch before backtracking to look at other folders.
* **Under the Hood:** Relies on a **Stack** data structure (Last-In, First-Out). When implemented recursively, it utilizes the system's native call stack.
* **DFS Subtypes:** Depending on *when* you visit the root node relative to its subtrees, DFS splits into three distinct operational styles:

| Traversal Type | Operational Order | File System Equivalent / Use Case |
| :--- | :--- | :--- |
| **Pre-Order** | Root -> Left -> Right | **Sidebar / Tree View:** Prints parent folder names first, then immediately dives into nested files (`My Project` -> `Source` -> `FileA` -> `FileB`...). Used for cloning/copying trees. |
| **In-Order** | Left -> Root -> Right | **Alphabetical/BST Sorting:** Standard folder parent-child links don't match this directly, but search engines flatten tree directories into Binary Search Trees (BST) using In-Order to list your whole system sorted from A to Z. |
| **Post-Order** | Left -> Right -> Root | **Calculating Folder Size / Deletion:** You must calculate file sizes (or delete files) at the deepest level first before you can safely process the parent folder holding them. |

### 2. Breadth-First Search (BFS)
* **The Strategy:** Sweeps across the structure level by level. It checks every folder at the current depth before stepping down into any subfolders.
* **Under the Hood:** Strictly requires a **Queue** data structure (First-In, First-Out).
* **BFS Subtype:** **Level-Order Traversal**
  * *Execution Pattern:* Scans `Level 1: [My Project]` -> `Level 2: [Source], [Documents]` -> `Level 3: FileA, FileB, FileC`.
  * *Use Case:* Cloud storage syncing (e.g., Dropbox/Google Drive checking top-level modifications first) and finding the shortest path to an item closest to the root directory.

---

## 📊 Complexity Analysis

| Traversal Paradigm | Time Complexity | Space Complexity (Worst Case) | Space Complexity (Balanced Tree) |
| :--- | :--- | :--- | :--- |
| **DFS** (Pre / In / Post) | O(n) | O(n) *(Skewed/deep line tree)* | O(log n) |
| **BFS** (Level-Order) | O(n) | O(n) *(Extremely wide/flat tree)* | O(n) *(Leaf nodes at lowest layer)* |

* **Why is Time Complexity always O(n)?** Regardless of strategy, the computer must visit **every single node exactly once** to complete the traversal.
* **Memory Tradeoff:** DFS space scales with tree **depth** (maximum stack size). BFS space scales with tree **width** (maximum queue size tracking a single level).

---

## 🎯 Interview & Exam Cheat Sheet

Professors and technical interviewers frequently test specific edge-cases. Memorise these key takeaways:

1. **Tree Reconstruction:** You **cannot** uniquely reconstruct a binary tree given only its In-Order traversal string. You need a combination of two sequences: **In-Order + Pre-Order** or **In-Order + Post-Order**.
2. **The Magic BST Property:** Performing an **In-Order traversal on a Binary Search Tree (BST)** will *always* yield values in perfectly sorted, ascending order.
3. **Data Structure Toolkit:** 
   * **DFS** uses a **Stack**.
   * **BFS** uses a **Queue**.
4. **Optimising Space O(1):** Standard DFS takes up call stack space. To bypass this, you can execute a **Morris Traversal**, which uses temporary pointers in empty right-child slots to traverse a tree using O(1) auxiliary space.
