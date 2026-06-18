# Day 1 — Fundamentals of Programming (14 Items)

## 1. Variables, Data Types & Naming

### Valid Identifiers
- Must start with letter, underscore `_`, or dollar sign `$`
- Cannot start with digit
- Case-sensitive
- Reserved keywords cannot be used

**Valid:** `variable_123`, `$money`, `_name`, `fullName`
**Invalid:** `7variable`, `try` (keyword), `full-name` (hyphen)

### Primitive Data Types (Java)
| Type | Size | Range |
|------|------|-------|
| byte | 1 B | -128 to 127 |
| short | 2 B | -32,768 to 32,767 |
| int | 4 B | -2^31 to 2^31-1 |
| long | 8 B | -2^63 to 2^63-1 |
| float | 4 B | ±3.4e-38 to ±3.4e+38 |
| double | 8 B | ±1.7e-308 to ±1.7e+308 |
| char | 2 B | 0 to 65,535 |
| boolean | 1 bit | true/false |

### Python Variables
- Dynamic typing — no type declaration needed
- `x = 5` automatically assigns int type
- `type(x)` returns `<class 'int'>`
- Multiple assignment: `a, b, c = 1, 2, 3`

### Type Casting Deep Dive

**Widening (Implicit)** — safe, no data loss
```java
int i = 100;
long l = i;        // int → long (OK)
float f = l;       // long → float (OK, possible precision loss but allowed)
double d = f;      // float → double (OK)
```

**Narrowing (Explicit)** — possible data loss, must cast
```java
double d = 100.5;
int i = (int) d;               // 100 (truncated)
byte b = (byte) 300;            // 44 (300 mod 256 = 44, overflow!)
```

**Integer Promotion**: In expressions, `byte`, `short`, `char` are promoted to `int`:
```java
byte a = 10, b = 20;
byte c = a + b;                 // ERROR: a+b is int, needs cast
byte c = (byte)(a + b);         // OK
```

**Type conversion in Python:**
```python
int(3.14)           # 3 (truncation)
float("10.5")       # 10.5
str(42)             # "42"
int("1010", 2)      # 10 (binary to decimal)
int(float("10.0"))  # 10 (string → float → int)
```

### Wrapper Classes & Autoboxing

| Primitive | Wrapper |
|-----------|---------|
| `int` | `Integer` |
| `double` | `Double` |
| `boolean` | `Boolean` |
| `char` | `Character` |

```java
Integer x = 5;               // autoboxing: int → Integer
int y = x;                   // unboxing: Integer → int
Integer z = Integer.valueOf(10);  // explicit boxing
int w = Integer.parseInt("42");   // string to int
```

---

## 2. Operators & Precedence

### Arithmetic Operators
| Operator | Meaning |
|----------|---------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division (float) |
| `//` | Integer division (Python) |
| `%` | Modulus |
| `**` | Exponentiation (Python) |

### Increment/Decrement (Java)
```java
int a = 4;
++a * 5    // prefix: a becomes 5, then 5*5 = 25
a++ * 5    // postfix: uses 4*5 = 20, then a becomes 5
```

### Operator Precedence (highest to lowest)
1. Parentheses `()`
2. Unary `++`, `--`, `+`, `-`, `!`, `not`
3. Multiplicative `*`, `/`, `%`, `//`
4. Additive `+`, `-`
5. Relational `<`, `>`, `<=`, `>=`
6. Equality `==`, `!=`
7. Logical AND `&&`, `and`
8. Logical OR `||`, `or`
9. Assignment `=`, `+=`, etc.

**Python example with precedence:**
```python
x = 5 * 2 + 3 // 4 + 10 ** 2
# 10 + 0 + 100 = 110
```

**Boolean logic:**
```python
x = not 2 + 3 == 5 or 5 + 2 <= 7 and 7 + 8 == 15
# not (5 == 5) or (7 <= 7) and (15 == 15)
# not True or True and True
# False or True = True
```

### Short-Circuit Evaluation
- `&&` / `and`: if left operand is `false`, right is **not evaluated**
- `||` / `or`: if left operand is `true`, right is **not evaluated**

```java
int x = 5, y = 0;
if (y != 0 && x / y > 1) { }     // safe: y!=0 is false, never evaluates x/y
if (y == 0 || x / y > 1) { }      // UNSAFE: y==0 is true, but x/y still evaluated!
```

### Bitwise Operators

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `&` | AND | `5 & 3` | `1` (101 & 011 = 001) |
| `\|` | OR | `5 \| 3` | `7` (101 \| 011 = 111) |
| `^` | XOR | `5 ^ 3` | `6` (101 ^ 011 = 110) |
| `~` | NOT | `~5` | `-6` (inverts all bits) |
| `<<` | Left shift | `5 << 1` | `10` (×2) |
| `>>` | Right shift | `5 >> 1` | `2` (÷2) |
| `>>>` | Unsigned right shift | `-1 >>> 1` | `2147483647` |

**Exam note**: `>>` preserves sign bit, `>>>` shifts zero into sign bit.

---

## 3. Control Structures

### if-else (Java)
```java
if (condition) {
    // code
} else if (otherCondition) {
    // code
} else {
    // code
}
```

### switch (Java)
```java
switch (value) {
    case 1:
        // code
        break;    // without break, falls through
    case 2:
        // code
        break;
    default:
        // code
}
```
**Without break** → all subsequent cases execute (fall-through).

### switch with String (Java 7+)
```java
String day = "Monday";
switch (day) {
    case "Monday":   System.out.println("Start of week"); break;
    case "Friday":   System.out.println("End of week"); break;
    default:         System.out.println("Mid-week");
}
```

### Enhanced switch arrow syntax (Java 14+)
```java
switch (day) {
    case "Monday", "Tuesday" -> System.out.println("Early week");
    case "Friday" -> System.out.println("Weekend near");
    default -> System.out.println("Other day");
}
```

### for Loop
```java
for (initialization; condition; increment/decrement) {
    // body
}
// Example:
for (int i = 0; i < args.length; i++) {
    System.out.println(args[i]);
}
```

### Enhanced for Loop (for-each)
```java
int[] numbers = {10, 20, 30, 40};
for (int num : numbers) {
    System.out.println(num);
}

List<String> names = Arrays.asList("A", "B", "C");
for (String name : names) {
    System.out.println(name);
}
```
**Cannot** modify array indices in for-each (no index variable).

### Variable Scope Rules
```java
public class ScopeDemo {
    int instanceVar = 10;           // instance scope (entire class)
    static int classVar = 20;       // class scope (shared)
    
    public void method(int param) { // parameter scope (method)
        int localVar = 30;           // block scope (method)
        if (true) {
            int blockVar = 40;       // block scope (if-block only)
            // can access: param, localVar, blockVar, instanceVar, classVar
        }
        // blockVar is OUT OF SCOPE here
    }
}
```
- **Local variables** must be initialized before use
- **Shadowing**: local variable with same name as field hides the field
- Use `this.field` to access shadowed instance field

### Python for loop
```python
for i in range(5):        # 0,1,2,3,4
for i in range(2, 6):     # 2,3,4,5
for i in range(0, 10, 2): # 0,2,4,6,8

# Enumerate (get index + value)
for index, value in enumerate(['a','b','c']):
    print(index, value)    # 0 a, 1 b, 2 c

# Zip (parallel iteration)
for a, b in zip([1,2,3], ['x','y','z']):
    print(a, b)            # 1 x, 2 y, 3 z

# List comprehension
squares = [x**2 for x in range(5)]        # [0,1,4,9,16]
evens = [x for x in range(10) if x % 2 == 0]  # [0,2,4,6,8]
```

### while Loop
```java
while (condition) {
    // body
}
```

### do-while Loop
```java
do {
    // body — executes at least once
} while (condition);
```

### break vs continue
- **break** — exits loop immediately
- **continue** — skips rest of current iteration, goes to next

---

## 4. Arrays

### Java Arrays
```java
// Declaration + allocation
int[] arr = new int[5];
int arr[] = new int[5];

// Initialization
int[] someArray = { 2, 13, 9, 11, 10 };

// Access
someArray[2]     // index 2 = 9
someArray.length // = 5

// Iteration
for (int i = 0; i <= arr.length - 2; ++i) {
    System.out.println(arr[i] + ",");
}
```

### Multidimensional Arrays
```java
int[][] twoD = new int[4][5];  // 4 rows, 5 cols
int[][] matrix = { {1,2}, {3,4}, {5,6} };
```

### Python Lists (like arrays)
```python
programming = ['Software', 'Electrical', 'Civil']
max(programming)  # 'Software' (alphabetically last)

# List slicing
siTE = ['A', 'B', 'C', 'D']
siTE[1:4] = ['E', 'F', 'G']
# Result: ['A', 'E', 'F', 'G']

# List operations
len(list)    # length
list[i]      # element at index i
list.append(x)  # add to end
```

### Common Array Exceptions
- `ArrayIndexOutOfBoundsException` — accessing index beyond bounds
- `NullPointerException` — array variable not initialized

---

## 5. Strings

### Java String Methods
```java
String s = "exercise";
s.substring(3, 5);   // from index 3 to 5 (exclusive) → "rc"
s.length();           // length
s.charAt(i);          // character at index
s.equals(other);      // compare content
s.indexOf("rc");      // returns index
```

### Python String Operations
```python
s = "Welcome"
s * 2                 # "WelcomeWelcome"
s[1:4]                # "elc"
len(s)                # length
"Hello" + " World"    # concatenation
```

### String Comparison (Java)
```java
// Use equals() NOT == for content comparison
String a = "hello";
String b = "hello";
a == b          // compares references (may be true due to interning)
a.equals(b)     // compares content (always correct)
```

---

## 6. Functions/Methods

### Java Method Syntax
```java
modifier returnType methodName(parameters) {
    // method body
}
```

### Method Overloading
Multiple methods with same name but different parameters:
```java
void test() { }
void test(int a) { }
void test(int a, int b) { }
double test(double a) { }
```
This is a form of **polymorphism** (compile-time / static polymorphism).

### Python Functions
```python
def function_name(param1, param2):
    """Docstring explaining what this does"""
    # body
    return value

# Default parameters
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

# Keyword arguments
greet(greeting="Hi", name="Abebe")

# *args (variable positional) and **kwargs (variable keyword)
def sum_all(*args):
    return sum(args)    # sum_all(1,2,3) → 6

def print_info(**kwargs):
    for k, v in kwargs.items():
        print(f"{k}: {v}")   # print_info(name="A", age=20)
```

### Method Parameters
- **Pass by value**: Java passes primitives by value (copy)
- **Pass by reference**: Objects pass the reference (copy of reference)

### Varargs (Variable Arguments) in Java
```java
public static int sum(int... numbers) {
    int total = 0;
    for (int n : numbers) total += n;
    return total;
}

sum(1, 2, 3);        // 6
sum(10, 20);         // 30
sum();               // 0 (zero args is valid)
```
Rules: only one varargs per method, must be the last parameter.

### Random Number Generation
```java
// Java
Random rand = new Random();
int x = rand.nextInt(100);       // 0 to 99
int y = rand.nextInt(50) + 10;   // 10 to 59
double d = rand.nextDouble();    // 0.0 to 1.0

// Python
import random
x = random.randint(1, 100)       // 1 to 100 inclusive
y = random.choice(['A','B','C']) // random element
```

### StringBuilder (Mutable String)
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");        // "Hello World"
sb.insert(5, " Java");      // "Hello Java World"
sb.reverse();               // "dlroW avaJ olleH"
sb.toString();              // convert to String
```
Why? Strings are immutable; `StringBuilder` is efficient for many concatenations.

---

## 7. Exception Handling

### Exception Hierarchy
```
Throwable
├── Error (irrecoverable — JVM errors, out of memory, etc.)
└── Exception
    ├── RuntimeException (unchecked — ArithmeticException,
    │   NullPointerException, ArrayIndexOutOfBoundsException)
    └── Checked exceptions (IOException, SQLException, etc.)
```

### try-catch-finally
```java
try {
    // code that may throw exception
} catch (ExceptionType e) {
    // handle exception
} finally {
    // always executes (even if exception occurs or not)
}
```

### throw vs throws
| throw | throws |
|-------|--------|
| Used to **explicitly throw** an exception | Used to **declare** exceptions a method may throw |
| `throw new ArithmeticException("msg");` | `void method() throws IOException {}` |
| Inside method body | In method signature |

### Types of Errors
1. **Syntax Error** — violates language grammar (compiler catches)
2. **Runtime Error** — occurs during execution (e.g., division by zero)
3. **Logical Error** — compiles and runs but gives wrong output

---

## 8. Input/Output & File Handling

### Java File I/O
```java
// Reading from file
FileInputStream fis = new FileInputStream("file.txt");

// Writing to file
FileOutputStream fos = new FileOutputStream("output.txt");

// Scanner for user input
Scanner sc = new Scanner(System.in);
int n = sc.nextInt();
```

### File I/O in Python
```python
# Reading
file = open("file.txt", "r")
content = file.read()
file.close()

# Writing
with open("file.txt", "w") as f:
    f.write("Hello World")
```

### File Modes
| Mode | Meaning |
|------|---------|
| `r` | Read |
| `w` | Write (overwrites) |
| `a` | Append |
| `r+` | Read and write |

---

## 9. Program Structure & Memory

### Java Program Structure
```java
package packageName;

import java.util.*;

public class ClassName {
    // class variables (static)
    // instance variables
    // constructors
    // methods
    
    public static void main(String[] args) {
        // entry point
    }
}
```

### Compilation Process (C++)
```
Source Code → Preprocessor → Compiler → Assembler → Linker → Executable
```

### Memory Areas
- **Stack**: local variables, method calls (LIFO)
- **Heap**: dynamically allocated objects (new keyword)
- **Code segment**: compiled code
- **Data segment**: static/global variables

### Constructor
- Same name as class
- No return type (not even void)
- Called automatically when object is created
- Can be overloaded

---

## 10. Problem-Solving Techniques

### Steps in Problem Solving
1. **Understand the problem** — read carefully, identify inputs/outputs
2. **Design algorithm** — stepwise logical description (platform independent)
3. **Write code** — implement in chosen language
4. **Test & debug** — verify with sample inputs
5. **Optimize** — improve efficiency if needed

### Algorithm Analysis
- **Time Complexity**: How runtime grows with input size
  - O(1) — constant
  - O(log n) — logarithmic
  - O(n) — linear
  - O(n²) — quadratic
  - O(2ⁿ) — exponential
- **Space Complexity**: How memory usage grows with input size

### Algorithm Analysis Cases
- **Best case**: minimum time (fastest)
- **Worst case**: maximum time (slowest)
- **Average case**: expected time

### Flowchart Symbols
- Oval: Start/End
- Parallelogram: Input/Output
- Rectangle: Process
- Diamond: Decision
- Arrow: Flow direction

---

## 11. Recursion

Recursion is a technique where a function calls itself.

### Structure
```java
returnType recursiveFunction(parameters) {
    if (baseCase) {
        return baseValue;
    } else {
        // recursive call with modified parameters
        return recursiveFunction(modifiedParams);
    }
}
```

### Examples
```java
// Factorial
int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}

// Fibonacci
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

### Recursion Deep — Call Stack Analysis

```java
public static int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```
**Call stack for factorial(4):**
```
factorial(4) → 4 * factorial(3)
  factorial(3) → 3 * factorial(2)
    factorial(2) → 2 * factorial(1)
      factorial(1) → 1      ← base case reached
    ← returns 2*1 = 2
  ← returns 3*2 = 6
← returns 4*6 = 24
```

**Tail recursion vs head recursion:**
- **Head recursion**: recursive call happens before processing (call then compute)
- **Tail recursion**: recursive call is the last operation (can be optimized by compiler)

### Recursion vs Iteration
| Recursion | Iteration |
|-----------|-----------|
| Function calls itself | Loop constructs |
| More memory (call stack) | Less memory |
| Elegant for tree/graph problems | Better for simple loops |
| Risk of stack overflow | No such risk |

### Assertions (Java)
```java
int x = -5;
assert x >= 0 : "x must be non-negative";   // throws AssertionError if false
// Enable with: java -ea ClassName
```

---

## 12. Testing & Debugging

### Testing Principles
- **Unit testing**: test individual components
- **Integration testing**: test combined components
- **System testing**: test entire system
- **Alpha testing**: internal testing by developers
- **Beta testing**: testing by real users

### Decision/Condition Coverage
- Test every branch of decision points (if-else, switch)
- 100% decision coverage means every branch executed at least once

### Debugging Techniques
1. Print statements / logging
2. Use debugger (breakpoints, step over/into)
3. Rubber duck debugging
4. Code review

### Common Bugs
- Off-by-one errors in loops
- Null pointer dereference
- Array index out of bounds
- Infinite loops
- Integer overflow
- Race conditions (multithreading)

---

---

## Question Bank Study Notes

### Variables & Data Types
Variables store data with a name, type, and value. Primitive types: `int`, `float`, `char`, `bool`. `string` is NOT primitive. Declare constants with `const`. **Scope**: local (inside function), global (entire program), block (`{}`). Shadowing: local hides global.

### Operators
**Arithmetic** (`+`, `-`, `*`, `/`, `%`) — precedence: `*`/`/`/`%` before `+`/`-`. **Relational** (`==`, `!=`, `<`, `>`, `<=`, `>=`). **Logical** (`&&`, `||`, `!`) — short-circuit: second operand skipped if first determines result. **Bitwise** (`&`, `|`, `^`, `~`, `<<`, `>>`). **Ternary** (`?:` — 3 operands). `sizeof()` returns bytes. `++i` increments before use, `i++` after. `sizeof(int)` = 4 bytes on 32-bit.

### Control Flow
**if-else**, **switch-case** (without `break` → fall-through). **Loops**: `for` (known count), `while` (checks before), `do-while` (at least once), `foreach`. Infinite loop: condition never false. Jump: `break` (exit loop), `continue` (skip iteration), `return` (exit function). `loop` is NOT a jump statement.

### Functions
**Declaration** (signature) vs **Definition** (body). **Prototype**: declares before use. **Pass-by-value**: copies argument. **Pass-by-reference**: modifies original. **Overloading**: same name, different parameters. Return: `void` = nothing, `int` = integer. Multiple returns via struct. Overloading differs in parameter number/type, not return type alone.

### Recursion
Function calls itself. Needs **base case** (stops) + **recursive case**. Call stack limits depth → stack overflow if too deep. Factorial(3) = 6.

### Arrays & Vectors
1D: `int arr[5] = {1,2,3,4,5}`. First index = 0. Out-of-bounds = undefined behavior. 2D = array of arrays. **Vector**: dynamic array — `push_back()` (add), `pop_back()` (remove last), `size()` (element count). String concatenation = joining strings.

### Pointers & Memory
**Null pointer** = address 0. `new` = dynamic allocation (heap). `delete` = free. Memory leak = allocated but not freed. `->` accesses struct member via pointer. Local vars on **stack**, call stack tracks active functions.

### File I/O
`ifstream` (read), `ofstream` (write), `fstream` (both). Append mode adds at end. Always check if file opened successfully. Text = human-readable chars.

### Program Design
**IPO**: Input-Process-Output. **Modular programming**: promotes code reuse. **Pseudocode**: informal algorithm description. **Debugging**: finding/fixing errors. **Debugger**: steps through code.

### Error Types
**Syntax**: grammar violation (caught by compiler). **Runtime**: occurs during execution (divide by zero). **Logical/Semantic**: runs but wrong output.

### Other
`7 % 3 = 1`. `//` = single comment, `/* */` = multi-line. `enum` = named integer constants. `typedef` = type alias. `struct` = groups data. Header files (`.h`) = shared declarations. `static` = persists between calls. `extern` = defined in another file. Swap without temp: `a=a+b; b=a-b; a=a-b`.


---

## Question Bank Study Notes

### Variables & Data Types
Variables store data with a name, type, and value. Primitive types: `int`, `float`, `char`, `bool`. `string` is NOT primitive. Declare constants with `const`. **Scope**: local (inside function), global (entire program), block (`{}`). Shadowing: local hides global.

### Operators
**Arithmetic** (`+`, `-`, `*`, `/`, `%`) — precedence: `*`/`/`/`%` before `+`/`-`. **Relational** (`==`, `!=`, `<`, `>`, `<=`, `>=`). **Logical** (`&&`, `||`, `!`) — short-circuit: second operand skipped if first determines result. **Bitwise** (`&`, `|`, `^`, `~`, `<<`, `>>`). **Ternary** (`?:` — 3 operands). `sizeof()` returns bytes. `++i` increments before use, `i++` after. `sizeof(int)` = 4 bytes on 32-bit.

### Control Flow
**if-else**, **switch-case** (without `break` → fall-through). **Loops**: `for` (known count), `while` (checks before), `do-while` (at least once), `foreach`. Infinite loop: condition never false. Jump: `break` (exit loop), `continue` (skip iteration), `return` (exit function). `loop` is NOT a jump statement.

### Functions
**Declaration** (signature) vs **Definition** (body). **Prototype**: declares before use. **Pass-by-value**: copies argument. **Pass-by-reference**: modifies original. **Overloading**: same name, different parameters. Return: `void` = nothing, `int` = integer. Multiple returns via struct. Overloading differs in parameter number/type, not return type alone.

### Recursion
Function calls itself. Needs **base case** (stops) + **recursive case**. Call stack limits depth → stack overflow if too deep. Factorial(3) = 6.

### Arrays & Vectors
1D: `int arr[5] = {1,2,3,4,5}`. First index = 0. Out-of-bounds = undefined behavior. 2D = array of arrays. **Vector**: dynamic array — `push_back()` (add), `pop_back()` (remove last), `size()` (element count). String concatenation = joining strings.

### Pointers & Memory
**Null pointer** = address 0. `new` = dynamic allocation (heap). `delete` = free. Memory leak = allocated but not freed. `->` accesses struct member via pointer. Local vars on **stack**, call stack tracks active functions.

### File I/O
`ifstream` (read), `ofstream` (write), `fstream` (both). Append mode adds at end. Always check if file opened successfully. Text = human-readable chars.

### Program Design
**IPO**: Input-Process-Output. **Modular programming**: promotes code reuse. **Pseudocode**: informal algorithm description. **Debugging**: finding/fixing errors. **Debugger**: steps through code.

### Error Types
**Syntax**: grammar violation (caught by compiler). **Runtime**: occurs during execution (divide by zero). **Logical/Semantic**: runs but wrong output.

### Other
`7 % 3 = 1`. `//` = single comment, `/* */` = multi-line. `enum` = named integer constants. `typedef` = type alias. `struct` = groups data. Header files (`.h`) = shared declarations. `static` = persists between calls. `extern` = defined in another file. Swap without temp: `a=a+b; b=a-b; a=a-b`.


## Practice Questions (from Actual Model Exams)

### Q1: Trace the output
```java
int x = 7;
x++;
int y = x;
x = x * 3;
System.out.println("the value of y is " + y);
```
**Answer**: `the value of y is 8`

### Q2: For loop output
```java
int[] arr = {3,4,5,6,7};
for(int i = 0; i <= arr.length - 2; ++i) {
    System.out.println(arr[i] + ",");
}
```
**Answer**: `3,4,5,6` (loop runs while i ≤ 3, so i = 0,1,2,3)

### Q3: Increment operator
```java
int a = 4;
System.out.print(++a * 5);
```
**Answer**: `25` (prefix: a becomes 5, then 5*5)

### Q4: Python list assignment
```python
siTE = ['A', 'B', 'C', 'D']
siTE[1:4] = ['E', 'F', 'G']
print(siTE)
```
**Answer**: `['A', 'E', 'F', 'G']` (slice replacement)

### Q5: Python max on strings
```python
programming = ['Software', 'Electrical', 'Civil']
print(max(programming))
```
**Answer**: `Software` (alphabetically last)

### Q6: String comparison
```python
yourString = "Ethioipa"
stringList = ["Kenya", "South Africa", "Ethioipa"]
print(stringList[1] == yourString)
print(stringList[1] is yourString)
```
**Answer**: `False False` (different strings at different memory locations)

### Q7: Python type conversion
```python
x = int(float("10.0")) + float(int("20")) // 2
print(x)
```
**Answer**: `15.0` (int(10.0)=10, int("20")=20, float(20)//2 = 10.0, 10+10.0=15.0)

### Q8: For loop structure
Which is correct?
```
A. for(initialization; condition)
B. for(increment/decrement; initialization; condition)
C. for(condition, initialization, increment/decrement)
D. for(initialization; condition; increment/decrement)
```
**Answer**: D

### Q9: Error types
When running your program, you did not see any error. However, the final output is not correct. What type of error?
- A. Syntax error
- B. Compiling error
- C. Logical error
- D. Runtime error

**Answer**: C (Logical error)

### Q10: Array bounds exception
Given:
```java
public void setValue(int position, String valueIn) {
    list[position - 1] = valueIn;
}
```
What might cause ArrayIndexOutOfBoundsException?
- A. Return type being void
- B. Method having more than one parameter
- C. The value of the first parameter (position)
- D. Type of position being int

**Answer**: C (if position is 0 or greater than list.length+1)

---

## Key Exam Tips for Programming

1. **Trace code manually** — step through each line, track variable values
2. **Operator precedence** — memorize the order, especially ++ and --
3. **Array bounds** — arrays are 0-indexed; index ≤ length-1
4. **String vs char** — strings use "", chars use ''
5. **= vs ==** — assignment vs comparison
6. **break in switch** — without it, execution falls through to next case
7. **Parameter passing** — Java is pass-by-value always
8. **Static vs instance** — static belongs to class, instance belongs to object
9. **Constructor name** = class name, no return type
10. **Error categories** — syntax (compile-time), runtime, logical
