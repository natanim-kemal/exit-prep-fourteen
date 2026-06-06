# Day 1 — Review Checklist

## Mastery Checklist

Tick off each topic as you complete it:

### Fundamentals
- [ ] Data types (int, float, double, char, boolean, String)
- [ ] Variable naming rules and conventions
- [ ] Type conversion (implicit vs explicit)
- [ ] Operator precedence table
- [ ] Integer division vs float division

### Control Flow
- [ ] if, if-else, else-if chains
- [ ] switch-case (remember break!)
- [ ] for loop (init; condition; increment)
- [ ] while loop
- [ ] do-while (executes at least once)
- [ ] break vs continue

### Arrays
- [ ] Declaration: `int[] arr = new int[n];`
- [ ] Initialization: `{v1, v2, v3}`
- [ ] Indexing: `arr[i]` where `0 ≤ i < arr.length`
- [ ] Length property: `arr.length` (not a method)
- [ ] Multidimensional arrays
- [ ] Python list slicing `list[start:end]`

### Strings
- [ ] `.equals()` for content comparison
- [ ] `.substring(start, end)` — end exclusive
- [ ] `.indexOf(str)` — returns index or -1
- [ ] `.length()` vs array `.length`
- [ ] Concatenation with `+`
- [ ] Immutability

### Methods/Functions
- [ ] Method signature (name + parameters)
- [ ] Return types and void
- [ ] Method overloading
- [ ] Pass by value (Java)
- [ ] `main` method signature
- [ ] `public static void main(String[] args)`

### Exception Handling
- [ ] try-catch-finally structure
- [ ] Checked vs unchecked exceptions
- [ ] `throw` vs `throws`
- [ ] Common exceptions: Arithmetic, NullPointer, ArrayIndexOutOfBounds

### File I/O
- [ ] FileInputStream / FileOutputStream
- [ ] Scanner for input
- [ ] File reading/writing in Python
- [ ] File modes (r, w, a, r+)

### Recursion
- [ ] Base case + recursive case
- [ ] Stack frames and memory
- [ ] Factorial, Fibonacci, GCD
- [ ] Recursion vs iteration

### Testing & Debugging
- [ ] 3 error types: syntax, runtime, logical
- [ ] Unit, integration, system testing
- [ ] Alpha vs Beta testing
- [ ] Decision/condition coverage

### Problem Solving
- [ ] Algorithm design process
- [ ] Time complexity (Big-O)
- [ ] Best/average/worst case analysis
- [ ] Flowchart symbols

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **Array bounds** | "0 to length-1" — always subtract 1 |
| **String equality** | "Equals, not equals-equals" — use `.equals()` |
| **Prefix ++a** | "Prefix = first" — increment first, then use |
| **Postfix a++** | "Post = after" — use first, then increment |
| **try-catch-finally** | "try it, catch it, finally clean it" |
| **Constructor** | "Same name, no return" |
| **Method overload** | "Same name, different params" |
| **Recursion** | "Base case or recursive call" |
| **Integer division** | "Truncate toward zero" |
| **Modulo** | "Remainder after division" |

---

## Formulas to Memorize

| Formula | Description |
|---------|-------------|
| `n! = n × (n-1)!` | Factorial (recursive) |
| `Fib(n) = Fib(n-1) + Fib(n-2)` | Fibonacci |
| `GCD(a,b) = GCD(b, a%b)` | Euclidean algorithm |
| `a % b = a - (a/b)*b` | Modulo definition |
| `arr[i]` valid when `0 ≤ i < arr.length` | Array bounds |
| `substring(i,j)` = chars from i to j-1 | Substring range |

---

## Bloom's Taxonomy for Programming

The exam tests at specific cognitive levels. For programming:

| Level | What You Must Do | Example Question |
|-------|------------------|------------------|
| **Remember** | Recall syntax and definitions | "What is the syntax of a for loop?" |
| **Understand** | Explain what code does | "What does this loop print?" |
| **Apply** | Write code for a given problem | "Write a method that sums array elements" |
| **Analyze** | Find bugs or trace execution | "What is the output of this code?" |
| **Evaluate** | Compare approaches | "Which algorithm is more efficient?" |
| **Create** | Design a complete solution | "Design a program that manages student records" |

**Most exam items are at Apply and Analyze levels** — expect to trace code and identify errors.

---

## Last-Minute Cram Sheet (1 page)

```
JAVA QUICK REFERENCE
────────────────────
// Variable
int x = 5;
final double PI = 3.14;

// Array
int[] nums = {1, 2, 3};
nums.length;          // 3
nums[0];              // 1

// String
String s = "hello";
s.length();           // 5
s.equals("hello");    // true
s.substring(1, 3);    // "el"

// Loop
for (int i = 0; i < n; i++) { }
while (cond) { }
do { } while (cond);

// Method
public static int add(int a, int b) {
    return a + b;
}

// Exception
try { risky(); }
catch (Exception e) { }
finally { cleanup(); }

// Constructor
class MyClass {
    int x;
    MyClass(int x) { this.x = x; }
}

PYTHON QUICK REFERENCE
──────────────────────
# Variable
x = 5

# List
nums = [1, 2, 3]
len(nums)       # 3
nums[0]         # 1
nums[1:3]       # [2, 3]

# String
s = "hello"
len(s)          # 5
s[1:3]          # "el"

# Loop
for i in range(n):
    # body

# Function
def add(a, b):
    return a + b
```
