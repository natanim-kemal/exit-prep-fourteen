# Day 3 — DSA Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: Complexity Analysis — Trace Loops

### Problem 1 — Nested loop boundary
```java
int count = 0;
for (int i = 0; i < n; i++)
    for (int j = i; j < n; j++)
        count++;
```
**Complexity**: n + (n-1) + (n-2) + ... + 1 = n(n+1)/2 = **O(n²)**

---

### Problem 2 — Logarithmic inner loop
```java
int count = 0;
for (int i = 0; i < n; i++)
    for (int j = 1; j < n; j = j * 2)
        count++;
```
**Complexity**: Outer n times × inner log₂ n times = **O(n log n)**

---

### Problem 3 — While loop halving
```java
int n = 64;
int count = 0;
while (n > 1) {
    n = n / 2;
    count++;
}
System.out.println(count);
```
**Answer**: **6** (64 → 32 → 16 → 8 → 4 → 2 → 1, count is iterations = log₂ 64 = 6)

---

### Problem 4 — Triple nested
```java
int count = 0;
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j++)
        for (int k = 0; k < n; k++)
            count++;
```
**Complexity**: n × n × n = **O(n³)**

---

### Problem 5 — Condition-based loops
```java
int count = 0;
for (int i = 1; i * i <= n; i++)  // stops when i² > n
    count++;
System.out.println(count);
```
For n = 100: loop runs i=1..10 → **10**
**Complexity**: **O(√n)**

---

## Set 2: Stack Trace Problems

### Problem 6 — Postfix expression evaluation
Evaluate postfix: `5 3 + 8 2 - *`

**Trace using stack:**
```
Read 5:  push 5              → [5]
Read 3:  push 3              → [5, 3]
Read +:  pop 3, pop 5, push 5+3=8   → [8]
Read 8:  push 8              → [8, 8]
Read 2:  push 2              → [8, 8, 2]
Read -:  pop 2, pop 8, push 8-2=6   → [8, 6]
Read *:  pop 6, pop 8, push 8*6=48  → [48]
```
**Result: 48**

---

### Problem 7 — Balanced parentheses check
```
String: "{[()]}" — balanced?
```
**Stack trace:**
```
Read {: push → [{]
Read [: push → [{, []
Read (: push → [{, [, (]
Read ): pop matches '(' → [{, []
Read ]: pop matches '[' → [{]
Read }: pop matches '{' → []
Stack empty → ✓ BALANCED
```

---

### Problem 8 — Stack reversal
```java
Stack<Integer> s = new Stack<>();
s.push(1); s.push(2); s.push(3); s.push(4);

Queue<Integer> q = new LinkedList<>();
while (!s.isEmpty()) q.add(s.pop());

while (!q.isEmpty()) s.push(q.remove());

System.out.print(s.pop() + " " + s.pop());
```
**Trace:**
- After push: s = [1,2,3,4] (top=4)
- Transfer to q: s becomes empty, q = [4,3,2,1]
- Transfer back to s: q becomes empty, s = [1,2,3,4]
- pop() twice: 4, 3
- **Output**: `4 3`

---

## Set 3: Queue Trace Problems

### Problem 9 — Queue operations
```java
Queue<Integer> q = new LinkedList<>();
q.add(10); q.add(20); q.add(30);      // [10, 20, 30]
System.out.println(q.remove());        // removes 10 → [20, 30]
q.add(40);                             // [20, 30, 40]
System.out.println(q.peek());          // 20
q.remove();                            // [30, 40]
System.out.println(q.size());          // 2
```
**Output**: `10, 20, 2`

---

### Problem 10 — Circular Queue tracking
Circular queue of size 5. Front = 0, Rear = 0.
```
Enqueue 1: front=0, rear=1 → [1, _, _, _, _]
Enqueue 2: front=0, rear=2 → [1, 2, _, _, _]
Dequeue:  remove 1, front=1 → [_, 2, _, _, _]
Enqueue 3: front=1, rear=3 → [_, 2, 3, _, _]
Enqueue 4: front=1, rear=4 → [_, 2, 3, 4, _]
Enqueue 5: front=1, rear=0 → [5, 2, 3, 4, _]
```
When `front == (rear+1) % size` → queue is **full**

---

## Set 4: Linked List Trace

### Problem 11 — Reverse singly linked list
```java
// Input:  1 → 2 → 3 → 4 → null
// Output: 4 → 3 → 2 → 1 → null

Node prev = null;
Node curr = head;
while (curr != null) {
    Node next = curr.next;
    curr.next = prev;
    prev = curr;
    curr = next;
}
head = prev;
```
**Trace:**
```
Iter 1: prev=null, curr=1, next=2 → 1.next=null → prev=1, curr=2
Iter 2: prev=1, curr=2, next=3  → 2.next=1   → prev=2, curr=3
Iter 3: prev=2, curr=3, next=4  → 3.next=2   → prev=3, curr=4
Iter 4: prev=3, curr=4, next=null → 4.next=3 → prev=4, curr=null
Head = 4
Result: 4 → 3 → 2 → 1 → null
```

---

### Problem 12 — Detect cycle in linked list (Floyd's Cycle Detection)
```java
boolean hasCycle(Node head) {
    Node slow = head;
    Node fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) return true;
    }
    return false;
}
```
**Technique**: Tortoise & Hare. If cycle exists, slow and fast will meet.
**Time**: O(n), **Space**: O(1)

---

## Set 5: BST & Tree Traversal

### Problem 13 — BST Construction
Insert these values into an empty BST in order: `[5, 3, 7, 2, 4, 6, 8]`

```
        5
       / \
      3   7
     / \ / \
    2  4 6  8
```

**Inorder traversal**: 2, 3, 4, 5, 6, 7, 8 ← sorted!
**Preorder**: 5, 3, 2, 4, 7, 6, 8
**Postorder**: 2, 4, 3, 6, 8, 7, 5

---

### Problem 14 — BST Search
Search for value 4 in the BST above.

```
Step 1: 4 < 5 → go left
Step 2: 4 > 3 → go right
Step 3: 4 == 4 → FOUND!
```
Comparisons: **3**

---

### Problem 15 — Tree from traversal
Given inorder = [D, B, E, A, F, C, G] and preorder = [A, B, D, E, C, F, G], reconstruct the tree.

**Preorder** gives root: A
**Inorder** splits into left [D, B, E] and right [F, C, G]
- Preorder left subtree root: B → splits [D, B, E] into left[D] and right[E]
- Preorder right subtree root: C → splits [F, C, G] into left[F] and right[G]

```
        A
      /   \
     B     C
    / \   / \
   D   E F   G
```

---

## Set 6: Hashing Trace

### Problem 16 — Linear Probing
Hash table of size 7, function f(x) = x % 7
Insert: [50, 17, 24, 38, 43, 15]

```
50 % 7 = 1 → slot 1 → [_, 50, _, _, _, _, _]
17 % 7 = 3 → slot 3 → [_, 50, _, 17, _, _, _]
24 % 7 = 3 → slot 3 taken → slot 4 → [_, 50, _, 17, 24, _, _]
38 % 7 = 3 → slot 3 taken, 4 taken → slot 5 → [_, 50, _, 17, 24, 38, _]
43 % 7 = 1 → slot 1 taken → slot 2 → [_, 50, 43, 17, 24, 38, _]
15 % 7 = 1 → slot 1,2,3,4,5,6 taken → slot 0 → [15, 50, 43, 17, 24, 38, _]
```

Final table: [15, 50, 43, 17, 24, 38, _]

---

## Set 7: Sorting Trace

### Problem 17 — Bubble Sort trace
Sort: [64, 34, 25, 12, 22]

```
Pass 1: [34, 25, 12, 22, 64]  (64 bubbled to end)
Pass 2: [25, 12, 22, 34, 64]  (34 bubbled)
Pass 3: [12, 22, 25, 34, 64]  (25 bubbled)
Pass 4: [12, 22, 25, 34, 64]  (no swap, done)
```
Comparisons: 10, Swaps: 6

---

### Problem 18 — Selection Sort trace
Sort: [64, 34, 25, 12, 22]

```
Pass 1: find min=12 at index 3, swap with 64 → [12, 34, 25, 64, 22]
Pass 2: find min=22 at index 4, swap with 34 → [12, 22, 25, 64, 34]
Pass 3: find min=25 at index 2, swap with itself → [12, 22, 25, 64, 34]
Pass 4: find min=34 at index 4, swap with 64 → [12, 22, 25, 34, 64]
```
Comparisons always: n(n-1)/2 = 10, Swaps: 3

---

### Problem 19 — Insertion Sort trace
Sort: [64, 34, 25, 12]

```
[64 | 34, 25, 12]   → insert 34: [34, 64 | 25, 12]
[34, 64 | 25, 12]   → insert 25: [25, 34, 64 | 12]
[25, 34, 64 | 12]   → insert 12: [12, 25, 34, 64]
```

---

## Set 8: Algorithm Design Problems

### Problem 20 — Find max subarray sum (Kadane's Algorithm)
```java
int maxSubArraySum(int[] arr) {
    int maxSoFar = arr[0];
    int maxEndingHere = arr[0];
    for (int i = 1; i < arr.length; i++) {
        maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);
        maxSoFar = Math.max(maxSoFar, maxEndingHere);
    }
    return maxSoFar;
}
// Input: [-2, 1, -3, 4, -1, 2, 1, -5, 4]
// Output: 6  (subarray [4, -1, 2, 1])
```
**Time**: O(n), **Space**: O(1)

---

### Problem 21 — Two-pointer technique
Find if there's a pair in sorted array that sums to target:
```java
boolean hasPairSum(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) return true;
        if (sum < target) left++;
        else right--;
    }
    return false;
}
// arr = [1, 2, 4, 7, 11, 15], target = 9
// Output: true (2 + 7 = 9)
```
**Time**: O(n), **Space**: O(1)

---

### Problem 22 — Fibonacci: Recursion vs DP
```java
// Naive recursion — O(2ⁿ)
int fib(int n) {
    if (n <= 1) return n;
    return fib(n-1) + fib(n-2);
}

// Dynamic Programming (memoization) — O(n)
int fibDP(int n, int[] memo) {
    if (memo[n] != 0) return memo[n];
    if (n <= 1) return n;
    memo[n] = fibDP(n-1, memo) + fibDP(n-2, memo);
    return memo[n];
}
```
fib(40) with recursion: ~331 million calls
fib(40) with DP: 40 calls

---

### Problem 23 — Check if array is sorted
```java
boolean isSorted(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++)
        if (arr[i] > arr[i + 1]) return false;
    return true;
}
```
**Time**: O(n)

---

## Common Exam Traps — DSA

| Trap | Explanation |
|------|-------------|
| **LIFO "queue"** | A "LIFO queue" is actually a **stack** — read carefully |
| **BST worst-case** | BST search is O(n) if skewed, NOT O(log n) always |
| **Binary tree ≠ BST** | Binary tree just means 0/1/2 children; BST adds ordering property |
| **Stable sort meaning** | Stability is about equal element order, NOT about performance |
| **Linear probing clustering** | Primary clustering = long runs of occupied slots |
| **O(n²) inner loop** | `for j=i; j<n; j++` is still O(n²), just half of n² |
| **log n base** | Big-O drops the base: log₂ n = O(log n) same as log₁₀ n |
| **Binary search requires sorted** | Binary search ONLY works on sorted arrays |
| **Queue deque order** | Queue removes from FRONT (oldest), NOT back |
| **Algorithm independence** | Algorithms should be platform/language independent |
