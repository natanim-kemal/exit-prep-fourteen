# Day 3 — DSA Review Checklist

## Mastery Checklist

### Linear Data Structures
- [ ] **Array**: O(1) access, O(n) insert/delete, fixed size
- [ ] **Linked List**: Singly, Doubly, Circular
- [ ] **Stack**: LIFO, push/pop/peek, applications (recursion, undo, parsing)
- [ ] **Queue**: FIFO, enqueue/dequeue/front, applications (print queue, BFS)
- [ ] **Priority Queue**: Heap-based, highest priority out first
- [ ] **Deque**: Double-ended, stack + queue functionality

### Non-Linear Data Structures
- [ ] **Tree**: root, parent, child, leaf, subtree, height, depth
- [ ] **Binary Tree**: full, complete, perfect, balanced, skewed
- [ ] **BST**: left < root < right, inorder = sorted
- [ ] **Traversals**: Preorder (NLR), Inorder (LNR), Postorder (LRN), Level-order
- [ ] **Heap**: Min-Heap, Max-Heap, bubble up/down
- [ ] **Graph**: directed/undirected, weighted, adjacency matrix/list
- [ ] **Graph Traversal**: BFS (queue), DFS (stack/recursion)

### Hashing
- [ ] Hash function properties
- [ ] Collision resolution: Chaining, Linear Probing, Quadratic, Double Hashing
- [ ] Load factor and resizing

### Algorithm Analysis
- [ ] Big-O notation and what it means
- [ ] Time complexities: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ)
- [ ] Best/Average/Worst case analysis
- [ ] Space complexity basics
- [ ] How to analyze nested loops

### Searching
- [ ] Linear Search: O(n), unsorted OK
- [ ] Binary Search: O(log n), sorted required
- [ ] BST Search: O(h) = O(log n) avg, O(n) worst

### Sorting
- [ ] Bubble Sort: O(n²), stable, in-place
- [ ] Selection Sort: O(n²), unstable, in-place
- [ ] Insertion Sort: O(n²), stable, in-place, O(n) best
- [ ] Merge Sort: O(n log n), stable, O(n) space
- [ ] Quick Sort: O(n log n) avg, O(n²) worst, unstable
- [ ] Heap Sort: O(n log n), unstable, in-place

### Algorithm Design Paradigms
- [ ] Divide & Conquer: Merge Sort, Quick Sort, Binary Search
- [ ] Greedy: Dijkstra, Prim, Kruskal, Huffman
- [ ] Dynamic Programming: Fibonacci (memoized), Knapsack
- [ ] Backtracking: N-Queens

### Algorithm Properties
- [ ] Input / Output / Definiteness / Finiteness / Effectiveness
- [ ] Platform and language independence
- [ ] Algorithm ≠ code (pseudocode is separate)

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **Stack LIFO** | "Last in, first out — like a stack of plates" |
| **Queue FIFO** | "First in, first out — like a checkout line" |
| **Preorder** | "Root first!" (Root → Left → Right) |
| **Inorder** | "Root in middle!" (Left → Root → Right) |
| **Postorder** | "Root last!" (Left → Right → Root) |
| **BST property** | "Left is less, Right is greater" |
| **Bubble Sort** | "Bubbles largest to end like bubbles in water" |
| **Merge Sort** | "Divide in half, sort halves, merge" |
| **Quick Sort** | "Pick pivot, partition, recurse" |
| **Binary Search** | "Halve the search space each time" |
| **O(log n)** | "Double input → one more step" |
| **O(n²)** | "Nested loops over all elements" |

---

## Bloom's Taxonomy — DSA

| Level | What You Must Do |
|-------|------------------|
| **Remember** | Define data structure names, operation names |
| **Understand** | Explain how stack differs from queue |
| **Apply** | Implement insertion into BST, traverse a tree |
| **Analyze** | Determine time complexity of an algorithm |
| **Evaluate** | Compare two sorting algorithms for a scenario |
| **Create** | Design an algorithm to solve a novel problem |

---

## 1-Page Cram Sheet

```
BIG-O CHEAT SHEET
══════════════════
O(1)      — Array access, stack push/pop
O(log n)  — Binary search, BST balanced
O(n)      — Linear search, traversal, insert at end
O(n log n)— Merge sort, Quick sort (avg), Heap sort
O(n²)     — Bubble, Selection, Insertion, nested loops
O(2ⁿ)     — Fibonacci (naive recursion)

DS OPERATIONS
═════════════
Stack:    push O(1), pop O(1), peek O(1)
Queue:    enqueue O(1), dequeue O(1)
LL:       insert head O(1), search O(n)
BST:      search/insert O(h) = O(log n) avg
Array:    access O(1), search O(n)

SORTING STABILITY
═════════════════
Stable:   Bubble, Insertion, Merge
Unstable: Selection, Quick, Heap

TRAVERSAL ORDER
═══════════════
Preorder:  Root → Left → Right
Inorder:   Left → Root → Right  ← BST = sorted!
Postorder: Left → Right → Root
Level:     BFS (top-down, left-right)

TREE TYPES
══════════
Full:     0 or 2 children per node
Complete: All levels full, last left-packed
Perfect:  All leaves same level, all internal have 2 children
Balanced: Height diff ≤ 1 (AVL)
Skewed:   All nodes have 1 child (= linked list)

HASHING
═══════
Load factor α = n/size
Collision: Chaining, Linear Probing, Quadratic, Double Hash

ALGORITHM PROPERTIES
════════════════════
Input, Output, Definiteness, Finiteness, Effectiveness
```
