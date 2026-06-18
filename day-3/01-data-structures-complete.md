# Data Structures & Algorithms — Study Notes

## 1. Algorithm Analysis

**Big-O notation**: describes the worst-case upper bound on time/space complexity as input size grows.
- **O(1)**: constant time — doesn't depend on input size (e.g., array access by index, stack push/pop)
- **O(log n)**: logarithmic — binary search, balanced BST operations
- **O(n)**: linear — linear search, traversing an array
- **O(n log n)**: linearithmic — merge sort, heap sort, quick sort (average)
- **O(n²)**: quadratic — bubble sort, selection sort, nested loops
- **O(2ⁿ)**: exponential — naive Fibonacci recursion
- **O(n!)**: factorial — grows the fastest

**Amortized O(1)**: average cost per operation over a sequence (e.g., dynamic array append — occasional O(n) resize but O(1) average).

## 2. Arrays

**Advantages**: O(1) random access by index, cache-friendly contiguous memory.
**Time complexities**: access O(1), search O(n), insertion/deletion O(n) (requires shifting).
**Space**: O(n).

## 3. Linked Lists

**Singly linked list**: each node has data + pointer to next node.
**Doubly linked list**: each node has data + pointers to both next and previous nodes.
**Circular linked list**: last node points back to head.

**Operations**: insert at head O(1), delete at head O(1), search O(n), access by index O(n).
**Advantage over array**: dynamic size without reallocation.
**Disadvantage**: no O(1) random access.

## 4. Stacks

**LIFO** (Last In, First Out). Operations: `push` (add to top), `pop` (remove from top), `peek`/`top` (view top without removing). All O(1).

**Applications**: balanced parentheses checking (push opening, pop on closing), undo/redo, infix to postfix conversion, function call stack.

## 5. Queues

**FIFO** (First In, First Out). Operations: `enqueue` (add to rear), `dequeue` (remove from front). All O(1).

**Circular queue**: solves the problem of overflow when front has moved (wraps around using modulo arithmetic).
**Priority queue**: elements processed by priority (not FIFO). Implemented efficiently using a **heap**.
**Deque**: double-ended queue — insert/remove at both ends.

**Applications**: print spooling, BFS, CPU scheduling (priority queue variant).

## 6. Trees

**Binary Tree**: each node has at most 2 children.
- **Root**: node with no parent
- **Leaf**: node with no children
- **Depth of root**: 0
- **Height of balanced BST with n nodes**: O(log n)
- **Edge count**: a tree with n nodes has n-1 edges

**Binary Search Tree (BST)**: left child < parent < right child.
- **Inorder traversal**: gives sorted ascending order
- **Reverse inorder**: gives reverse sorted order
- **Unbalanced BST degenerates**: into a linked list (O(n) search)

**Complete Binary Tree**: all levels filled except possibly the last, which is filled left to right.
**Full Binary Tree**: every node has 0 or 2 children.

**Traversals**:
- **Preorder** (Root, Left, Right): used to copy/serialize a tree
- **Inorder** (Left, Root, Right): gives sorted order in BST
- **Postorder** (Left, Right, Root): used to delete a tree safely (children before parent)
- **Level-order**: uses a queue (BFS)

**Self-balancing BST (AVL)**: maintains O(log n) height by rebalancing after insertions/deletions.

## 7. Heaps

**Max-Heap**: parent >= both children. Root is the maximum element.
**Min-Heap**: parent <= both children. Root is the minimum element.

**Operations**: insert O(log n), extract min/max O(log n), build heap from n elements O(n). **Heapify**: sift-up (after insertion), sift-down (after deletion). Heap Sort: O(n log n), not stable (swapping in heapify breaks stability).

## 8. Graphs

**Representations**: 
- **Adjacency Matrix**: O(V²) space — better for dense graphs
- **Adjacency List**: O(V+E) space — better for sparse graphs
- **Diagonal of adjacency matrix**: represents self-loops

**Properties**: 
- **Undirected**: edges have no direction
- **Connected**: path exists between every pair of vertices
- **Acyclic**: no cycles (a tree is connected and acyclic)
- **Weighted**: edges have numerical values
- **Degree of a vertex**: number of edges incident to it

**Graph Algorithms**:
- **BFS**: uses queue; finds shortest path in unweighted graphs; O(V+E) time
- **DFS**: uses stack/recursion; detects connected components and cycles; O(V+E) time; space O(m) where m = max depth
- **Dijkstra**: finds shortest path in weighted graphs (no negative weights); uses priority queue
- **Kruskal/Prim**: find Minimum Spanning Tree (MST). Kruskal sorts edges by weight; Prim grows from a starting vertex
- **Topological sort**: orders vertices in a DAG
- **Kosaraju/Tarjan**: find Strongly Connected Components
- **Branching factor in BFS**: number of children per node

## 9. Sorting Algorithms

| Algorithm | Best | Average | Worst | Space | Stable |
|-----------|------|---------|-------|-------|--------|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) | Yes |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) | Yes |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) | No |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) | Yes |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) | No |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) | No |

**Key points**:
- **Divide and Conquer**: Merge Sort, Quick Sort
- **Stable** sorts preserve relative order of equal elements (Bubble, Insertion, Merge)
- **Adaptive** (O(n) best case): Insertion Sort, Bubble Sort — good for nearly-sorted data
- Selection Sort always does n(n-1)/2 comparisons
- Not in-place: Merge Sort (needs O(n) extra space)

## 10. Hashing & Hash Tables

Average search time: **O(1)**, worst case O(n) (collisions).
**Collision resolution**: chaining, open addressing (linear probing, quadratic probing, double hashing).

## 11. Binary Search

Requires **sorted** input. Steps: compare target with middle element, go to left half if target < mid, right half if target > mid. Mid calculation: `mid = low + (high - low) / 2`. Time: O(log n).
