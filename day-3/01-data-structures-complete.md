# Day 3 — Data Structures & Algorithms (8 Items)

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
