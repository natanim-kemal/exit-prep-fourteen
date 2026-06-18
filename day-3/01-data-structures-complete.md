# Day 3 — Data Structures & Algorithms (119 Items)

## 1. Classification of Data Structures

```
Data Structures
├── Linear (elements in sequence)
│   ├── Static: Array
│   └── Dynamic: Linked List, Stack, Queue
└── Non-Linear (elements not sequential)
    ├── Tree: Binary Tree, BST, Heap
    └── Graph: Directed, Undirected, Weighted
```

**Exam question**: Which is a non-linear data structure?
- Queue → ❌ linear
- Stack → ❌ linear  
- **Tree** → ✓ non-linear
- Linked list → ❌ linear

---

## 2. Arrays (Review + Deep)

### Array Characteristics
- Fixed size (in most languages)
- Contiguous memory allocation
- O(1) access via index
- O(n) search (unsorted), O(log n) search (sorted binary search)

### Array Operations Complexity

| Operation | Time | Notes |
|-----------|------|-------|
| Access by index | O(1) | Direct memory address calc |
| Search (unsorted) | O(n) | Linear scan |
| Search (sorted) | O(log n) | Binary search |
| Insert at end | O(1) | If space available |
| Insert at beginning/middle | O(n) | Shift elements |
| Delete | O(n) | Shift elements |

### Jagged Array (Java)
```java
int[][] jagged = new int[3][];
jagged[0] = new int[]{1,2};
jagged[1] = new int[]{3,4,5};
jagged[2] = new int[]{6};
// Rows have different lengths
```

---

## 3. Linked Lists

### Singly Linked List
```
[data|next] → [data|next] → [data|null]
   Head                         Tail
```

### Node Structure
```java
class Node {
    int data;
    Node next;
    Node(int d) { data = d; next = null; }
}
```

### Operations Complexity

| Operation | Singly | Doubly |
|-----------|--------|--------|
| Access head | O(1) | O(1) |
| Access tail | O(n) | O(1) |
| Insert at head | O(1) | O(1) |
| Insert at tail | O(1)* | O(1) |
| Delete at head | O(1) | O(1) |
| Search | O(n) | O(n) |

*If tail pointer maintained

### Doubly Linked List
```
null ← [prev|data|next] ↔ [prev|data|next] ↔ [prev|data|next] → null
```

### Circular Linked List
- Last node points back to head (no null)
- Useful for round-robin scheduling, circular buffers

### Array vs Linked List

| Feature | Array | Linked List |
|---------|-------|-------------|
| Memory | Contiguous | Scattered |
| Size | Fixed | Dynamic |
| Access | O(1) random | O(n) sequential |
| Insert/Delete at start | O(n) | O(1) |
| Memory overhead | Minimal | Extra per node (next ptr) |

### Free List (Memory Management)
- Linked list of free memory blocks
- Modification: store addresses of `n` free blocks in the first free block (**grouping**)

---

## 4. Stacks

### LIFO Principle (Last In, First Out)
```
Push:   add to top
Pop:    remove from top
Peek:   view top without removing
```

### Stack Operations
```java
Stack<Integer> stack = new Stack<>();
stack.push(10);      // [10]
stack.push(20);      // [10, 20]
stack.peek();        // 20 (top)
stack.pop();         // returns 20 → [10]
stack.isEmpty();     // false
stack.size();        // 1
```

### Applications
1. **Function call stack** (recursion management)
2. **Undo/Redo** in editors
3. **Expression evaluation** (postfix/prefix conversion)
4. **Syntax parsing** (matching brackets)
5. **DFS** (Depth-First Search)

### Exam Trick — LIFO vs FIFO
```
A queue in which the item most recently added is always the first one out refers to:
A. LIFO queue     ← STACK (trick: called "queue" but actually a stack)
B. FIFO queue     ← normal queue
C. Real time queue
D. Priority queue
```
**Answer**: A — LIFO queue is actually a **stack**

### Stack Implementation Options
```java
// Using Array
class StackArray {
    int[] arr; int top;
    void push(int x) { arr[++top] = x; }
    int pop() { return arr[top--]; }
}

// Using Linked List
class StackLL {
    Node head;
    void push(int x) {
        Node n = new Node(x);
        n.next = head;
        head = n;
    }
    int pop() {
        if (head == null) throw;
        int val = head.data;
        head = head.next;
        return val;
    }
}
```

---

## 5. Queues

### FIFO Principle (First In, First Out)
```
Enqueue: add to rear
Dequeue: remove from front
Front:   view front element
```

### Queue Operations
```java
Queue<Integer> q = new LinkedList<>();
q.add(10);         // [10]
q.add(20);         // [10, 20]
q.peek();          // 10 (front)
q.remove();        // returns 10 → [20]
```

### Queue Applications
1. **Print queue** (OS scheduling)
2. **BFS** (Breadth-First Search)
3. **CPU scheduling** (FCFS)
4. **Buffers** (IO, keyboard)
5. **Simulation** of real-world queues

### Circular Queue
- Front and rear pointers wrap around
- Efficient use of array space
- Condition: `front == (rear + 1) % size` means full

### Priority Queue
- Elements have priority values
- Higher priority elements dequeued first
- Implemented with **Heap** data structure
- Applications: Dijkstra's algorithm, Huffman coding

### Deque (Double-Ended Queue)
- Insert/delete from both ends
- `ArrayDeque` in Java
- Can function as both stack and queue

### Indirect Applications of Queues
```
Which is an INDIRECT application of queues?
A. Auxiliary data structure for algorithms     ← ✓ indirect
B. Simulation of real-world queues              ← direct
C. OS print queue scheduling                     ← direct
D. Multiprogramming                             ← indirect
```

---

## 6. Trees

### Tree Terminology
- **Node**: element in tree
- **Root**: topmost node (no parent)
- **Parent/Child**: direct connection relationship
- **Leaf**: node with no children
- **Subtree**: portion of tree rooted at a node
- **Height**: longest path from root to leaf
- **Depth**: distance from root
- **Level**: all nodes at same depth

### Binary Tree Definition
```
Which is NOT true about binary tree?
A. A tree is binary if each node has zero child     ← TRUE (can have 0)
B. A tree is binary if each node has 0, 1, or 2 children   ← TRUE
C. Empty tree is also a valid binary tree                    ← TRUE
D. A tree is binary iff each node has zero child             ← FALSE (can have 1 or 2)
```

### Binary Tree Types

| Type | Description |
|------|-------------|
| **Full/Strict** | Every node has 0 or 2 children |
| **Complete** | All levels filled except possibly last, which is left-packed |
| **Perfect** | All internal nodes have 2 children, all leaves same level |
| **Balanced** | Height difference between subtrees ≤ 1 |
| **Skewed** | All nodes have 1 child (resembles linked list) |

### Binary Tree Traversals

```java
class TreeNode {
    int data;
    TreeNode left, right;
    TreeNode(int d) { data = d; }
}
```

| Traversal | Order | Result (tree below) |
|-----------|-------|---------------------|
| **Preorder** (Root-Left-Right) | NLR | F, B, A, D, C, E, G, I, H |
| **Inorder** (Left-Root-Right) | LNR | A, B, C, D, E, F, G, H, I |
| **Postorder** (Left-Right-Root) | LRN | A, C, E, D, B, H, I, G, F |
| **Level-order** (BFS) | Top-down, left-right | F, B, G, A, D, I, C, E, H |

```
         F
       /   \
      B     G
     / \     \
    A   D     I
       / \   /
      C   E H
```

**Preorder** = F B A D C E G I H  
**Inorder** = A B C D E F G H I  (BST gives sorted order!)  
**Postorder** = A C E D B H I G F  

### Binary Search Tree (BST)
- Left subtree < root < Right subtree
- Inorder traversal gives **sorted order**
- Operations: O(h) where h = height (O(log n) if balanced, O(n) if skewed)

```java
class BST {
    TreeNode root;
    
    TreeNode insert(TreeNode r, int x) {
        if (r == null) return new TreeNode(x);
        if (x < r.data) r.left = insert(r.left, x);
        else if (x > r.data) r.right = insert(r.right, x);
        return r;
    }
    
    boolean search(TreeNode r, int x) {
        if (r == null) return false;
        if (x == r.data) return true;
        return x < r.data ? search(r.left, x) : search(r.right, x);
    }
}
```

### BST Deletion Cases
1. **Leaf**: simply remove
2. **One child**: replace node with child
3. **Two children**: find inorder successor (smallest in right subtree), copy value, delete successor

### Tree Traversal — Identify from Sequence
Given inorder + preorder/postorder, you can reconstruct the tree (exam common).

---

## 7. Heaps

### Min-Heap vs Max-Heap

| Feature | Min-Heap | Max-Heap |
|---------|----------|----------|
| Root | Smallest element | Largest element |
| Property | Parent ≤ children | Parent ≥ children |
| Use | Priority Queue, Dijkstra | Heap Sort, scheduling |

### Heap Operations
- **Insert**: add at end, bubble up (O(log n))
- **Delete min/max**: replace root with last element, bubble down (O(log n))
- **Build heap**: O(n) (Floyd's method)
- **Heap sort**: O(n log n)

---

## 8. Graphs

### Graph Representations

| Representation | Space | Edge Check |
|----------------|-------|------------|
| Adjacency Matrix | O(V²) | O(1) |
| Adjacency List | O(V+E) | O(degree(v)) |

```java
// Adjacency List
class Graph {
    int V;
    List<Integer>[] adj;
    
    Graph(int v) {
        V = v;
        adj = new ArrayList[v];
        for (int i = 0; i < v; i++) adj[i] = new ArrayList<>();
    }
    
    void addEdge(int u, int v) {
        adj[u].add(v);
        adj[v].add(u);  // undirected
    }
}
```

### Graph Traversals

| Algorithm | Data Structure | Application |
|-----------|---------------|-------------|
| **BFS** (Breadth-First) | Queue | Shortest path in unweighted, level-order |
| **DFS** (Depth-First) | Stack/Recursion | Topological sort, cycle detection, path finding |

```java
// BFS
void bfs(int start) {
    boolean[] visited = new boolean[V];
    Queue<Integer> q = new LinkedList<>();
    visited[start] = true;
    q.add(start);
    while (!q.isEmpty()) {
        int u = q.poll();
        for (int v : adj[u]) {
            if (!visited[v]) { visited[v] = true; q.add(v); }
        }
    }
}

// DFS (recursive)
void dfs(int u, boolean[] visited) {
    visited[u] = true;
    for (int v : adj[u]) {
        if (!visited[v]) dfs(v, visited);
    }
}
```

### Weighted Graphs & Dijkstra's Algorithm
```
Dijkstra's Algorithm — shortest path from source to all nodes
- Uses: Priority Queue (Min-Heap)
- Time: O((V+E) log V)
- Does NOT work with negative edge weights
- Greedy algorithm (always picks closest unvisited node)
```

**Dijkstra vs Uniform Cost Search:**
- Dijkstra: discovers nodes as they come, uses a **priority queue**
- UCS: first collects all nodes in a **priority queue**, then processes
- Both are optimal, both find shortest path

### Spanning Tree
- Subset of edges connecting all vertices with minimum total edges (V-1)
- **Minimum Spanning Tree** (MST): Kruskal's or Prim's algorithm

---

## 9. Hashing

### Hash Table Concepts
- Key → hash function → index
- Good hash function: uniform distribution, fast computation

### Collision Resolution

| Method | Description | Pros | Cons |
|--------|-------------|------|------|
| **Chaining** | Each bucket stores linked list | Simple, unlimited items | Extra memory for pointers |
| **Linear Probing** | If occupied, try next slot | Cache-friendly | Clustering problem |
| **Quadratic Probing** | Try i² away | Less clustering | May not find slot |
| **Double Hashing** | Second hash for step | Good distribution | Slower |

### Linear Probing Example
```
Hash: f(x) = x
Table size: 7

Insert: 12 → 12%7 = 5 (slot 5)
Insert: 9  → 9%7 = 2 (slot 2)
Insert: 18 → 18%7 = 4 (slot 4)
Insert: 3  → 3%7 = 3 (slot 3, but 3 < 4 doesn't matter — check empty)
             → check slot 3: empty → insert at 3
Insert: 14 → 14%7 = 0 (slot 0)
Insert: 21 → 21%7 = 0 (slot 0 occupied) → 1, 2 occupied → 3 occupied
             → 4 occupied → 5 occupied → 6 empty → insert at 6
Insert: 4  → 4%7 = 4 (occupied) → 5 occupied → 6 occupied → 0 occupied
             → 1 empty → insert at 1

Final table: [14, 4, 9, 3, 18, 12, 21]
```

### Load Factor
- `α = n / tableSize` (number of items / table size)
- Higher α → more collisions
- Resize when α exceeds threshold (typically 0.75)

---

## 10. Algorithm Analysis (Complexity)

### Big-O Notation

| Notation | Name | Description |
|----------|------|-------------|
| O(1) | Constant | Fixed time, independent of input |
| O(log n) | Logarithmic | Halves each iteration (binary search) |
| O(n) | Linear | Scans all elements once |
| O(n log n) | Linearithmic | Divide & conquer (merge sort) |
| O(n²) | Quadratic | Nested loops |
| O(2ⁿ) | Exponential | Recursive without memoization |

### Complexity Cases
- **Best case**: minimum time (e.g., sorted array for bubble sort → O(n))
- **Average case**: expected time (e.g., quicksort → O(n log n))
- **Worst case**: maximum time (e.g., reversed sorted for bubble sort → O(n²))

### Complexity Analysis Steps
1. Find basic operation (innermost loop/recursive call)
2. Count how many times it executes as function of n
3. Express using Big-O (drop constants, keep highest order)

```java
// Example 1: O(n)
for (int i = 0; i < n; i++) { print(n); }

// Example 2: O(n²)
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j++)
        print(n);

// Example 3: O(n²) — watch the bounds
for (int i = 0; i < n; i++)
    for (int j = i; j < n; j++)      // n + (n-1) + ... + 1 = n(n+1)/2 = O(n²)
        print(n);

// Example 4: O(n log n)
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j = j * 2)  // log₂ n
        print(n);

// Example 5: O(√n)
for (int i = 1; i * i < n; i++)
    print(n);
```

### Time Complexity — Hard Exam Problem
```java
function someFunction(int n) {
    for (int i = 0; i < n; i++)           // n
        for (int j = 0; j < i * i; j++)   // i²
            if (j % i == 0) {
                for (int k = 0; k < j; k++)  // j
                    print("*");
            }
}
```
**Analysis:**
- Outer: i = 0 to n-1
- Middle: j = 0 to i²-1
- Inner (conditional): k = 0 to j-1, only when `j % i == 0`
- j % i == 0 when j is a multiple of i: j = 0, i, 2i, 3i, ..., i²-i → approximately i values
- For each such j, inner loop runs j times
- Sum ≈ Σᵢ (i × average j value) = Σᵢ (i × i²/2) = ½ Σᵢ i³ = O(n⁴)

---

## 11. Searching Algorithms

### Linear Search
```java
int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++)
        if (arr[i] == target) return i;
    return -1;
}
```
- Time: O(n)
- Space: O(1)
- Works on unsorted data

### Binary Search
```java
int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;  // avoid overflow
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```
- Time: O(log n)
- Space: O(1) iterative, O(log n) recursive
- **Requires sorted array**

---

## 12. Sorting Algorithms

| Algorithm | Best | Average | Worst | Space | Stable | In-place |
|-----------|------|---------|-------|-------|--------|----------|
| **Bubble** | O(n) | O(n²) | O(n²) | O(1) | ✓ | ✓ |
| **Selection** | O(n²) | O(n²) | O(n²) | O(1) | ✗ | ✓ |
| **Insertion** | O(n) | O(n²) | O(n²) | O(1) | ✓ | ✓ |
| **Merge** | O(n log n) | O(n log n) | O(n log n) | O(n) | ✓ | ✗ |
| **Quick** | O(n log n) | O(n log n) | O(n²) | O(log n) | ✗ | ✓ |
| **Heap** | O(n log n) | O(n log n) | O(n log n) | O(1) | ✗ | ✓ |

### Bubble Sort
```java
void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n-1; i++) {
        boolean swapped = false;
        for (int j = 0; j < n-i-1; j++) {
            if (arr[j] > arr[j+1]) {
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
                swapped = true;
            }
        }
        if (!swapped) break;  // optimization: already sorted
    }
}
```

### Selection Sort
```java
void selectionSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n-1; i++) {
        int minIdx = i;
        for (int j = i+1; j < n; j++)
            if (arr[j] < arr[minIdx]) minIdx = j;
        int temp = arr[i];
        arr[i] = arr[minIdx];
        arr[minIdx] = temp;
    }
}
```

### Insertion Sort
```java
void insertionSort(int[] arr) {
    int n = arr.length;
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

### Merge Sort (Divide & Conquer)
```java
void mergeSort(int[] arr, int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}
// Time: O(n log n) always
// Space: O(n) — needs temp array
```

### Quick Sort (Divide & Conquer)
```java
void quickSort(int[] arr, int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
// Average: O(n log n)
// Worst: O(n²) — poor pivot choice
// Can improve with randomized pivot
```

### Stability
- **Stable**: maintains relative order of equal elements (Bubble, Insertion, Merge)
- **Unstable**: may not maintain order (Selection, Quick, Heap)

---

## 13. Algorithm Design Paradigms

| Paradigm | Description | Examples |
|----------|-------------|----------|
| **Divide & Conquer** | Split problem, solve parts, combine | Merge Sort, Quick Sort, Binary Search |
| **Greedy** | Make locally optimal choice at each step | Dijkstra, Prim, Kruskal, Huffman |
| **Dynamic Programming** | Solve subproblems once, store results | Fibonacci (memoized), KnapSack, LCS |
| **Backtracking** | Try all candidates, abandon dead ends | N-Queens, Sudoku |
| **Brute Force** | Try all possibilities | Linear Search, Bubble Sort |

### Greedy vs Dynamic Programming

| Feature | Greedy | DP |
|---------|--------|----|
| Decision | One-time, irreversible | Considers all options |
| Optimality | May not be optimal | Guaranteed optimal |
| Overlap | No subproblem overlap | Subproblems overlap |
| Example | Dijkstra, Huffman | 0/1 Knapsack, Floyd-Warshall |

---

## 14. Algorithm Development Concepts

### Algorithm Definition
- Step-by-step **logical** description of solving a problem
- Should be developed **independently** of programming language and platform
- Equivalent to **pseudocode**, not actual code
- Considers: input, output, definiteness, finiteness, effectiveness

```
Which is NOT true regarding algorithm development?
A. Should be developed by considering platform it runs on    ← FALSE
B. Stepwise logical description of how to solve problem      ← TRUE
C. Developed considering details of programming language     ← FALSE
D. Equivalent to programming language code                   ← FALSE
```
**Answer**: A, C, D are all false statements about algorithm development. B is the correct characteristic.

### Algorithm Properties
1. **Input** — zero or more inputs
2. **Output** — at least one output
3. **Definiteness** — clear, unambiguous steps
4. **Finiteness** — terminates after finite steps
5. **Effectiveness** — each step is basic enough

---

## Exam-Style Practice Questions

### Q1: Queue type
A queue in which the item most recently added is always the first one out refers to?

**Answer**: **LIFO queue** (trick — it's actually describing a **stack**, but named as a "queue")

---

### Q2: Non-linear data structure
Which is a non-linear data structure?
- A. Queue
- B. Stack
- C. **Tree** ← ✓
- D. Linked list

---

### Q3: Binary tree definition
Which is NOT true about binary tree?
- A. A tree is called binary tree iff each node has zero child
- B. A tree is called binary tree if each node has 0, 1, or 2 children
- C. Empty tree is also a valid binary tree
- D. Can visualize as root + two disjoint binary trees

**Answer**: A (each node does NOT have to have zero children; 0, 1, or 2 are all allowed)

---

### Q4: Time complexity analysis
```java
function someFunction(int n) {
    for (int i = 0; i < n * 10; i++) {
        console.log(n);
    }
}
```
What is the time complexity?
- A. O(n²)
- B. O(log n)
- C. O(n log n)
- D. **O(n)** ← ✓

**Analysis**: Loop runs n*10 times → O(n) (constants dropped)

---

### Q5: Time complexity — hard
```java
function(int n) {
    for (int i = 0; i < n; i++)
        for (int j = i; j < i * i; j++)
            if (j % i == 0)
                for (int k = 0; k < j; k++)
                    print("*");
}
```
- A. O(n²)
- B. O(n log n)
- C. **O(n⁵)** ← answer from exam
- D. O(n⁷)

**Reason**: n × n² × (avg j) ≈ n × n² × n²/2 = O(n⁵)

---

### Q6: Analysis mechanism
Which analysis mechanism defines the input for which the algorithm takes the **least** time?

**Answer**: **Best case** analysis (fastest time to complete)

---

### Q7: Binary tree traversal
Given a BST with inorder traversal: [2, 5, 7, 10, 15, 20], which is true?

**Answer**: Inorder traversal of BST always produces **sorted ascending** order

---

### Q8: Queue applications
Which is an **indirect** application of queues?
- A. Auxiliary data structure for algorithms ← ✓
- B. Simulation of real-world queues
- C. OS print queue scheduling
- D. Multiprogramming

---

### Q9: Hash table — linear probing insertion order
Given hash table with identity function f(x)=x, size 7. Elements inserted. Which insertion order could produce the final table [14, 4, 9, 3, 18, 12, 21]?
```java
A. 12, 9, 18, 3, 14, 21, 4
B. 9, 14, 4, 18, 12, 3, 21   ← one possible answer
C. 12, 14, 3, 9, 4, 18, 21
D. 12, 3, 14, 18, 4, 9, 21
```

---

### Q10: Quadtree
In a quadtree, each non-leaf node has exactly how many children?

**Answer**: **4**

---

### Q11: Free list modification
A modification of the free-list approach is to store the addresses of n free blocks in the first free block. This is called:

**Answer**: **Grouping**

---

### Q12: Dijkstra vs UCS
Which specifies divergence between Dijkstra's Algorithm and Uniform Cost Search?
- A. UCS finds optimal solution while DA does not
- B. **DA discovers nodes as they come while UCS first collects them in a Queue** ← ✓
- C. DA is optimal but not UCS
- D. Both are the same

---

### Q13: Stack — valid operations
Which is NOT a valid stack operation?
- A. Push
- B. Pop
- C. **Enqueue** ← ✓ (this is queue)
- D. Peek

---

### Q14: Complexity class
Which complexity class is considered the most efficient for large inputs?
- A. O(2ⁿ)
- B. O(n²)
- C. O(n!)
- D. **O(log n)** ← ✓

---

### Q15: BST search
In a BST with n nodes, the worst-case search time is:
- A. O(1)
- B. O(log n)
- C. **O(n)** ← ✓ (if tree is skewed)
- D. O(n²)

---

### Q16: Sorting stability
Which sorting algorithm is **stable**?
- A. Selection sort
- B. **Merge sort** ← ✓
- C. Quick sort
- D. Heap sort

---

### Q17: Graph BFS uses which data structure?
- A. Stack
- B. **Queue** ← ✓
- C. Priority queue
- D. Array

---

### Q18: Linked list — deleting head
In a singly linked list with a head pointer, deleting the first node takes:
- A. **O(1)** ← ✓
- B. O(n)
- C. O(log n)
- D. O(n²)

---

## Quick Reference Card

```
LINEAR DS: Array, Stack, Queue, Linked List
NON-LINEAR: Tree, Graph

STACK (LIFO): push, pop, peek
QUEUE (FIFO): enqueue, dequeue, front

TREE TRAVERSAL:
  Preorder:  Root → Left → Right
  Inorder:   Left → Root → Right  (BST → sorted)
  Postorder: Left → Right → Root

BST: left < root < right

TIME COMPLEXITIES:
  O(1)     — array access
  O(log n) — binary search
  O(n)     — linear search, traversal
  O(n log n) — merge sort, quick sort (avg)
  O(n²)   — bubble, selection, nested loops
  O(2ⁿ)   — naive Fibonacci

SORTING:
  Stable:  Bubble, Insertion, Merge
  Unstable: Selection, Quick, Heap

HASHING COLLISION:
  Chaining, Linear Probing, Quadratic Probing, Double Hashing

ALGORITHM PROPERTIES:
  Input, Output, Definiteness, Finiteness, Effectiveness
```


## Practice Questions (from Question Bank)

### Q135. Consider a system where time complexity of searching in a balanced BST?

- A) O1
- B) On log n
- C) On
- D) Olog n
  **Answer: B**

### Q136. Which sort is O(n log n) in ALL cases?

- A) Insertion Sort
- B) Merge Sort
- C) Bubble Sort
- D) Quick Sort
  **Answer: B**

### Q137. Which stack operation removes top element?

- A) enqueue
- B) pop
- C) push
- D) dequeue
  **Answer: B**

### Q138. In a resource-constrained environment, bST inorder traversal gives:?

- A) Reverse order
- B) Random order
- C) Sorted ascending order
- D) Level order
  **Answer: C**

### Q139. Circular queue solves which linear queue problem?

- A) Thread safety
- B) Underflow
- C) Overflow when front moved
- D) Priority ordering
  **Answer: C**

### Q140. BFS uses which data structure?

- A) Queue
- B) Deque
- C) Stack
- D) Priority queue
  **Answer: A**

### Q141. Consider a system where adjacency List space complexity for sparse graph?

- A) OE²
- B) OV
- C) OV²
- D) OV+E
  **Answer: D**

### Q142. Which sorting algorithm is NOT stable?

- A) Merge Sort
- B) Bubble Sort
- C) Insertion Sort
- D) Quick Sort
  **Answer: D**

### Q143. In Max-Heap, which property must hold?

- A) Parent < children
- B) Left > right
- C) Parent >= both children
- D) All leaves same level
  **Answer: A**

### Q144. When designing for high performance, worst case of Quick Sort and its cause?

- A) O — sorted input
- B) O — worst pivot choice
- C) O — random pivot
- D) O — balanced partitions
  **Answer: A**

### Q145. Which finds shortest path in weighted graph, no negative weights?

- A) DFS
- B) Dijkstra
- C) BFS
- D) Kruskal
  **Answer: B**

### Q146. Postorder traversal visits nodes as:?

- A) Root, Left, Right
- B) Left, Root, Right
- C) Right, Left, Root
- D) Left, Right, Root
  **Answer: A**

### Q147. When designing for high performance, doubly linked list differs from singly by having:?

- A) O search
- B) Less memory
- C) Both next and prev pointers
- D) Circular traversal
  **Answer: C**

### Q148. Binary search requires input to be:?

- A) In linked list
- B) No duplicates
- C) Power of 2 size
- D) Sorted
  **Answer: D**

### Q149. Time to insert at HEAD of singly linked list?

- A) On
- B) O1
- C) Olog n
- D) On²
  **Answer: B**

### Q150. In a resource-constrained environment, lIFO describes which data structure?

- A) Graph
- B) Queue
- C) Stack
- D) Tree
  **Answer: C**

### Q151. FIFO describes which data structure?

- A) Priority Queue
- B) Deque
- C) Stack
- D) Queue
  **Answer: A**

### Q152. Which description of Big-O notation used for is accurate?

- A) Measuring actual execution time
- B) Ranking algorithms by difficulty
- C) Counting lines of code
- D) Worst-case upper bound on time/space
  **Answer: D**

### Q153. In a resource-constrained environment, identify the correct statement about O(1) complexity.

- A) Linear time
- B) Logarithmic time
- C) Constant time regardless
- D) Quadratic time
  **Answer: C**

### Q154. Binary search time complexity?

- A) On
- B) O1
- C) On²
- D) Olog n
  **Answer: D**

### Q155. Bubble sort worst case?

- A) Olog n
- B) On
- C) On²
- D) On log n
  **Answer: C**

### Q156. In a resource-constrained environment, which sort is best for nearly-sorted data?

- A) Heap Sort
- B) Insertion Sort
- C) Quick Sort
- D) Merge Sort
  **Answer: B**

### Q157. DFS uses which data structure (or concept)?

- A) Stack/Recursion
- B) Priority Queue
- C) Queue
- D) Circular Buffer
  **Answer: A**

### Q158. Preorder traversal visits nodes as:?

- A) Left, Right, Root
- B) Root, Left, Right
- C) Left, Root, Right
- D) Right, Root, Left
  **Answer: A**

### Q159. In a resource-constrained environment, identify the correct statement about priority queue.

- A) Double-ended queue
- B) Stack in reverse
- C) Queue with fixed size
- D) Queue where elements
  **Answer: D**

### Q160. Heap Sort builds what structure first?

- A) Max-Heap
- B) Min-Heap
- C) BST
- D) AVL tree
  **Answer: A**

### Q161. Selection sort finds minimum and:?

- A) Merges two halves
- B) Inserts into sorted portion
- C) Swaps to front of unsorted part
- D) Partitions around pivot
  **Answer: C**

### Q162. In a resource-constrained environment, merge Sort space complexity?

- A) On²
- B) Olog n
- C) O1
- D) On
  **Answer: D**

### Q163. Which of the following best describes n AVL tree?

- A) B-tree variant
- B) Binary tree with alphabetical
- C) Self-balancing BST with
- D) Heap with AVL property
  **Answer: D**

### Q164. Level-order traversal uses:?

- A) Stack
- B) Queue
- C) Priority Queue
- D) Recursion
  **Answer: B**

### Q165. Consider a system where which graph representation is better for dense graphs?

- A) Adjacency List
- B) Edge List
- C) Adjacency Matrix
- D) Incidence Matrix
  **Answer: C**

### Q166. Insertion sort best-case time complexity?

- A) On²
- B) On
- C) On log n
- D) Olog n
  **Answer: B**

### Q167. Which algorithm finds Minimum Spanning Tree?

- A) Kruskal
- B) BFS
- C) DFS
- D) Dijkstra
  **Answer: A**

### Q168. Consider a system where what does 'stable' mean for a sorting algorithm?

- A) Works on linked lists
- B) Runs in O
- C) Never crashes
- D) Preserves relative order
  **Answer: D**

### Q169. Which description of height of a balanced BST with n nodes is accurate?

- A) O1
- B) On
- C) On²
- D) Olog n
  **Answer: D**

### Q170. Circular linked list last node points to:?

- A) Random node
- B) Null
- C) Previous node
- D) Head node
  **Answer: D**

### Q171. When designing for high performance, which of the following best describes NOT in-place sorting?

- A) Merge Sort
- B) Insertion Sort
- C) Quick Sort
- D) Bubble Sort
  **Answer: A**

### Q172. Stack application: balanced parentheses checking uses:?

- A) Count all brackets
- B) Push opening brackets, pop
- C) Use queue for FIFO checking
- D) Sort brackets first
  **Answer: B**

### Q173. Which description of deque is accurate?

- A) Priority queue
- B) Stack + Queue hybrid only
- C) Double-ended queue with
- D) Circular queue
  **Answer: C**

### Q174. In a resource-constrained environment, time complexity of Heap Sort?

- A) On
- B) Olog n
- C) On log n
- D) On²
  **Answer: C**

### Q175. Which of the following best describes branching factor in BFS analysis?

- A) Number of edges
- B) Depth of tree
- C) Height of tree
- D) Number of children per node
  **Answer: D**

### Q176. What makes DFS not complete for infinite graphs?

- A) It uses too much memory
- B) It can get stuck in infinite
- C) It only works on trees
- D) It requires sorted input
  **Answer: B**

### Q177. In a resource-constrained environment, a graph with no cycles is called:?

- A) Acyclic graph
- B) Weighted graph
- C) Directed graph
- D) Dense graph
  **Answer: A**

### Q178. Prim's algorithm builds MST by:?

- A) Reversing Dijkstra
- B) Growing a tree from a
- C) Using DFS
- D) Sorting all edges
  **Answer: B**

### Q179. Which traversal is used to copy/serialize a tree?

- A) Level-order
- B) Inorder
- C) Postorder
- D) Preorder
  **Answer: D**

### Q180. In a resource-constrained environment, which traversal is used to delete a tree safely?

- A) Inorder
- B) Preorder
- C) Postorder
- D) Level-order
  **Answer: C**

### Q181. Time complexity of linear search?

- A) On log n
- B) O1
- C) On
- D) Olog n
  **Answer: C**

### Q182. Infix to postfix conversion uses which structure?

- A) Array
- B) Tree
- C) Stack
- D) Queue
  **Answer: C**

### Q183. Which of the following best describes peek/top operation on a stack?

- A) Removes top
- B) Views top without removing
- C) Adds to top
- D) Clears stack
  **Answer: B**

### Q184. In a BST, left child is always:?

- A) Less than parent
- B) Random
- C) Greater than parent
- D) Equal to parent
  **Answer: A**

### Q185. Which description of Dijkstra's limitation is accurate?

- A) Only works on unweighted graphs
- B) Cannot handle negative edge weights
- C) Requires sorted adjacency list
- D) Only works on trees
  **Answer: B**

### Q186. In a resource-constrained environment, selection sort is NOT stable because:?

- A) It uses recursion
- B) Swapping can change
- C) It runs in O
- D) It doesn't compare
  **Answer: B**

### Q187. Space complexity of DFS with m being max depth?

- A) On²
- B) Ob^d
- C) O1
- D) Om
  **Answer: D**

### Q188. Identify the correct statement about complete binary tree.

- A) Tree with n! nodes
- B) All levels filled except
- C) Every node has exactly 2
- D) Balanced BST always
  **Answer: B**

### Q189. When designing for high performance, heap insert operation time complexity?

- A) Olog n
- B) O1
- C) On
- D) On log n
  **Answer: A**

### Q190. Identify the correct statement about hash table's average search time.

- A) O1
- B) Olog n
- C) On log n
- D) On
  **Answer: A**

### Q191. Kruskal's algorithm sorts edges by:?

- A) Vertex degree
- B) Destination vertex
- C) Edge weight
- D) Source vertex
  **Answer: C**

### Q192. In a resource-constrained environment, a tree with n nodes has how many edges?

- A) n
- B) n-1
- C) 2n
- D) n+1
  **Answer: B**

### Q193. Which description of main advantage of a doubly linked list over singly is accurate?

- A) Simpler insertion
- B) Less memory
- C) Faster search
- D) Can traverse in both directions
  **Answer: D**

### Q194. Bubble sort best case (already sorted)?

- A) O1
- B) On log n
- C) On²
- D) On
  **Answer: D**

### Q195. Identify the correct statement about graph's adjacency matrix diagonal represent.

- A) Edge weights
- B) Connected components
- C) Vertex degrees
- D) Self-loops
  **Answer: D**

### Q196. Which search is used in BFS for shortest path in unweighted graph?

- A) BFS itself
- B) Dijkstra
- C) DFS
- D) A*
  **Answer: A**

### Q197. Stack overflow in recursion is caused by:?

- A) Large arrays
- B) Infinite while loops
- C) Too many variables
- D) Too many recursive calls
  **Answer: D**

### Q198. When designing for high performance, identify the correct statement about spanning tree.

- A) Full tree with all possible
- B) AVL tree variant
- C) Subgraph connecting all
- D) Complete binary tree
  **Answer: C**

### Q199. Time complexity of inserting into a sorted linked list?

- A) O1
- B) Olog n
- C) On
- D) On²
  **Answer: C**

### Q200. Identify the correct statement about purpose of a sentinel node in linked lists.

- A) Points to last node
- B) Stores list size
- C) Marks deleted nodes
- D) Dummy node simplifying
  **Answer: D**

### Q201. In a resource-constrained environment, which data structure supports undo/redo operations?

- A) Stack
- B) Graph
- C) Heap
- D) Queue
  **Answer: A**

### Q202. What does BFS guarantee in unweighted graphs?

- A) Topological order
- B) Minimum spanning tree
- C) All paths found
- D) Shortest path by number of edges
  **Answer: D**

### Q203. Min-Heap property: parent is:?

- A) Equal to left child
- B) Greater than
- C) Random relative to children
- D) Less than
  **Answer: D**

### Q204. Consider a system where binary search mid calculation: mid = ?

- A) / 2
- B) low + 1
- C) high - low
- D) / 2
  **Answer: A**

### Q205. Identify the correct statement about worst case for a BST that becomes unbalanced (degenerates).

- A) O search
- B) O search
- C) O search
- D) O search, like a linked list
  **Answer: D**

### Q206. Application of Queue: CPU scheduling uses which variant?

- A) Queue
- B) Deque
- C) Priority Queue
- D) Stack
  **Answer: C**

### Q207. Consider a system where what operation rebuilds heap property after insertion?

- A) Rotate
- B) Sift-down
- C) Rebalance
- D) Sift-up
  **Answer: D**

### Q208. Counting sort has time complexity of:?

- A) On²
- B) On log n
- C) On
- D) O where k is value range
  **Answer: D**

### Q209. Which description of topological sort used for is accurate?

- A) Ordering vertices in DAG
- B) Sorting numbers
- C) Building MST
- D) Finding shortest path
  **Answer: A**

### Q210. When designing for high performance, time complexity to find maximum element in unsorted array?

- A) On
- B) O1
- C) Olog n
- D) On log n
  **Answer: A**

### Q211. Which description of graph cycle is accurate?

- A) A path that visits every vertex once
- B) An edge connecting non-adjacent vertices
- C) A disconnected subgraph
- D) A path that starts and ends at same vertex
  **Answer: D**

### Q212. Adjacency Matrix space complexity?

- A) OV²
- B) OE
- C) OV+E
- D) OV
  **Answer: A**

### Q213. Which sort divides array into two halves, sorts each, then merges?

- A) Heap Sort
- B) Merge Sort
- C) Bubble Sort
- D) Quick Sort
  **Answer: B**

### Q214. Which of the following best describes tree's root node?

- A) Deepest node
- B) Node with most children
- C) Node with no parent
- D) Node with no children
  **Answer: C**

### Q215. Which of the following best describes leaf nodes in a tree?

- A) Root's direct children
- B) Nodes with no parent
- C) Nodes with no children
- D) Nodes at depth 1
  **Answer: C**

### Q216. When designing for high performance, quick sort average case time complexity?

- A) On log n
- B) On²
- C) Olog n
- D) On
  **Answer: A**

### Q217. Which algorithm is called 'divide and conquer'?

- A) Selection Sort
- B) Insertion Sort
- C) Merge Sort
- D) Bubble Sort
  **Answer: C**

### Q218. Dijkstra's algorithm uses which data structure for efficiency?

- A) Stack
- B) Deque
- C) Priority Queue
- D) Queue
  **Answer: C**

### Q219. Identify the correct statement about depth of the root node in a tree.

- A) 1
- B) 0
- C) -1
- D) Depends on tree size
  **Answer: B**

### Q220. A full binary tree has every node with:?

- A) 0 or 2 children
- B) Exactly 1
- C) At least 1 child
- D) Exactly 2 children
  **Answer: A**

### Q221. BFS time complexity for graph with V vertices and E edges?

- A) OE²
- B) OV²
- C) OV+E
- D) OV log V
  **Answer: C**

### Q222. In a resource-constrained environment, which operation is O(n) in singly linked list?

- A) Get size
- B) Insert at head
- C) Delete at head
- D) Search by value
  **Answer: D**

### Q223. Which of the following best describes weighted graph?

- A) Tree with weights on nodes
- B) Graph where edges have numerical values
- C) Graph with heavy nodes
- D) Dense graph with many edges
  **Answer: B**

### Q224. Insertion sort builds sorted array by:?

- A) Finding minimum and placing at front
- B) Merging sorted halves
- C) Inserting each element into correct
- D) Pivoting around middle element
  **Answer: C**

### Q225. Which traversal visits all nodes at depth d before depth d+1?

- A) BFS
- B) DFS
- C) Inorder
- D) Postorder
  **Answer: A**

### Q226. Which sort has O(n) best case and is adaptive?

- A) Merge Sort
- B) Quick Sort
- C) Selection Sort
- D) Insertion Sort
  **Answer: D**

### Q227. Time complexity of building a heap from n elements?

- A) On²
- B) On log n
- C) On
- D) Olog n
  **Answer: C**

### Q228. When designing for high performance, identify the correct statement about n undirected graph.

- A) Graph where edges have no direction
- B) Graph with all vertices connected
- C) Graph with no edges
- D) Graph with only self-loops
  **Answer: A**

### Q229. In Quick Sort, what is a 'pivot'?

- A) Element chosen to partition
- B) The last element always
- C) The median always
- D) The first element always
  **Answer: A**

### Q230. Identify the correct statement about main drawback of Bubble Sort.

- A) Needs extra memory
- B) Cannot sort integers
- C) O in average/worst case —
- D) Not stable
  **Answer: C**

### Q231. Consider a system where stack push/pop operations are both:?

- A) On
- B) Olog n
- C) On²
- D) O1
  **Answer: D**

### Q232. Which traversal gives reverse sorted order in a BST?

- A) Reverse Inorder
- B) Postorder
- C) Preorder
- D) Level order
  **Answer: A**

### Q233. DFS can detect what in a graph?

- A) Shortest path
- B) Connected components and cycles
- C) All-pairs shortest paths
- D) Minimum spanning tree
  **Answer: B**

### Q234. In a resource-constrained environment, a priority queue can be implemented efficiently using:?

- A) Heap
- B) Stack
- C) Array
- D) Linked list
  **Answer: A**

### Q235. What does enqueue do in a queue?

- A) Checks if empty
- B) Peeks at front
- C) Adds to rear
- D) Removes from front
  **Answer: C**

### Q236. What does dequeue do in a queue?

- A) Peeks at rear
- B) Adds to rear
- C) Clears queue
- D) Removes from front
  **Answer: D**

### Q237. Consider a system where binary search goes to which half if target < arr[mid]?

- A) Random half
- B) Left half
- C) Stays at mid
- D) Right half
  **Answer: B**

### Q238. Selection Sort is NOT stable because:?

- A) Requires sorted input
- B) Non-adjacent swaps can
- C) It merges subarrays
- D) Uses recursion
  **Answer: B**

### Q239. Which description of degree of a vertex in a graph is accurate?

- A) Number of edges incident to it
- B) Its weight
- C) Its depth in tree
- D) Distance from root
  **Answer: A**

### Q240. When designing for high performance, in a tree, the path from root to a node determines its:?

- A) Degree
- B) Weight
- C) Depth/Level
- D) Balance factor
  **Answer: C**

### Q241. Heap Sort is NOT stable because:?

- A) Requires sorted input
- B) Runs in O
- C) Swapping in heapify
- D) Uses extra memory
  **Answer: C**

### Q242. Which sort always performs exactly n(n-1)/2 comparisons regardless of input?

- A) Insertion Sort
- B) Selection Sort
- C) Bubble Sort
- D) Quick Sort
  **Answer: B**

### Q243. Which description of time to delete a node from middle of doubly linked list given pointer to it is accurate?

- A) On²
- B) O1
- C) On
- D) Olog n
  **Answer: B**

### Q244. A connected graph has what property?

- A) No cycles
- B) Path exists between every
- C) Equal edge weights
- D) All vertices have same
  **Answer: B**

### Q245. What distinguishes a tree from a general graph?

- A) Trees have weighted edges
- B) Trees are connected and acyclic
- C) Trees require sorted data
- D) Trees have at most 2 children per node
  **Answer: B**

### Q246. When designing for high performance, counting number of nodes in a binary tree requires:?

- A) O double traversal
- B) O for balanced trees only
- C) O traversal
- D) O traversal visiting all nodes
  **Answer: D**

### Q247. Which graph algorithm finds strongly connected components?

- A) Dijkstra
- B) Kosaraju/Tarjan
- C) BFS
- D) Kruskal
  **Answer: B**

### Q248. Time to access element at index i in array?

- A) Olog n
- B) O1
- C) On
- D) Oi
  **Answer: B**

### Q249. What problem does a priority queue solve that a regular queue doesn't?

- A) Processing elements by
- B) Circular buffering
- C) FIFO ordering
- D) Thread safety
  **Answer: A**

### Q250. Which of the following best describes n in-order successor of a node in BST?

- A) Parent node
- B) Smallest node in right subtree
- C) Next node added to tree
- D) Largest node in left subtree
  **Answer: B**

### Q251. Big-O order: which grows fastest?

- A) O2^n
- B) On log n
- C) On²
- D) On!
  **Answer: D**

### Q252. In a resource-constrained environment, which data structure is used in print spooling?

- A) Stack
- B) Deque
- C) Queue
- D) Priority Queue
  **Answer: C**

### Q253. What does 'amortized O(1)' mean for dynamic array append?

- A) Append is always O
- B) Every append is O
- C) Average cost per append
- D) Size doubles every
  **Answer: C**

