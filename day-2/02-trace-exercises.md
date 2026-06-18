# Day 2 — OOP Code Trace Exercises (Exam-Style)

## Set 1: Class & Object Tracing

### Problem 1 — Constructor + Method Chain
```java
class Box {
    private int width, height, depth;
    
    public Box() { width = 1; height = 1; depth = 1; }
    public Box(int w, int h, int d) { width = w; height = h; depth = d; }
    public int volume() { return width * height * depth; }
}

public class TestBox {
    public static void main(String[] args) {
        Box b1 = new Box();
        Box b2 = new Box(2, 3, 4);
        System.out.println(b1.volume() + ", " + b2.volume());
    }
}
```
**Trace:**
- b1: default constructor → 1×1×1 = 1
- b2: parameterized → 2×3×4 = 24
- **Output**: `1, 24`

---

### Problem 2 — Setter After Constructor
```java
class Student {
    private String name;
    private int id;
    
    public Student(String n, int i) { name = n; id = i; }
    public void setName(String n) { name = n; }
    public String getName() { return name; }
}

public class TestStudent {
    public static void main(String[] args) {
        Student s = new Student("Abebe", 101);
        s.setName("Kebede");
        System.out.println(s.getName());
    }
}
```
**Trace:**
- Constructor sets name = "Abebe"
- setName("Kebede") changes to "Kebede"
- **Output**: `Kebede`

---

### Problem 3 — Reference Assignment
```java
class Point {
    int x, y;
    Point(int x, int y) { this.x = x; this.y = y; }
}

public class TestPoint {
    public static void main(String[] args) {
        Point p1 = new Point(2, 3);
        Point p2 = p1;
        p2.x = 10;
        System.out.println(p1.x + ", " + p1.y);
    }
}
```
**Trace:**
- p1 → Point(2, 3) at memory address 0x100
- p2 → same address 0x100 (reference copy)
- p2.x = 10 changes the same object
- **Output**: `10, 3`

---

## Set 2: Inheritance

### Problem 4 — Overriding
```java
class Animal {
    public String sound() { return "Generic"; }
}

class Cat extends Animal {
    public String sound() { return "Meow"; }
}

class Dog extends Animal {
    public String sound() { return "Bark"; }
}

public class TestAnimals {
    public static void main(String[] args) {
        Animal a1 = new Cat();
        Animal a2 = new Dog();
        Animal a3 = new Animal();
        System.out.println(a1.sound() + " " + a2.sound() + " " + a3.sound());
    }
}
```
**Trace:**
- a1 is Cat → "Meow"
- a2 is Dog → "Bark"
- a3 is Animal → "Generic"
- **Output**: `Meow Bark Generic`

---

### Problem 5 — super + constructor chain
```java
class Parent {
    Parent() { System.out.print("Parent "); }
}

class Child extends Parent {
    Child() {
        super();  // calls Parent() — implicit even without writing it
        System.out.print("Child ");
    }
}

public class TestInherit {
    public static void main(String[] args) {
        Child c = new Child();
    }
}
```
**Trace:**
- Child() called → first statement is super() → prints "Parent "
- Back to Child() → prints "Child "
- **Output**: `Parent Child`

---

### Problem 6 — Polymorphic Array
```java
class Shape {
    public String type() { return "Shape"; }
}
class Circle extends Shape {
    public String type() { return "Circle"; }
}
class Square extends Shape {
    public String type() { return "Square"; }
}

public class TestShapes {
    public static void main(String[] args) {
        Shape[] shapes = { new Circle(), new Shape(), new Square() };
        for (Shape s : shapes) {
            System.out.print(s.type() + " ");
        }
    }
}
```
**Output**: `Circle Shape Square`

---

## Set 3: Static Context

### Problem 7 — Static Variable
```java
class Account {
    static int totalAccounts = 0;
    int accountId;
    
    Account() {
        totalAccounts++;
        accountId = totalAccounts;
    }
}

public class TestAccount {
    public static void main(String[] args) {
        Account a1 = new Account();
        Account a2 = new Account();
        Account a3 = new Account();
        System.out.println(a2.accountId + ", " + Account.totalAccounts);
    }
}
```
**Trace:**
- a1: totalAccounts=1, accountId=1
- a2: totalAccounts=2, accountId=2
- a3: totalAccounts=3, accountId=3
- **Output**: `2, 3`

---

### Problem 8 — Static Method
```java
class MathUtils {
    public static int square(int x) { return x * x; }
    public int cube(int x) { return x * x * x; }
}

public class TestMath {
    public static void main(String[] args) {
        System.out.println(MathUtils.square(5));
        // System.out.println(MathUtils.cube(5));  // would NOT compile — cube is not static
        MathUtils m = new MathUtils();
        System.out.println(m.cube(3));
    }
}
```
**Output**: `25, 27`

---

## Set 4: Abstract & Interface

### Problem 9 — Abstract Class
```java
abstract class Vehicle {
    public abstract void move();
    public void fuelType() { System.out.print("Gasoline "); }
}

class Car extends Vehicle {
    public void move() { System.out.print("Driving "); }
}

public class TestVehicle {
    public static void main(String[] args) {
        Vehicle v = new Car();
        v.move();
        v.fuelType();
    }
}
```
**Output**: `Driving Gasoline`

---

### Problem 10 — Multiple Interfaces
```java
interface Flyable { void fly(); }
interface Swimmable { void swim(); }

class Duck implements Flyable, Swimmable {
    public void fly() { System.out.print("Flying "); }
    public void swim() { System.out.print("Swimming "); }
}

public class TestDuck {
    public static void main(String[] args) {
        Duck d = new Duck();
        d.fly();
        d.swim();
    }
}
```
**Output**: `Flying Swimming`

---

## Set 5: GUI / Swing

### Problem 11 — Layout + Components
Which layout does this code use?
```java
JFrame f = new JFrame();
f.add(new JButton("North"), BorderLayout.NORTH);
f.add(new JButton("Center"), BorderLayout.CENTER);
f.setVisible(true);
```
**Answer**: BorderLayout (default for JFrame)

---

### Problem 12 — Event Handling
```java
class MyButton extends JButton {
    public MyButton(String text) { super(text); }
}

// Which method would you call on MyButton to handle clicks?
// A. addMouseListener()
// B. addActionListener()    ← correct
// C. addKeyListener()
// D. onClick()
```
**Answer**: B — JButton fires ActionEvent, handled by ActionListener

---

### Problem 13 — Null Layout
```java
JFrame f = new JFrame();
f.setLayout(null);
JButton b = new JButton("Click");
b.setBounds(20, 30, 100, 40);
f.add(b);
f.setSize(300, 200);
f.setVisible(true);
```
Where will the button appear?
- **Answer**: At coordinates (20, 30) with size 100×40 pixels

---

## Set 6: UML Interpretation

### Problem 14 — UML to Code
Given the UML:
```
┌─────────────────────┐
│      Person         │
├─────────────────────┤
│ - name: String      │
│ - age: int          │
├─────────────────────┤
│ + Person(s, i)      │
│ + getName(): String │
│ + setName(s)        │
│ + isAdult(): bool   │
└─────────────────────┘
```

Which are TRUE?
```java
A. Person p = new Person("John", 25);       // ✓
B. System.out.println(p.name);              // ✗ name is private
C. System.out.println(p.getName());         // ✓
D. p.setName("Jane");                       // ✓
E. p.isAdult();                             // ✓
```
**Answer**: A, C, D, E are valid

---

## Set 7: Advanced OOP — Aggregation, Composition, Coupling

### Problem 15 — Composition vs Aggregation
```java
class Engine { }
class Car {
    private Engine e = new Engine();  // Composition: Car creates Engine
}

class Professor { }
class Department {
    private List<Professor> profs;     // Aggregation: Profs exist independently
}
```
Which relationship has stronger lifetime dependency?
**Answer**: Composition (Car dies → Engine dies). Aggregation (Department closes → Profs still exist).

---

### Problem 16 — Constructor Chaining Deep
```java
class A {
    A() { System.out.print("A "); }
}
class B extends A {
    B() { System.out.print("B "); }
}
class C extends B {
    C() { System.out.print("C "); }
}
public class TestChain {
    public static void main(String[] args) {
        C c = new C();
    }
}
```
**Answer**: `A B C` — constructor chain goes A → B → C (super() is implicit first statement)

---

### Problem 17 — Object class override
```java
class Item {
    String name;
    Item(String n) { name = n; }
    // no toString() override
}
public class TestToString {
    public static void main(String[] args) {
        Item i = new Item("Book");
        System.out.println(i);
    }
}
```
**Answer**: Prints something like `Item@15db9742` (class name + hex hashcode) — Object's default toString()

---

### Problem 18 — equals() vs ==
```java
String s1 = new String("hello");
String s2 = new String("hello");
System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```
**Answer**: `false` (different references), `true` (same content)

---

### Problem 19 — Comparable interface
```java
class Num implements Comparable<Num> {
    int val;
    Num(int v) { val = v; }
    public int compareTo(Num o) { return this.val - o.val; }
}

public class TestComp {
    public static void main(String[] args) {
        Num a = new Num(10);
        Num b = new Num(5);
        System.out.println(a.compareTo(b));
    }
}
```
**Answer**: `5` (10 - 5 = positive, meaning a > b)

---

### Problem 20 — Singleton
```java
class Singleton {
    private static Singleton instance;
    private Singleton() { }
    public static Singleton getInstance() {
        if (instance == null) instance = new Singleton();
        return instance;
    }
}

// Client code
Singleton s1 = Singleton.getInstance();
Singleton s2 = Singleton.getInstance();
System.out.println(s1 == s2);
```
**Answer**: `true` — both references point to the same single instance

---

### Problem 21 — Anonymous Class
```java
interface Greeter { void greet(); }

public class TestAnon {
    public static void main(String[] args) {
        Greeter g = new Greeter() {
            public void greet() {
                System.out.println("Hello");
            }
        };
        g.greet();
    }
}
```
**Answer**: `Hello`

---

### Problem 22 — Lambda
```java
interface MathOp { int op(int a, int b); }

public class TestLambda {
    public static void main(String[] args) {
        MathOp add = (x, y) -> x + y;
        MathOp mul = (x, y) -> x * y;
        System.out.println(add.op(4, 5) + ", " + mul.op(4, 5));
    }
}
```
**Answer**: `9, 20`

---

### Problem 23 — Enum
```java
enum Color { RED, GREEN, BLUE }

public class TestEnum {
    public static void main(String[] args) {
        Color c = Color.RED;
        System.out.println(c.ordinal());
        System.out.println(c.name());
    }
}
```
**Answer**: `0`, `RED` (ordinal() returns position index starting from 0)

---

### Problem 24 — Generics
```java
class Pair<T> {
    T first, second;
    Pair(T f, T s) { first = f; second = s; }
    T getFirst() { return first; }
}

public class TestGen {
    public static void main(String[] args) {
        Pair<String> p = new Pair<>("A", "B");
        System.out.println(p.getFirst().toLowerCase());
    }
}
```
**Answer**: `a`

---

### Problem 25 — Shallow vs Deep Copy
```java
class Address { String city; Address(String c) { city = c; } }
class Person implements Cloneable {
    String name;
    Address addr;
    Person(String n, String c) { name = n; addr = new Address(c); }
    public Object clone() throws CloneNotSupportedException {
        return super.clone();  // SHALLOW copy
    }
}

Person p1 = new Person("Abebe", "AA");
Person p2 = (Person) p1.clone();
p2.addr.city = "Adama";
System.out.println(p1.addr.city);
```
**Answer**: `Adama` — shallow copy means p1 and p2 share the same Address object

---

### Problem 26 — Composition in UML
Given: `House` contains `Room` objects. If `House` is destroyed, `Room` objects are also destroyed. What is this relationship?

**Answer**: Composition (filled diamond ◆—). Strong ownership.

---

### Problem 27 — Coupling & Cohesion
A class `ReportGenerator` has methods for: fetching data, calculating stats, formatting HTML, sending email. What is true?
```java
A. High cohesion, loose coupling
B. Low cohesion, tight coupling
C. Low cohesion, loose coupling   ← correct
D. High cohesion, tight coupling
```
**Answer**: C — the class does too many unrelated things (low cohesion)

---

## Set 8: Design Pattern Identification

### Problem 28 — Pattern Matching
Identify the design pattern in each scenario:

a) `UndoManager` saves snapshots of document state so users can revert changes → _________
b) A logger writes messages to console, file, and network — each handler passes to the next → _________
c) A sorting utility that accepts different comparison algorithms at runtime → _________
d) A framework defines `prepare()` → `cook()` → `serve()` — subclasses implement each step → _________
e) A database connection pool provides a single global access point → _________
f) A GUI button notifies multiple panels when clicked → _________
g) Wrapping a `FileReader` with a `BufferedReader` to add buffering behavior → _________
h) Different UI controls (buttons, text fields) are treated the same way in a container → _________

**Solution:**
a) **Memento** — state save/restore for undo
b) **Chain of Responsibility** — each handler decides to process or pass along
c) **Strategy** — interchangeable algorithms
d) **Template Method** — skeleton filled by subclasses
e) **Singleton** — single global instance
f) **Observer** — subject notifies dependents
g) **Decorator** — dynamically adds behavior
h) **Composite** — individual and composite treated uniformly

---

### Problem 29 — Which Pattern?
```java
public class Logger {
    private static Logger instance;
    private Logger() {}
    public static Logger getInstance() {
        if (instance == null) instance = new Logger();
        return instance;
    }
    public void log(String msg) { System.out.println(msg); }
}
```
**Answer**: **Singleton** — private constructor, static getInstance()

---

### Problem 30 — Which Pattern?
```java
interface SortStrategy { int[] sort(int[] data); }
class BubbleSort implements SortStrategy { ... }
class QuickSort implements SortStrategy { ... }

class Sorter {
    private SortStrategy strategy;
    public void setStrategy(SortStrategy s) { this.strategy = s; }
    public int[] sort(int[] data) { return strategy.sort(data); }
}
```
**Answer**: **Strategy** — interchangeable algorithms via interface

---

### Problem 31 — Which Pattern?
```java
interface Iterator<T> {
    boolean hasNext();
    T next();
}
class ArrayIterator<T> implements Iterator<T> {
    private T[] items;
    private int pos = 0;
    public boolean hasNext() { return pos < items.length; }
    public T next() { return items[pos++]; }
}
```
**Answer**: **Iterator** — traverses collection without exposing internal structure

---

### Problem 32 — Which Pattern?
```java
class TextWriter {
    public void write(String text) { System.out.print(text); }
}
class BoldDecorator extends TextWriter {
    private TextWriter writer;
    BoldDecorator(TextWriter w) { this.writer = w; }
    public void write(String text) { System.out.print("<b>"); writer.write(text); System.out.print("</b>"); }
}
```
**Answer**: **Decorator** — wraps object to dynamically add behavior

---

### Problem 33 — Which Pattern?
```java
class ComputerFacade {
    private CPU cpu = new CPU();
    private Memory mem = new Memory();
    private HardDrive hd = new HardDrive();
    
    public void start() {
        cpu.freeze();
        mem.load(0, hd.read(0, 1024));
        cpu.execute();
    }
}
```
**Answer**: **Facade** — simplified interface to complex subsystem

---

### Problem 34 — Which Pattern?
```java
class TextEditor {
    private class Memento {
        String content;
        Memento(String c) { content = c; }
    }
    private String content;
    
    public Memento save() { return new Memento(content); }
    public void restore(Memento m) { content = m.content; }
    public void write(String s) { content = s; }
}
```
**Answer**: **Memento** — save/restore object state

---

### Problem 35 — Exam Multiple Choice
Which pattern is used when an object's behavior changes based on its internal state?
a) Strategy
b) State ✓
c) Observer
d) Command

**Answer**: **State** — different behavior per state (vending machine: hasMoney vs noMoney)

---

### Problem 36 — True or False
"Adapter pattern is used to provide a simplified interface to a complex subsystem."
**Answer**: **False** — that's Facade. Adapter makes incompatible interfaces work together.

---

## Common Exam Traps — OOP

| Trap | Example | Why |
|------|---------|-----|
| **Reference vs Object** | `Parent p = new Child()` | Reference type determines accessible methods |
| **Static context** | Calling instance method from `main` | Need object reference |
| **Constructor name case** | `employee()` vs `Employee()` | Must match class name exactly |
| **Default constructor lost** | Adding parameterized constructor removes default | Must define no-arg explicitly if needed |
| **Overriding vs overloading** | Same name, different params ≠ same params | Check parameter lists carefully |
| **Abstract instantiation** | `new Shape()` if Shape is abstract | Compiler error |
| **Interface instantiation** | `new Flyable()` | Interfaces cannot be instantiated |
| **super() position** | Any code before `super()` | Must be first statement in constructor |
| **Private inheritance** | `private` members are not inherited | Only public/protected accessible |
| **this() vs super()** | Both must be first statement | Can't use both in same constructor |
| **Shallow vs deep clone** | `super.clone()` for objects | Nested objects still shared |
| **Comparable return** | `a.compareTo(b)` returns `a.val - b.val` | Negative = a<b, Zero = equal, Positive = a>b |
| **Enum ordinal** | `Color.RED.ordinal()` = 0 | Starts from 0, depends on declaration order |
| **Generics erasure** | `List<String>` becomes `List` at runtime | No generic type info at runtime |
| **Lambda vs anonymous** | Lambda `this` refers to enclosing | Anonymous `this` refers to anonymous instance iteself |
