# Day 1 — Code Trace Exercises (Exam-Style)

## Exercise Set 1: Variable & Operators

### Problem 1
```java
int a = 5;
int b = a++ + ++a;
System.out.println(b);
```
**Step-by-step:**
- `a++` uses 5, then a = 6
- `++a` increments to 7, then uses 7
- b = 5 + 7 = **12**

---

### Problem 2
```python
x = 10
y = x // 3 + x % 3
print(y)
```
**Step-by-step:**
- `10 // 3` = 3 (integer division)
- `10 % 3` = 1 (remainder)
- y = 3 + 1 = **4**

---

### Problem 3
```python
x = 5 * 2 + 3 // 4 + 10 ** 2
print(x)
```
**Step-by-step:**
- `10 ** 2` = 100 (exponentiation first)
- `5 * 2` = 10
- `3 // 4` = 0 (integer division)
- 10 + 0 + 100 = **110**

---

### Problem 4
```java
int x = 2, y = 3, z = 5;
boolean result = x < y && y < z || x > z;
System.out.println(result);
```
**Step-by-step:**
- `x < y` = true
- `y < z` = true
- `true && true` = true
- `x > z` = false
- `true || false` = **true**

---

### Problem 5
```python
x = not 2 + 3 == 5 or 5 + 2 <= 7 and 7 + 8 == 15
print(x)
```
**Step-by-step:**
- `2 + 3 == 5` → true
- `not true` → false
- `5 + 2 <= 7` → true
- `7 + 8 == 15` → true
- `true and true` → true
- `false or true` → **True**

---

## Exercise Set 2: Arrays

### Problem 6
```java
int[] arr = {10, 20, 30, 40, 50};
int sum = 0;
for (int i = 1; i < arr.length - 1; i++) {
    sum += arr[i];
}
System.out.println(sum);
```
**Trace:**
- i=1: sum+=20 → sum=20
- i=2: sum+=30 → sum=50
- i=3: sum+=40 → sum=90
- i=4: condition `i < 4` fails
- **Output: 90**

---

### Problem 7
```python
nums = [1, 2, 3, 4, 5]
nums[2:4] = [10, 20]
print(nums)
```
**Result:** `[1, 2, 10, 20, 5]`
(Slice indices 2 and 3 are replaced)

---

### Problem 8
```python
matrix = [[1,2],[3,4],[5,6]]
print(matrix[1][0])
print(len(matrix))
```
- `matrix[1][0]` = 3 (row 1, column 0)
- `len(matrix)` = 3 (3 rows)
- **Output: 3, 3**

---

## Exercise Set 3: Loops

### Problem 9
```java
int count = 0;
for (int i = 0; i < 5; i++) {
    for (int j = i; j < 5; j++) {
        count++;
    }
}
System.out.println(count);
```
**Trace:**
- i=0: j=0..4 → 5 iterations
- i=1: j=1..4 → 4 iterations
- i=2: j=2..4 → 3 iterations
- i=3: j=3..4 → 2 iterations
- i=4: j=4..4 → 1 iteration
- Total: 5+4+3+2+1 = **15**

---

### Problem 10
```java
int x = 5, y = 1;
while (x > 0) {
    y *= x;
    x--;
}
System.out.println(y);
```
**Trace:**
- x=5: y=1*5=5
- x=4: y=5*4=20
- x=3: y=20*3=60
- x=2: y=60*2=120
- x=1: y=120*1=120
- x=0: loop stops
- **Output: 120** (5! = factorial)

---

## Exercise Set 4: Methods & Recursion

### Problem 11
```java
public static int mystery(int n) {
    if (n <= 0) return 0;
    return n + mystery(n - 2);
}
System.out.println(mystery(6));
```
**Trace:**
- mystery(6) = 6 + mystery(4)
- mystery(4) = 4 + mystery(2)
- mystery(2) = 2 + mystery(0)
- mystery(0) = 0
- Back: 2+0=2, 4+2=6, 6+6=**12**

---

### Problem 12
```java
public static int func(int a, int b) {
    if (b == 0) return a;
    return func(b, a % b);
}
System.out.println(func(48, 18));
```
**Trace:**
- func(48, 18) → func(18, 48%18=12)
- func(18, 12) → func(12, 18%12=6)
- func(12, 6) → func(6, 12%6=0)
- func(6, 0) → return 6
- **Output: 6** (GCD of 48 and 18)

---

## Exercise Set 5: Exception Handling

### Problem 13
```java
try {
    int[] arr = new int[5];
    arr[10] = 100;
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Out of bounds");
} catch (Exception e) {
    System.out.println("General error");
} finally {
    System.out.println("Done");
}
```
**Output:**
```
Out of bounds
Done
```
(Finally always executes, even after catch)

---

### Problem 14
```java
public static int divide(int a, int b) throws ArithmeticException {
    return a / b;
}

public static void main(String[] args) {
    try {
        System.out.println(divide(10, 0));
    } catch (ArithmeticException e) {
        System.out.println("Cannot divide by zero");
    }
}
```
**Output:** `Cannot divide by zero`

---

## Exercise Set 6: String Operations

### Problem 15
```java
String s = "programming";
System.out.println(s.substring(3, 7));
System.out.println(s.indexOf("gram"));
```
- `substring(3,7)` → indices 3-6 = **"gram"**
- `indexOf("gram")` → **3**

---

### Problem 16
```python
text = "exit exam"
print(text.upper())
print(text.replace("exit", "final"))
```
- `upper()` → `"EXIT EXAM"`
- `replace("exit", "final")` → `"final exam"`

---

## Exercise Set 7: Problem-Solving Logic

### Problem 17
What does this algorithm output?
```
Set total = 0
Set i = 1
While i <= 10:
    If i % 2 == 0:
        total = total + i
    i = i + 1
Print total
```
**Trace:** Sum of even numbers 2+4+6+8+10 = **30**

---

### Problem 18
How many times does "Hello" print?
```python
for i in range(3):
    for j in range(2):
        print("Hello")
```
3 × 2 = **6 times**

---

## Exercise Set 8: Advanced — Integer Overflow & Promotion

### Problem 19
```java
byte b = (byte) 300;
System.out.println(b);
```
**Trace:**
- 300 in binary: `0001 0010 1100`
- byte is 8 bits: takes lower 8 = `0010 1100` = 44
- But `300 mod 256 = 44`, and byte signed range is -128 to 127
- **Output**: `44`

---

### Problem 20 — Short-Circuit Evaluation
```java
int x = 10;
boolean result = (x > 20) && (++x > 0);
System.out.println(x + ", " + result);
```
**Trace:**
- `x > 20` is false → short-circuit: `++x` is **NOT evaluated**
- x stays 10
- **Output**: `10, false`

---

### Problem 21 — Integer Promotion
```java
byte a = 5, b = 10;
// byte c = a + b;  // would NOT compile — why?
int c = a + b;
System.out.println(c);
```
**Answer**: `a + b` promotes both to `int`, result is `int`. Cannot assign `int` to `byte` without cast.
**Output**: `15`

---

### Problem 22 — Varargs
```java
public static int sum(int... nums) {
    int s = 0;
    for (int n : nums) s += n;
    return s;
}
System.out.println(sum(1, 2, 3, 4, 5));
System.out.println(sum());
```
**Output**: `15` and `0`

---

### Problem 23 — Autoboxing
```java
Integer a = 127;
Integer b = 127;
Integer c = 128;
Integer d = 128;
System.out.println(a == b);
System.out.println(c == d);
```
**Answer**: `true` then `false`. Java caches Integer from -128 to 127. Outside range, new objects created.
Use `.equals()` for reliable comparison.

---

### Problem 24 — For-each with array modification
```java
int[] arr = {1, 2, 3, 4};
for (int x : arr) {
    x = x * 2;
}
System.out.println(arr[0] + ", " + arr[1]);
```
**Answer**: `1, 2` — for-each gives a **copy** of each element for primitives. Original array unchanged.

---

### Problem 25 — Enhanced switch
```java
String day = "MONDAY";
int result = switch (day) {
    case "MONDAY", "FRIDAY" -> 1;
    case "WEDNESDAY" -> 2;
    default -> 0;
};
System.out.println(result);
```
**Answer**: `1`

---

### Problem 26 — StringBuilder
```java
StringBuilder sb = new StringBuilder("ABC");
sb.append("DEF");
sb.insert(2, "XYZ");
System.out.println(sb);
```
**Trace:**
- Start: "ABC"
- append: "ABCDEF"
- insert at index 2: "AB" + "XYZ" + "CDEF"
- **Output**: `ABXYZCDEF`

---

### Problem 27 — Bitwise
```java
System.out.println(5 & 3);    // 101 & 011 = 001 = 1
System.out.println(5 | 3);    // 101 | 011 = 111 = 7
System.out.println(5 ^ 3);    // 101 ^ 011 = 110 = 6
System.out.println(5 << 1);   // 1010 = 10
```
**Output**: `1, 7, 6, 10`

---

### Problem 28 — Variable Scope
```java
public class Scope {
    static int x = 10;
    public static void main(String[] args) {
        int x = 20;
        System.out.println(x);
        System.out.println(Scope.x);
    }
}
```
**Answer**: `20` (local shadows static), `10` (qualified access)

---

## Problem 29 — Decimal to Binary Conversion (Algorithm Design)
Write an algorithm (pseudocode) to convert a decimal number to binary.

**Solution:**
```
Input: decimal number n
Output: binary string

Set result = ""
While n > 0:
    Set remainder = n % 2
    Prepend remainder to result
    Set n = n / 2   (integer division)
Print result
```

---

## Common Exam Traps (Extended)

| Trap | Example | Why It's Wrong |
|------|---------|----------------|
| **Off-by-one** | `i <= arr.length` | Should be `< arr.length` |
| **= vs ==** | `if (x = 5)` | Assignment, not comparison |
| **Missing break** | switch without break | Falls through to next case |
| **Static context** | Calling non-static from static | Need object reference |
| **Integer division** | `5/2` returns `2` (not 2.5) | Use double for precision |
| **Null reference** | `arr.length` when arr is null | NullPointerException |
| **String ==** | `s1 == s2` | Compares references, not content |
| **Postfix vs prefix** | `a++` vs `++a` | Postfix returns old value first |
| **Integer overflow** | `byte b = 200` | Range is -128 to 127 |
| **Short-circuit** | `x > 0 && x/y > 1` with y=0 | If x>0 false, y not evaluated |
| **Autoboxing cache** | `Integer c = 128; d = 128; c == d` | false (outside -128..127) |
| **For-each modification** | `for (int x : arr) { x *= 2; }` | x is a copy, original unchanged |
| **Shadowing** | local var = field name | Local hides field; use `this.` or `ClassName.` |

---

## Quick Reference Card

```
Variable Naming:  letter/underscore/$ + letters/digits/underscore
Array Indexing:   0 to length-1
String compare:   .equals() not ==
Modulo:           a % b = remainder of a/b
Integer division: a/b truncates toward zero
Prefix ++a:       increment then use
Postfix a++:      use then increment
try-catch-finally: finally ALWAYS runs
Constructor:      same name as class, no return type
Method overload:  same name, different parameters
Array init:       {val1, val2, val3} or new type[size]
Type casting:     (int)3.14 → 3, int(float("10.0")) → 10

Widening:  byte→short→int→long→float→double (automatic)
Narrowing: reverse direction → explicit cast needed
Integer cache: -128 to 127 for Integer.valueOf/autoboxing
Varargs:   type... name — last parameter only
For-each:  for (type var : collection) — read-only access
Short-circuit: && stops at false, || stops at true
Bitwise <<:  multiply by 2^n
Bitwise >>:  divide by 2^n
```
