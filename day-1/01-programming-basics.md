# Day 1 — Fundamentals of Programming (134 Items)

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


## Practice Questions (from Question Bank)

### Q1. Which loop is guaranteed to execute at least once?

- A) foreach
- B) while
- C) for
- D) do-while
  **Answer: D**

### Q2. Which of the following best describes output of: x=5; for i=1 to 3: x=x*i; print x?

- A) 60
- B) 125
- C) 30
- D) 15
  **Answer: C**

### Q3. In pass-by-reference, modifying the parameter inside a function:?

- A) Deletes the original
- B) Modifies a copy
- C) Modifies the original variable
- D) Has no effect on original
  **Answer: C**

### Q4. Which of the following best describes base case of factorial(n)?

- A) n==2 returns 2
- B) n==1 returns n
- C) n==0 returns 1
- D) n>0 returns n
  **Answer: C**

### Q5. Which statement about Variable shadowing is correct?

- A) Constant masks variable
- B) Global overrides local
- C) Two vars share memory
- D) Local hides global within scope
  **Answer: D**

### Q6. When designing for high performance, which C++ stream handles both reading and writing?

- A) fstream
- B) ofstream
- C) ifstream
- D) iostream
  **Answer: A**

### Q7. A 2D array is conceptually:?

- A) Tree with 2 children
- B) Linked list of stacks
- C) Hash table with row keys
- D) Array of arrays
  **Answer: D**

### Q8. How is Implicit type conversion best characterized?

- A) Compiler converts automatically
- B) Runtime type error
- C) Library function converts
- D) Programmer casts manually
  **Answer: A**

### Q9. Consider a system where which operator checks NOT equal in C++?

- A) !=
- B) <>
- C) ~=
- D) =/=
  **Answer: A**

### Q10. Main advantage of modular programming:?

- A) Promotes code reuse
- B) Harder to debug
- C) Uses more memory
- D) Prevents recursion
  **Answer: A**

### Q11. Append mode when opening a file:?

- A) Overwrites from beginning
- B) Opens read-only
- C) Always creates new file
- D) Adds at end without deleting
  **Answer: D**

### Q12. Which of the following best describes NOT a valid jump statement?

- A) continue
- B) break
- C) return
- D) loop
  **Answer: D**

### Q13. How is Function overloading best characterized?

- A) Too many arguments
- B) Same name different parameters
- C) Function calls itself
- D) Calling function many times
  **Answer: B**

### Q14. No 'break' in switch-case causes:?

- A) Fall-through to next case
- B) Compile error
- C) Only matched case runs
- D) Program terminates
  **Answer: A**

### Q15. When designing for high performance, last index of int arr[10] in C++?

- A) 0
- B) 10
- C) 9
- D) 1
  **Answer: C**

### Q16. What does a flowchart diamond shape represent?

- A) Start/end
- B) Process/action
- C) Input/output
- D) Decision/condition
  **Answer: D**

### Q17. Which data type stores TRUE or FALSE?

- A) float
- B) bool
- C) char
- D) int
  **Answer: B**

### Q18. Identify the correct statement about scope of a variable declared inside a function.

- A) Available in all files
- B) Local to that function
- C) Accessible only in loops
- D) Global
  **Answer: B**

### Q19. What does IPO stand for in program design?

- A) Index-Position-Offset
- B) Integer-Pointer-Object
- C) Instruction-Program-Operation
- D) Input-Process-Output
  **Answer: D**

### Q20. Which loop is best when iteration count is known in advance?

- A) recursion
- B) while
- C) for
- D) do-while
  **Answer: C**

### Q21. When designing for high performance, which description of constant in programming is accurate?

- A) A function with no return value
- B) A pointer to memory
- C) A variable that changes often
- D) A named value that cannot change
  **Answer: D**

### Q22. How is Pass-by-value best characterized?

- A) A copy of the argument is passed
- B) Original is modified
- C) Only pointers are passed
- D) Both copies change together
  **Answer: A**

### Q23. Recursion requires which two components?

- A) Array and pointer
- B) Loop and condition
- C) Function and variable
- D) Base case and recursive case
  **Answer: D**

### Q24. Consider a system where what does the modulo operator (%) return?

- A) Quotient of division
- B) Power of a number
- C) Absolute value
- D) Remainder of division
  **Answer: D**

### Q25. Which of these is a relational operator?

- A) <<
- B) ++
- C) &&
- D) >=
  **Answer: D**

### Q26. Which of the following best describes vector in C++?

- A) A fixed-size array
- B) A pointer to an array
- C) A dynamic array that resizes
- D) A 2D matrix
  **Answer: C**

### Q27. Consider a system where which method removes the last element from a C++ vector?

- A) pop_back
- B) remove
- C) erase_last
- D) delete
  **Answer: A**

### Q28. Which description of string concatenation is accurate?

- A) Comparing two strings
- B) Joining two strings together
- C) Reversing a string
- D) Splitting a string
  **Answer: B**

### Q29. What does 'return 0' at end of main() indicate?

- A) Program terminated abnormally
- B) Successful program execution
- C) Error occurred
- D) Memory was freed
  **Answer: B**

### Q30. Consider a system where local variables are stored in:?

- A) Global memory
- B) Heap
- C) Stack
- D) Register always
  **Answer: C**

### Q31. Which of the following best describes pseudocode?

- A) Informal high-level description of
- B) Binary representation of code
- C) A programming language like Python
- D) Compiled code in disguise
  **Answer: A**

### Q32. Which arithmetic operator has highest precedence?

- A) -
- B) +
- C) *
- D) %
  **Answer: C**

### Q33. In a resource-constrained environment, an infinite loop occurs when:?

- A) Loop runs exactly once
- B) Loop condition never becomes false
- C) Break is used inside loop
- D) Loop variable is negative
  **Answer: B**

### Q34. Which description of purpose of a function prototype is accurate?

- A) Declares function signature before use
- B) Defines function body
- C) Allocates memory for function
- D) Calls the function
  **Answer: A**

### Q35. Which description of difference between '=' and '==' in C++ is accurate?

- A) Both check equality
- B) '=' assigns value
- C) '==' assigns value
- D) No difference
  **Answer: B**

### Q36. When designing for high performance, which file mode opens for reading only?

- A) ifstream
- B) fstream
- C) rwstream
- D) ofstream
  **Answer: A**

### Q37. What does a do-while loop guarantee compared to while?

- A) No condition needed
- B) At least one execution of the body
- C) Faster execution
- D) Counter always increments
  **Answer: B**

### Q38. Which of the following best describes n algorithm?

- A) A step-by-step procedure
- B) A programming language
- C) A type of loop
- D) A data structure
  **Answer: A**

### Q39. When designing for high performance, what is the primary function of is?

- A) |
- B) &
- C) ||
- D) &&
  **Answer: D**

### Q40. Which of the following best describes output of: x=10; x+=5; print x?

- A) 15
- B) 5
- C) 50
- D) 10
  **Answer: A**

### Q41. What happens when you access index beyond array bounds in C++?

- A) Compile error always
- B) Undefined behavior
- C) Exception is thrown always
- D) Returns 0
  **Answer: B**

### Q42. Which of the following best describes correct way to declare a constant in C++?

- A) const float PI = 3.14
- B) final float PI = 3.14
- C) static PI = 3.14
- D) var PI = 3.14
  **Answer: A**

### Q43. What does 'void' mean as a function return type?

- A) Function has no parameters
- B) Returns zero
- C) Returns nothing
- D) Returns null pointer
  **Answer: B**

### Q44. Nested loops have what time complexity when both run n times?

- A) O2n
- B) On log n
- C) On²
- D) On
  **Answer: C**

### Q45. Consider a system where which statement exits only the current loop iteration?

- A) exit
- B) continue
- C) break
- D) return
  **Answer: B**

### Q46. Which description of index of the FIRST element in an array is accurate?

- A) 1
- B) Depends on language
- C) -1
- D) 0
  **Answer: D**

### Q47. Which bitwise operator flips all bits?

- A) |
- B) ~
- C) ^
- D) &
  **Answer: B**

### Q48. In a resource-constrained environment, which description of struct in C++ is accurate?

- A) A loop construct
- B) Groups different data
- C) A function type
- D) A pointer type
  **Answer: B**

### Q49. An enum in C++ is used to define:?

- A) Dynamic arrays
- B) Named integer constants
- C) String collections
- D) Floating point sets
  **Answer: B**

### Q50. Which of the following best describes 'typedef' used for in C++?

- A) Allocates memory
- B) Declares a constant
- C) Creates an alias for a data type
- D) Defines a new function
  **Answer: C**

### Q51. Identify the correct statement about n example of an IPO diagram use.

- A) Creating a class hierarchy
- B) Drawing network topology
- C) Designing database schema
- D) Documenting input, processing
  **Answer: D**

### Q52. What does short-circuit evaluation mean in logical operators?

- A) Both operands always evaluated
- B) Logical operators have no precedence
- C) Second operand not evaluated if first
- D) Operators execute faster on small values
  **Answer: C**

### Q53. Which description of result of 7 % 3 is accurate?

- A) 0
- B) 2
- C) 1
- D) 3
  **Answer: C**

### Q54. Consider a system where which loop structure checks condition AFTER executing body?

- A) do-while
- B) for
- C) foreach
- D) while
  **Answer: A**

### Q55. What does the 'break' statement do inside a loop?

- A) Skips current iteration
- B) Exits the loop immediately
- C) Goes to next function
- D) Restarts the loop
  **Answer: B**

### Q56. Which of these correctly initializes a 1D array of 5 integers in C++?

- A) int arr[5] = {1,2,3,4,5}
- B) int[5] arr
- C) array<int> arr
- D) int arr = {1,2,3,4,5}
  **Answer: A**

### Q57. When designing for high performance, recursion depth is limited by:?

- A) CPU speed
- B) Call stack size
- C) Heap size
- D) Array length
  **Answer: B**

### Q58. Identify the correct statement about call stack.

- A) Queue of processes waiting
- B) Array of function pointers
- C) Memory structure tracking active
- D) Memory for global variables
  **Answer: C**

### Q59. Which data type can store a single character?

- A) string
- B) char
- C) int
- D) bool
  **Answer: B**

### Q60. Identify the correct statement about purpose of 'return' in a non-void function.

- A) Sends a value back to the caller
- B) Exits the program
- C) Frees memory
- D) Prints output
  **Answer: A**

### Q61. Which of the following is a logical operator?

- A) ++
- B) ||
- C) !=
- D) >=
  **Answer: B**

### Q62. Which description of difference between compile-time and runtime errors is accurate?

- A) Runtime caught by compiler
- B) No difference
- C) Both occur during execution
- D) Compile-time caught by compiler
  **Answer: D**

### Q63. Consider a system where two-dimensional arrays use how many indices?

- A) One
- B) Depends on language
- C) Three
- D) Two
  **Answer: D**

### Q64. Which type conversion can cause data loss?

- A) float to double
- B) char to int
- C) int to float
- D) double to int
  **Answer: D**

### Q65. Identify the correct statement about purpose of comments in code.

- A) They improve runtime speed
- B) They are executed by the compiler
- C) They document code for human
- D) They declare variables
  **Answer: C**

### Q66. Which keyword in C++ declares a variable whose value cannot change after initialization?

- A) extern
- B) static
- C) const
- D) volatile
  **Answer: C**

### Q67. What does 'scope' mean in programming?

- A) The memory address of a variable
- B) The size of a variable
- C) The type of a variable
- D) The region where a variable is accessible
  **Answer: D**

### Q68. Which of the following best describes valid way to check if x is between 1 and 10 inclusive in C++?

- A) x >= 1 || x <= 10
- B) 1 <= x OR x <= 10
- C) 1 < x < 10
- D) x >= 1 && x <= 10
  **Answer: D**

### Q69. In a resource-constrained environment, overloaded functions must differ in:?

- A) Function name
- B) Number
- C) Return type only
- D) Scope
  **Answer: B**

### Q70. Which of the following best describes output of: for(int i=0;i<3;i++) cout<<i;?

- A) 012
- B) 1 2 3
- C) 123
- D) 0 1 2
  **Answer: A**

### Q71. Global variables are accessible:?

- A) Only inside main
- B) Throughout the entire program
- C) Only inside functions
- D) Only in header files
  **Answer: B**

### Q72. Identify the correct statement about text file vs binary file.

- A) No difference
- B) Text stores human-readable chars
- C) Binary is slower to read
- D) Text files are larger always
  **Answer: B**

### Q73. Which error check is essential before reading from a file?

- A) Check CPU speed
- B) Check available RAM
- C) Check file size
- D) Check if file opened successfully
  **Answer: D**

### Q74. Which of the following best describes XOR bitwise operator (^) result of 5^3?

- A) 15
- B) 8
- C) 2
- D) 6
  **Answer: D**

### Q75. Which description of difference between ++i and i++ is accurate?

- A) i++ increments before use
- B) No difference
- C) ++i adds 2
- D) ++i increments before use
  **Answer: D**

### Q76. Which of these is an example of a high-level language?

- A) Machine code
- B) Assembly
- C) Python
- D) Binary
  **Answer: C**

### Q77. Which of the following best describes purpose of a debugger?

- A) Format source code
- B) Compile source code
- C) Step through code to find
- D) Optimize code speed
  **Answer: C**

### Q78. When designing for high performance, a function that returns no value uses which return type?

- A) empty
- B) null
- C) void
- D) none
  **Answer: C**

### Q79. Identify the correct statement about output of: int x=3; cout << x*x+1;.

- A) 9
- B) 7
- C) 13
- D) 10
  **Answer: D**

### Q80. Which of the following searches require array to be sorted?

- A) Brute-force search
- B) Linear search
- C) Sequential search
- D) Binary search
  **Answer: D**

### Q81. In a resource-constrained environment, what does endl do in C++?

- A) Inserts newline and flushes buffer
- B) Declares end of array
- C) Closes file stream
- D) Ends the program
  **Answer: A**

### Q82. Multiple return values from a function in C++ can be achieved using:?

- A) Global variables only
- B) Structs
- C) Arrays of booleans
- D) Multiple return statements
  **Answer: B**

### Q83. Identify the correct statement about size of int in most 32-bit C++ systems.

- A) 1 byte
- B) 8 bytes
- C) 4 bytes
- D) 2 bytes
  **Answer: C**

### Q84. Which storage class makes a variable persist between function calls?

- A) register
- B) static
- C) auto
- D) extern
  **Answer: B**

### Q85. What does 'extern' mean in C++?

- A) Variable is on heap
- B) Variable is local to block
- C) Variable is constant
- D) Variable is defined in another file
  **Answer: D**

### Q86. Which of the following best describes purpose of a header file (.h) in C++?

- A) Stores compiled object code
- B) Defines the main function
- C) Holds executable code
- D) Contains declarations shared
  **Answer: D**

### Q87. Consider a system where what happens if a recursive function has no base case?

- A) It returns 0
- B) It runs once
- C) Compiler catches it
- D) It causes infinite
  **Answer: D**

### Q88. Which of these is NOT a primitive data type in most languages?

- A) float
- B) bool
- C) string
- D) int
  **Answer: C**

### Q89. Identify the correct statement about output of: int a=5,b=3; cout<<(a>b?a:b);.

- A) 5
- B) 3
- C) 0
- D) 8
  **Answer: A**

### Q90. When designing for high performance, the ternary operator ?: takes how many operands?

- A) 2
- B) 1
- C) 4
- D) 3
  **Answer: D**

### Q91. Which loop would you use to read lines from a file until EOF?

- A) while loop checking EOF condition
- B) nested for loop
- C) for loop with known count
- D) do-while always
  **Answer: A**

### Q92. Which of the following best describes syntax error?

- A) Error in program logic
- B) Memory allocation failure
- C) Violation of language grammar rules
- D) Error during file I/O
  **Answer: C**

### Q93. Consider a system where which description of semantic error is accurate?

- A) Runtime crash
- B) Code runs but produces wrong
- C) Uninitialized variable always
- D) Grammar mistake in code
  **Answer: B**

### Q94. Which description of output of: cout<<(10/3); is accurate?

- A) 3
- B) 4
- C) 3.33
- D) 3.0
  **Answer: A**

### Q95. Which of the following best describes output of: cout<<(10.0/3);?

- A) 3.33333
- B) 3.3
- C) 3
- D) Error
  **Answer: A**

### Q96. Which of the following best describes linked list's advantage over an array?

- A) Less memory per element
- B) Dynamic size without
- C) Faster sorting
- D) Faster random access
  **Answer: B**

### Q97. Which of these is NOT a valid variable name in C++?

- A) myVar
- B) totalSum
- C) 2fast
- D) _count
  **Answer: C**

### Q98. What does the sizeof() operator return?

- A) Memory size in bytes of a type
- B) Number of elements
- C) Maximum value of type
- D) Index of last element
  **Answer: A**

### Q99. Consider a system where which of the following best describes null pointer?

- A) Pointer to last element
- B) Pointer with no type
- C) Pointer to a deleted object
- D) Pointer to address 0
  **Answer: D**

### Q100. Which operator is used to access a member of a struct via pointer?

- A) ->
- B) .
- C) *
- D) ::
  **Answer: A**

### Q101. Identify the correct statement about purpose of the 'new' keyword in C++.

- A) Creates a new file
- B) Imports a module
- C) Declares a new variable
- D) Dynamically allocates
  **Answer: D**

### Q102. Identify the correct statement about purpose of 'delete' in C++.

- A) Closes a stream
- B) Removes a variable from
- C) Removes a file
- D) Frees dynamically
  **Answer: D**

### Q103. Which description of memory leak is accurate?

- A) Allocated memory not freed
- B) Writing beyond array bounds
- C) Stack overflow
- D) Data being read incorrectly
  **Answer: A**

### Q104. Which of the following correctly swaps two integer variables a and b without a temp variable?

- A) a=b
- B) a=a+b
- C) a*=b
- D) swap only
  **Answer: B**

### Q105. Which description of n identifier in programming is accurate?

- A) A memory address
- B) An operator
- C) A name given to variables
- D) A data type
  **Answer: C**

### Q106. Which of the following is a unary operator?

- A) *
- B) %
- C) +
- D) !
  **Answer: D**

### Q107. Which of the following best describes correct syntax for a single-line comment in C++?

- A) /* comment */
- B) // comment
- C) <!-- comment -->
- D) # comment
  **Answer: B**

### Q108. Identify the correct statement about multi-line comment syntax in C++.

- A) /* ... */
- B) <!-- ... -->
- C) # ... #
- D) // ... //
  **Answer: A**

### Q109. Identify the correct statement about output of: int arr[]={1,2,3}; cout<<arr[1];.

- A) 0
- B) 3
- C) 1
- D) 2
  **Answer: D**

### Q110. Which of the following best describes true about function parameters in C++?

- A) Parameters are always passed by reference
- B) Only primitive types can be parameters
- C) Parameters can be passed by value
- D) Parameters must have default values
  **Answer: C**

### Q111. Which of the following best describes difference between declaration and definition?

- A) Definition states type
- B) Both always occur together
- C) Declaration states type/name
- D) No difference
  **Answer: C**

### Q112. Identify the correct statement about output of: int x=1; while(x<5){x*=2;} cout<<x;.

- A) 8
- B) 5
- C) 2
- D) 4
  **Answer: A**

### Q113. Identify the correct statement about NOT a stage in the program development process.

- A) Problem analysis
- B) Algorithm design
- C) Testing
- D) Marketing
  **Answer: D**

### Q114. Which description of purpose of testing in software development is accurate?

- A) Design the user interface
- B) Write more code
- C) Compile the source code
- D) Find and fix defects before
  **Answer: D**

### Q115. What does 'maintenance' mean in the program development process?

- A) Testing before release
- B) Updates and fixes after
- C) Designing algorithms
- D) Rewriting the entire program
  **Answer: B**

### Q116. Which of the following best describes output of this recursive call: fact(3)?  (fact(0)=1, fact(n)=n*fact(n-1))?

- A) 1
- B) 6
- C) 9
- D) 3
  **Answer: B**

### Q117. In a resource-constrained environment, what does a return type of 'int' mean for a function?

- A) Function returns an integer value
- B) Function uses integer variables internally
- C) Function has integer loops
- D) Function takes integer parameter
  **Answer: A**

### Q118. Which of the following is an example of an assignment operator?

- A) !=
- B) ==
- C) +=
- D) >=
  **Answer: C**

### Q119. Identify the correct statement about output of: int x=5; x-=3; cout<<x;.

- A) 5
- B) 2
- C) 3
- D) 8
  **Answer: B**

### Q120. Consider a system where a 'while' loop with condition 'while(true)' creates:?

- A) A loop that runs once
- B) A loop that runs 10 times
- C) An infinite loop
- D) A compile error
  **Answer: C**

### Q121. Which of the following best describes main purpose of code indentation?

- A) Required by all compilers
- B) Improves code readability
- C) Prevents memory leaks
- D) Reduces execution time
  **Answer: B**

### Q122. Which description of output of: for(int i=5;i>0;i--) cout<<i<<" "; is accurate?

- A) 0 1 2 3 4
- B) 5 4 3 2 1
- C) 5 4 3 2 1 0
- D) 1 2 3 4 5
  **Answer: B**

### Q123. Which of the following correctly describes type casting in C++?

- A) Automatic type change by OS
- B) Explicit conversion from one type
- C) Comparing two different types
- D) Changing variable name
  **Answer: B**

### Q124. Identify the correct statement about output of: cout<<(5==5);.

- A) 5
- B) true
- C) 1
- D) equal
  **Answer: C**

### Q125. What does 'push_back()' do in a C++ vector?

- A) Sorts the vector
- B) Returns last element
- C) Removes last element
- D) Adds element at the end
  **Answer: D**

### Q126. In a resource-constrained environment, which description of 'size()' in a C++ vector is accurate?

- A) Returns memory size in bytes
- B) Returns last index
- C) Returns max capacity
- D) Returns number of elements
  **Answer: D**

### Q127. Which of the following BEST describes an IPO chart?

- A) Shows what goes in, what
- B) Diagrams object inheritance
- C) Displays memory allocation
- D) Maps function calls
  **Answer: A**

### Q128. Identify the correct statement about main risk of using global variables.

- A) They use more CPU
- B) They can be accidentally
- C) They cannot store complex types
- D) They are slower to access
  **Answer: B**

### Q129. When designing for high performance, what type of error occurs when dividing by zero at runtime?

- A) Syntax error
- B) Runtime error
- C) Compile error
- D) Logical error
  **Answer: B**

### Q130. What does the 'continue' statement do inside a for loop?

- A) Skips rest of current
- B) Exits the loop
- C) Restarts loop from
- D) Jumps to outer loop
  **Answer: A**

### Q131. If int arr[3]={10,20,30}, what is arr[2]?

- A) 20
- B) 10
- C) 30
- D) undefined
  **Answer: C**

### Q132. When designing for high performance, which of the following best describes a 'while' loop?

- A) Cannot be nested
- B) Only used with counters
- C) Condition is checked before
- D) Always runs at least once
  **Answer: C**

### Q133. Which of the following best describes output of: int a=2,b=3; cout<<a<<b;?

- A) 5
- B) 6
- C) 2 3
- D) 23
  **Answer: D**

### Q134. Which statement best describes 'debugging'?

- A) Compiling source code
- B) Designing program logic
- C) Finding and fixing errors in code
- D) Writing test cases
  **Answer: C**

