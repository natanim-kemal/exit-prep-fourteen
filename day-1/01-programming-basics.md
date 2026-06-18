# Fundamentals of Programming — Study Notes

## 1. Variables & Data Types

Variables store data in memory. Each variable has a name, type, and value. Common primitive types are `int` (integer), `float` (decimal), `char` (single character), `bool` (true/false), and `string` (text). In strongly-typed languages like C++/Java, you must declare the type before use.

**Variable naming rules:** Must start with a letter or underscore, cannot start with a digit, case-sensitive, cannot use reserved keywords. Example: `myVar`, `_count` (valid); `2fast`, `try` (invalid).

**Constants** are declared with `const` keyword and cannot change after initialization: `const float PI = 3.14;`

**Scope** determines where a variable is accessible:
- **Local**: declared inside a function, accessible only within that function (stored on stack)
- **Global**: declared outside all functions, accessible throughout the program
- **Block**: declared inside a block `{}`, accessible only within that block
- Variable shadowing occurs when a local variable hides a global variable within its scope

## 2. Operators

**Arithmetic**: `+`, `-`, `*`, `/`, `%` (modulo — returns remainder of division). Precedence: `*`, `/`, `%` before `+`, `-`.

**Relational**: `==`, `!=`, `<`, `>`, `<=`, `>=` — compare values, return boolean.

**Logical**: `&&` (AND), `||` (OR), `!` (NOT). Short-circuit evaluation means second operand is not evaluated if the first already determines the result.

**Assignment**: `=`, `+=`, `-=`, `*=`, `/=` — assign or modify a variable.

**Bitwise**: `&` (AND), `|` (OR), `^` (XOR), `~` (NOT/flip bits), `<<` (left shift), `>>` (right shift). XOR of 5^3 = 6 (101 ^ 011 = 110).

**Increment/Decrement**: `++i` (pre-increment: increment before use), `i++` (post-increment: use then increment).

**Ternary**: `condition ? value_if_true : value_if_false` — takes 3 operands.

**sizeof()**: returns memory size of a type/variable in bytes. `int` is typically 4 bytes on 32-bit systems.

## 3. Control Flow

### Selection
- **if-else**: executes code based on condition
- **switch-case**: multi-way branch; without `break`, execution falls through to the next case

### Loops
- **for**: best when iteration count is known in advance: `for(initialization; condition; increment)`
- **while**: condition is checked BEFORE the body executes
- **do-while**: guarantees at least one execution (condition checked AFTER body)
- **foreach**: iterates over collections

**Infinite loop**: occurs when loop condition never becomes false: `while(true){}`

**Jump statements**: `break` (exits loop immediately), `continue` (skips rest of current iteration), `return` (exits function). `loop` is NOT a valid jump statement.

## 4. Functions

A function is a reusable block of code. Key concepts:

**Declaration vs Definition**: Declaration states the function's signature (return type, name, parameters). Definition provides the body. A **prototype** declares the function before its first use.

**Parameters**:
- **Pass-by-value**: a copy of the argument is passed; original is not modified
- **Pass-by-reference**: modifies the original variable
- **Default parameters**: have default values if argument not provided

**Overloading**: same function name but different parameters (number or type). Cannot overload by return type alone.

**Return types**: `void` means returns nothing; `int` returns an integer value.

**`return` statement**: sends a value back to the caller in a non-void function.

**Multiple return values** can be achieved using structs or tuples.

## 5. Recursion

A function that calls itself. Requires two components:
1. **Base case**: stops the recursion (e.g., `factorial(0) = 1`, `factorial(1) = 1`)
2. **Recursive case**: function calls itself with modified parameters

**Call stack**: each recursive call pushes a new frame onto the stack. Recursion depth is limited by call stack size — too many calls cause stack overflow.

Example: `factorial(3)` = 3 × 2 × 1 = 6.

A recursive function with no base case causes infinite recursion (stack overflow).

## 6. Arrays & Strings

### Arrays
- **1D array**: contiguous memory locations of the same type: `int arr[5] = {1,2,3,4,5};`
- **Indexing**: first element is at index 0, last at index (size-1). `arr[2]` accesses the 3rd element.
- **Bounds**: accessing beyond array bounds causes undefined behavior (no automatic bounds check in C++)
- **2D array**: conceptually an array of arrays, uses two indices

### Vectors (C++ STL)
- Dynamic array that resizes automatically: `vector<int> v;`
- **push_back()**: adds element at the end
- **pop_back()**: removes the last element
- **size()**: returns number of elements

### Strings
- **Concatenation**: joining two strings together (operator `+` in many languages)
- `string` is NOT a primitive type in most languages (it's a class/object)

## 7. Pointers & Memory

- **Null pointer**: pointer to address 0 (nullptr/NULL)
- **new**: dynamically allocates memory on heap, returns pointer
- **delete**: frees dynamically allocated memory
- **Memory leak**: allocated memory that is never freed
- **`->` operator**: accesses a member of a struct via pointer
- **Call stack**: memory structure that tracks active function calls (LIFO)
- Local variables are stored on the **stack**

## 8. File I/O

**File streams in C++**: `ifstream` (reading only), `ofstream` (writing only), `fstream` (both reading and writing).

**File modes**: append mode (`ios::app`) adds data at the end without deleting existing content. Always check if file opened successfully before reading.

**Text vs Binary**: text files store human-readable characters; binary files store raw bytes.

## 9. Program Development

**IPO (Input-Process-Output)**: documents what goes in, the processing steps, and what comes out. Used in program design.

**Modular programming**: divides program into separate modules — main advantage is code reuse.

**Pseudocode**: informal high-level description of an algorithm (not actual code).

**Testing**: finds and fixes defects before deployment. **Maintenance**: updates and fixes after release.

**Debugging**: finding and fixing errors in code. A **debugger** helps step through code to find bugs.

## 10. Error Types
- **Syntax error**: violation of language grammar rules (caught by compiler)
- **Runtime error**: occurs during execution (e.g., division by zero)
- **Logical/Semantic error**: code runs but produces wrong output
- **Compile-time error**: caught by compiler

## 11. Other Key Concepts

- **Modulo operator `%`**: returns remainder of division (7 % 3 = 1)
- **Comments**: document code for humans; `//` for single-line, `/* */` for multi-line
- **Enum**: defines named integer constants
- **typedef**: creates an alias for a data type
- **struct**: groups different data types together
- **Header files (.h)**: contain declarations shared across files
- **Storage classes**: `static` (persists between calls), `extern` (defined in another file), `register` (suggest CPU register), `auto` (default local)
- **Swap without temp**: `a = a + b; b = a - b; a = a - b;`
- **Binary search**: requires array to be sorted
- **Linked list advantage** over array: dynamic size without reallocation
