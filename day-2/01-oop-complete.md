# Day 2 — Object-Oriented Programming (98 Items) + GUI

## 1. OOP Principles

### The Four Pillars of OOP

| Principle | Description | Real-World Analogy |
|-----------|-------------|-------------------|
| **Encapsulation** | Bundling data + methods; hiding internal state | ATM — you interact via buttons, not internal mechanics |
| **Inheritance** | Child class inherits parent's properties/behaviors | Child inherits traits from parents |
| **Polymorphism** | Same interface, different implementations | "Play" means different things for Piano vs Guitar |
| **Abstraction** | Hide complexity, show only essentials | Driving a car — you use steering wheel, not engine internals |

---

## 2. Classes & Objects

### Class Definition (Java)
```java
public class Employee {
    // Attributes (fields) — usually private
    private String name;
    private String address;
    private String phone;
    private int yearOfBirth;
    
    // Constructor — same name as class, no return type
    public Employee(String name, String address, String phone, int yearOfBirth) {
        this.name = name;
        this.address = address;
        this.phone = phone;
        this.yearOfBirth = yearOfBirth;
    }
    
    // Methods — usually public
    public String getName() { return name; }
    public String getAddress() { return address; }
    public int getYearOfBirth() { return yearOfBirth; }
    public int calculateAge(int currentYear) {
        return currentYear - yearOfBirth;
    }
}
```

### Creating Objects
```java
Employee emp1 = new Employee("Patel", "Essex", "02085332455", 1970);
//         ↑ class   ↑ keyword  ↑ constructor call with arguments
```

**Common mistake** — wrong order or wrong types of arguments:
```java
// WRONG: phone is String, yearOfBirth is int
Employee emp1 = new Employee("Patel", "Essex", "02085332455", "1970");

// WRONG: missing 4th argument
Employee emp1 = new Employee("Patel", "Essex", "1970");

// WRONG: variable declaration syntax flipped
emp1 Employee = new Employee(...

// CORRECT
Employee emp1 = new Employee("Patel", "Essex", "02085332455", 1970);
```

### Object vs Class
- **Class**: blueprint / template (compile-time)
- **Object**: instance of a class (runtime, has its own memory)

### Object Class Methods (Every Class Inherits from Object)
| Method | Purpose |
|--------|---------|
| `toString()` | Returns string representation — override for meaningful output |
| `equals(Object o)` | Compares objects for content equality — override for custom logic |
| `hashCode()` | Returns integer hash — must be consistent with equals() |
| `getClass()` | Returns runtime class object |
| `clone()` | Creates object copy (must implement Cloneable) |
| `finalize()` | Called before garbage collection (deprecated) |

**Override example:**
```java
@Override
public String toString() {
    return "Employee[name=" + name + ", year=" + yearOfBirth + "]";
}

@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (!(o instanceof Employee)) return false;
    Employee e = (Employee) o;
    return this.name.equals(e.name) && this.yearOfBirth == e.yearOfBirth;
}
```

### Relationships: Association, Aggregation, Composition

| Type | Strength | Lifetime | UML Symbol | Example |
|------|----------|----------|------------|---------|
| **Association** | Weak | Independent | `—` | Teacher `—` Student |
| **Aggregation** | Medium | Independent | `◇—` | Department `◇—` Professor (dept removed, prof still exists) |
| **Composition** | Strong | Dependent | `◆—` | House `◆—` Room (house destroyed, rooms gone) |

```java
// Association (uses-a)
class Driver { void drive(Car c) { } }      // Driver uses Car temporarily

// Aggregation (has-a, weak)
class Department { List<Professor> profs; }  // Profs exist without Department

// Composition (has-a, strong)
class House { List<Room> rooms; }            // Rooms destroyed with House
```

### Coupling & Cohesion

| Concept | Low | High |
|---------|-----|------|
| **Cohesion** (how focused a class is) | Diffuse responsibilities | Single, clear purpose |
| **Coupling** (how dependent classes are) | Loose, independent | Tight, many dependencies |

**Goal**: High cohesion + Loose coupling
- High cohesion → methods in a class are strongly related
- Loose coupling → classes interact through well-defined interfaces

---

## 3. Constructors

### Constructor Rules
- Same name as class
- No return type (not even `void`)
- Called automatically when `new` is used
- Can be **overloaded** (multiple constructors with different params)
- If no constructor defined, Java provides **default constructor** (no-arg)

### Constructor Overloading
```java
public class SomeClass {
    private int one;
    private int two;
    
    // Constructor 1: no-arg
    public SomeClass() {
        one = 2;
        two = 4;
    }
    
    // Constructor 2: parameterized
    public SomeClass(int x, int y) {
        one = x;
        two = y;
    }
}
```

### this keyword
- Refers to current object's instance
- Used to distinguish instance vars from parameters: `this.name = name;`
- Can call another constructor: `this();` or `this(x, y);`

---

## 4. Access Modifiers

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| `public` | ✓ | ✓ | ✓ | ✓ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| `default` (none) | ✓ | ✓ | ✗ | ✗ |
| `private` | ✓ | ✗ | ✗ | ✗ |

**Exam tip**: If you want instance variables accessible from the class AND its subclasses → use `protected`.

---

## 5. Static vs Instance Members

| Feature | static | instance |
|---------|--------|----------|
| Belongs to | Class | Object |
| Accessed via | `ClassName.member` | `objectReference.member` |
| Shared? | Yes (one copy for all objects) | No (each object has own copy) |
| Can access instance vars? | No | Yes |
| `this` available? | No | Yes |

### Static Method Rules
```java
public class Hello {
    public static void main(String[] args) {
        // static method CANNOT directly access instance variables
        // static method CAN access other static members
    }
}
```

### Static Variable
- One copy shared across all instances
- Often used for constants: `public static final double PI = 3.14159;`

---

## 6. Inheritance

### Syntax
```java
class Child extends Parent {
    // inherits all public/protected members
    // can add new members
    // can override methods
}
```

### What is inherited?
- `public` and `protected` fields/methods
- **NOT inherited**: `private` members, constructors
- **Static methods** are inherited but **NOT overridden** (they can be hidden)

### Constructor Chaining Rule
```java
class GrandParent { GrandParent() { System.out.print("GP "); } }
class Parent extends GrandParent { Parent() { System.out.print("P "); } }
class Child extends Parent { Child() { System.out.print("C "); } }

new Child();  // Output: GP P C
```
Every constructor calls `super()` as its first statement (implicitly if not written).
Chain goes all the way up to Object class constructor.

### Preventing Inheritance
```java
final class CannotExtend { }     // cannot be subclassed
// final method: cannot be overridden
public final void doSomething() { }
```

### Method Overriding
- Child class redefines a parent method
- Same name, same parameters, same return type
- Use `@Override` annotation (optional but recommended)
- Overridden method is called based on **object type** at runtime

```java
class Animal {
    public void speak() {
        System.out.println("Animal speaks");
    }
}

class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("Dog barks");
    }
}

// Usage:
Animal a = new Dog();
a.speak();    // "Dog barks" — runtime polymorphism
```

### super keyword
- Refers to parent class
- `super.methodName()` — call parent's method
- `super()` — call parent's constructor (must be first statement)

---

## 7. Polymorphism

### Compile-Time Polymorphism (Method Overloading)
```java
class Calculator {
    int add(int a, int b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
    double add(double a, double b) { return a + b; }
}
```
- Same name, **different parameters** (number, type, or order)
- Resolved at compile time

### Runtime Polymorphism (Method Overriding)
- Same method signature, different implementation in subclass
- Resolved at runtime based on actual object type

### Overloading vs Overriding

| Feature | Overloading | Overriding |
|---------|-------------|------------|
| Parameters | Must differ | Must be identical |
| Return type | Can differ | Must be same (or covariant) |
| Class | Same class | Parent → child |
| Keyword | — | `@Override` |
| Binding | Compile-time | Runtime |
| Purpose | Convenience (same operation, different inputs) | Specialized behavior |

---

## 8. Abstract Classes vs Interfaces

### Abstract Class
```java
abstract class Shape {
    protected String color;
    
    // Concrete method
    public void setColor(String c) { color = c; }
    
    // Abstract method — no body
    public abstract double getArea();
}
```
- Cannot be **instantiated** (no `new Shape()`)
- Can have both abstract and concrete methods
- Can have constructors, fields

### Interface
```java
interface Drawable {
    void draw();  // implicitly public abstract
    default void print() { }  // default method (Java 8+)
    static void info() { }    // static method (Java 8+)
    private void helper() { } // private helper (Java 9+)
}
```
- All methods are implicitly `public abstract` (before Java 8)
- Cannot have instance variables (only `public static final` constants)
- A class can `implement` **multiple** interfaces
- Java 8+ allows `default` and `static` methods with body
- Java 9+ allows `private` methods in interfaces

### Functional Interface & Lambda (Java 8+)
```java
@FunctionalInterface
interface Calculator {
    int operate(int a, int b);    // exactly ONE abstract method
}

// Anonymous class (old way)
Calculator add = new Calculator() {
    public int operate(int a, int b) { return a + b; }
};

// Lambda (new way)
Calculator add = (a, b) -> a + b;
Calculator multiply = (a, b) -> a * b;

System.out.println(add.operate(5, 3));      // 8
System.out.println(multiply.operate(5, 3)); // 15
```

### Common Built-in Functional Interfaces
| Interface | Method | Signature |
|-----------|--------|-----------|
| `Predicate<T>` | `test()` | `T → boolean` |
| `Function<T,R>` | `apply()` | `T → R` |
| `Consumer<T>` | `accept()` | `T → void` |
| `Supplier<T>` | `get()` | `void → T` |

### Anonymous Classes
- A class without a name, defined and instantiated in one statement
- Used for event listeners, callbacks, and quick overrides

```java
// Anonymous class extending a class
Animal myDog = new Animal() {
    @Override
    public void speak() {
        System.out.println("Woof!");
    }
};

// Anonymous class implementing an interface
ActionListener listener = new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.out.println("Clicked!");
    }
};
button.addActionListener(listener);
```

### Inner Class Types

| Type | Definition | Has access to outer `this`? | Can have static members? |
|------|------------|----------------------------|--------------------------|
| **Member inner** | `class Inner` defined inside outer class | ✓ Yes | No |
| **Static nested** | `static class Nested` | ✗ No | ✓ Yes |
| **Local inner** | Defined inside a method block | ✓ Yes (if effectively final) | No |
| **Anonymous** | `new Interface() { }` on the fly | ✓ Yes | No |

```java
class Outer {
    private int x = 10;
    
    class Inner {                                   // member inner
        void show() { System.out.println(x); }      // can access private outer fields
    }
    
    static class Nested {                           // static nested
        void show() { /* cannot access x directly */ }
    }
    
    void method() {
        class Local { }                             // local inner class
    }
}

// Usage:
Outer o = new Outer();
Outer.Inner i = o.new Inner();                      // needs outer instance
Outer.Nested n = new Outer.Nested();                // static: no outer needed
```

### Lambda vs Anonymous Class
| Feature | Lambda | Anonymous Class |
|---------|--------|----------------|
| Use case | Only for functional interfaces | Can extend class or implement any interface |
| Syntax | `(args) -> expression` | `new Type() { ... }` |
| Instance variables | Not allowed | Allowed |
| `this` keyword | Refers to enclosing class | Refers to anonymous instance itself |
| Compilation | `invokedynamic` instruction | New class file generated |

### Enums in Java
```java
public enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}

Day today = Day.MONDAY;
if (today == Day.MONDAY) { }   // use == for enum comparison (safe)

// Enum with fields, constructor, and methods
public enum Status {
    PENDING(0), ACTIVE(1), INACTIVE(2);
    
    private final int code;
    Status(int code) { this.code = code; }
    public int getCode() { return code; }
}
// Status.ACTIVE.getCode() → 1
// Status.values() → array of all constants
// Status.valueOf("ACTIVE") → Status.ACTIVE
```

### Generics Basics
```java
// Generic class
class Box<T> {
    private T content;
    public void set(T content) { this.content = content; }
    public T get() { return content; }
}

Box<String> stringBox = new Box<>();     // T = String
Box<Integer> intBox = new Box<>();       // T = Integer
// Box<int> errorBox;                    // ERROR: primitive not allowed, use Integer

// Generic method
public static <T> T getMiddle(T... a) {
    return a[a.length / 2];
}
String mid = getMiddle("A", "B", "C");   // "B"

// Wildcards
List<?> list;                // unbounded: any type (read only)
List<? extends Number>;      // upper bounded: Number or subclasses (read safe)
List<? super Integer>;       // lower bounded: Integer or superclasses (write safe)

// Type erasure: generics are compile-time only; <T> becomes Object at runtime
```

### Comparable vs Comparator

| Feature | Comparable | Comparator |
|---------|------------|------------|
| Package | `java.lang` | `java.util` |
| Method | `compareTo(T o)` | `compare(T o1, T o2)` |
| Sorting type | Natural order | Custom order |
| Implementation | `class X implements Comparable<X>` | Lambda or separate class |
| Single/Multiple | Single natural sort | Many custom sorts possible |

```java
// Comparable — natural ordering
class Student implements Comparable<Student> {
    int id;
    String name;
    
    public int compareTo(Student other) {
        return Integer.compare(this.id, other.id);  // ascending by id
        // return this.id - other.id;  // simpler but risk of overflow
    }
}

// Comparator — custom ordering
Comparator<Student> byName = (a, b) -> a.name.compareTo(b.name);
Comparator<Student> byNameDesc = (a, b) -> b.name.compareTo(a.name);

Collections.sort(list);             // uses Comparable (natural order)
Collections.sort(list, byName);     // uses Comparator (custom order)
list.sort(byName);                  // List.sort() (Java 8+)
```

### Design Patterns — Singleton
```java
public class Singleton {
    private static Singleton instance;
    
    private Singleton() { }  // private constructor prevents external instantiation
    
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
// Usage: Singleton.getInstance() — same object every time
```

### Design Patterns — Factory
```java
interface Animal { void speak(); }
class Dog implements Animal { public void speak() { System.out.println("Bark"); } }
class Cat implements Animal { public void speak() { System.out.println("Meow"); } }

class AnimalFactory {
    public static Animal create(String type) {
        switch (type.toLowerCase()) {
            case "dog": return new Dog();
            case "cat": return new Cat();
            default: throw new IllegalArgumentException("Unknown: " + type);
        }
    }
}
// Animal a = AnimalFactory.create("dog");  // don't need to know Dog class
```

### Design Patterns (GoF — Gang of Four)

**Design patterns** = reusable solutions to common software design problems. The 23 GoF patterns fall into 3 categories:

#### Creational (5) — How objects are created

| Pattern | Purpose | Example |
|---------|---------|---------|
| **Singleton** | Ensures a class has **only one instance** globally | `Runtime.getRuntime()`, database connection pool |
| **Factory Method** | Creates objects **without specifying exact class** | `AnimalFactory.create("dog")` |
| **Abstract Factory** | Creates **families of related objects** | UI toolkits (Windows/Mac/Linux look) |
| **Builder** | Constructs complex objects **step-by-step** | `StringBuilder`, `StringBuffer` |
| **Prototype** | Creates objects by **cloning** an existing one | `clone()` method |

#### Structural (7) — How classes/objects are composed

| Pattern | Purpose | Example |
|---------|---------|---------|
| **Adapter** | Makes **incompatible interfaces work together** | Power plug adapter, `Arrays.asList()` |
| **Decorator** | Adds behavior to an object **dynamically** | `BufferedReader br = new BufferedReader(new FileReader(f))` |
| **Proxy** | Provides a **surrogate/placeholder** for another object | Lazy loading, access control, `java.lang.reflect.Proxy` |
| **Facade** | Provides a **simplified interface** to a complex subsystem | `JOptionPane.showMessageDialog()` |
| **Composite** | Treats individual objects and compositions **uniformly** | File system (files + folders both extend Entry) |
| **Bridge** | Separates **abstraction from implementation** | JDBC drivers (same API, different DB implementations) |
| **Flyweight** | Shares objects to support **large numbers efficiently** | String pool, character glyphs in text editors |

#### Behavioral (11) — How objects interact

| Pattern | Purpose | Example |
|---------|---------|---------|
| **Memento** | **Save/restore** object state to previous state | Ctrl+Z (undo), checkpoints |
| **Observer** | **Notify dependents** when subject state changes | Swing listeners, MVC, pub-sub |
| **Iterator** | **Traverse** a collection without exposing structure | `for (T item : collection)` |
| **Strategy** | **Encapsulates interchangeable algorithms** | Sorting algorithms, payment methods |
| **Command** | Encapsulates a **request as an object** | Menu actions, undo/redo queues |
| **Visitor** | **Adds new operations** without changing object classes | AST node processing, compilers |
| **State** | Changes **behavior when internal state changes** | Vending machine, TCP connection states |
| **Template Method** | Defines algorithm **skeleton**, subclasses fill steps | `AbstractList.indexedBinarySearch()` |
| **Chain of Resp.** | Passes request along a **chain of handlers** | Loggers (INFO → WARN → ERROR), event bubbling |
| **Mediator** | **Centralizes communication** between objects | Chat room, air traffic control |
| **Interpreter** | Defines **grammar** and interprets sentences | Regex engines, language parsers |

#### Common Exam Traps

| Question | Wrong answer (trap) | Correct answer |
|----------|---------------------|----------------|
| Restore object to previous state | Iterator, Observer | **Memento** |
| Only one instance | Factory, Builder | **Singleton** |
| Incompatible interfaces | Facade, Bridge | **Adapter** |
| Interchangeable algorithms | Command, State | **Strategy** |
| Add behavior dynamically | Proxy, Adapter | **Decorator** |
| Family of related objects | Factory Method, Builder | **Abstract Factory** |
| Simplified interface to subsystem | Adapter, Proxy | **Facade** |
| Notify on state change | Memento, State | **Observer** |

### Serialization
```java
import java.io.*;

class Person implements Serializable {
    private static final long serialVersionUID = 1L;  // version control
    String name;
    transient int age;  // transient fields are NOT serialized
    
    // After deserialization, transient fields get default values (0, null)
}

// Serialize (write)
ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("person.ser"));
oos.writeObject(person);
oos.close();

// Deserialize (read)
ObjectInputStream ois = new ObjectInputStream(new FileInputStream("person.ser"));
Person p = (Person) ois.readObject();
ois.close();
```

### Object Cloning (Cloneable)
```java
class Address { String city; Address(String c) { city = c; } }

class Person implements Cloneable {
    String name;
    Address address;
    
    // Shallow clone — primitives copied, objects share reference
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
    
    // Deep clone — everything including nested objects is copied
    public Person deepClone() {
        Person p = new Person();
        p.name = this.name;
        p.address = new Address(this.address.city);  // new Address object
        return p;
    }
}
```
- **Shallow copy**: `super.clone()` — fields copied, but object references point to same objects
- **Deep copy**: manually copy all nested mutable objects too

### Abstract Class vs Interface

| Feature | Abstract Class | Interface |
|---------|---------------|-----------|
| Instantiation | ❌ | ❌ |
| Abstract methods | ✓ | ✓ |
| Concrete methods | ✓ | default/static methods only |
| Fields | Any type | `public static final` only |
| Constructors | ✓ | ❌ |
| Multiple inheritance | ❌ (single extends) | ✓ (multiple implements) |
| `extends` / `implements` | `extends` | `implements` |

---

## 9. UML Class Diagrams

### Notation
```
┌───────────────┐
│   ClassName   │  ← Class name (bold, centered)
├───────────────┤
│ - attribute   │  ← Attributes (- private, + public, # protected)
│ + method()    │  ← Methods (return type after colon)
└───────────────┘
```

### Relationships
| Symbol | Meaning |
|--------|---------|
| `▷—` | Inheritance (extends) |
| `- - ▷` | Interface implementation |
| `—` | Association |
| `◇—` | Aggregation (has-a, weak) |
| `◆—` | Composition (has-a, strong) |
| `0..*` | Multiplicity |

### Exam Example
```
┌────────────────────────────────────┐
│            Employee                │
├────────────────────────────────────┤
│ - name: String                     │
│ - address: String                  │
│ - phone: String                    │
│ - yearOfBirth: int                 │
├────────────────────────────────────┤
│ + Employee(name, addr, phone, yob) │
│ + getName(): String                │
│ + getAddress(): String             │
│ + calculateAge(int): int           │
└────────────────────────────────────┘
```

**Common exam question**: Given the UML, which method call is valid?
```java
// Assuming emp1 is an Employee object:
emp1.getAddress();    // ✓ correct
emp1.Address;         // ✗ attribute is private
emp1.getAddress;      // ✗ missing parentheses
getAddress();         // ✗ not a standalone function
```

---

## 10. GUI Development (Swing)

### AWT vs Swing

| AWT | Swing |
|-----|-------|
| Platform-dependent | Platform-independent |
| Heavyweight | Lightweight |
| Looks different on each OS | Consistent look-and-feel |
| `java.awt` package | `javax.swing` package |
| Older | Newer (since Java 2) |

### Hierarchy of Swing Classes
```
Object
  └── Component
        ├── Container
        │     ├── Window
        │     │     ├── Frame → JFrame
        │     │     └── Dialog → JDialog
        │     └── Panel → JPanel
        └── JComponent
              ├── JLabel
              ├── JButton
              ├── JTextField
              ├── JTextArea
              ├── JList
              ├── JComboBox
              ├── JSlider
              ├── JTable
              ├── JMenu
              └── AbstractButton
                    └── JMenuItem, JCheckBox, JRadioButton
```

### JFrame (Top-Level Container)
```java
import javax.swing.*;

public class Simple {
    public static void main(String[] args) {
        JFrame f = new JFrame("EmptyFrame");
        f.setSize(300, 200);
        f.setTitle("First JFrame");
        f.setLocationRelativeTo(null);  // center on screen
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setVisible(true);
    }
}
```

### JFrame Constants for close operation
| Constant | Behavior |
|----------|----------|
| `JFrame.EXIT_ON_CLOSE` | Exit application |
| `JFrame.HIDE_ON_CLOSE` | Hide frame, app keeps running |
| `JFrame.DO_NOTHING_ON_CLOSE` | Ignore close click |

### Common Swing Components

**JLabel** — display text/image (non-editable)
```java
JLabel l1 = new JLabel("First Label.");
l1.setBounds(50, 50, 100, 30);  // x, y, width, height
f.add(l1);
```

**JButton** — clickable action
```java
JButton b = new JButton("Click Here");
b.setBounds(50, 100, 95, 30);
f.add(b);
```

**JTextField** — single-line input
```java
JTextField t1 = new JTextField("Default text");
t1.setBounds(50, 100, 200, 30);
f.add(t1);
```

**JTextArea** — multi-line text
```java
JTextArea a = new JTextArea("Welcome to IT Class");
a.setBounds(10, 30, 200, 200);
f.add(a);
```

### Container Types

| Container | Type | Default Layout | Has Title Bar? |
|-----------|------|----------------|----------------|
| JFrame | Top-level | BorderLayout | Yes |
| JDialog | Top-level | BorderLayout | Yes |
| JPanel | Lightweight | FlowLayout | No |

---

## 11. Layout Managers

### BorderLayout (default for JFrame)
Places components in 5 areas:
```java
f.add(component, BorderLayout.NORTH);
f.add(component, BorderLayout.SOUTH);
f.add(component, BorderLayout.EAST);
f.add(component, BorderLayout.WEST);
f.add(component, BorderLayout.CENTER);  // takes remaining space
```

### FlowLayout (default for JPanel)
- Components placed left-to-right in a row
- Wraps to next row when no space

### GridLayout
- Divides container into equal-sized cells
```java
f.setLayout(new GridLayout(rows, cols));
```

### Setting Layout
```java
f.setLayout(new FlowLayout());
// or with null for absolute positioning:
f.setLayout(null);
// then use setBounds() for each component
```

---

## 12. Event Handling (Delegation Model)

### Three Components
1. **Event Source** — generates the event (e.g., button)
2. **Event Object** — carries event info (e.g., ActionEvent)
3. **Event Listener** — receives and processes event

### Steps
```java
// 1. Register listener with source
button.addActionListener(listenerObject);

// 2. Create listener class implementing the interface
class MyListener implements ActionListener {
    public void actionPerformed(ActionEvent e) {
        // handle the event
        System.out.println("Button clicked!");
    }
}
```

### Common Event Types & Listeners

| Event Class | Listener Interface | Method |
|-------------|-------------------|--------|
| ActionEvent | ActionListener | `actionPerformed()` |
| MouseEvent | MouseListener | `mouseClicked()`, `mousePressed()`, etc. |
| KeyEvent | KeyListener | `keyPressed()`, `keyReleased()` |
| TextEvent | TextListener | `textValueChanged()` |

---

## 13. Java Packages (java.*)

| Package | Purpose |
|---------|---------|
| `java.awt` | AWT components, layouts, colors |
| `java.awt.event` | Event classes and listener interfaces |
| `javax.swing` | Swing components (JFrame, JButton, etc.) |

---

## Exam-Style Practice Questions

### Q1: OOP Principles
Which OOP principle allows the creation of several methods with the same name but different parameters?

**Answer**: Polymorphism (specifically method overloading, which is compile-time polymorphism)

---

### Q2: Constructor Overloading
```java
class SomeClass {
    private int one;
    private int two;
    
    public SomeClass() { one = 2; two = 4; }
    public SomeClass(int x, int y) { one = x; two = y; }
    public void setOne(int x) { one = x; }
    public void setTwo(int x) { two = x; }
    public void equalize() { one = two; }
    public int calcSum() { return one + two; }
    public int calcDiff() { return two - one; }
}

// What does this print?
SomeClass myClass = new SomeClass();
myClass.equalize();
System.out.print(myClass.calcSum());
```
**Trace**:
- `SomeClass()` → one=2, two=4
- `equalize()` → one becomes 4
- `calcSum()` → 4+4 = **8**

Wait — the constructor sets `one = 2, two = 4`, then `equalize()` sets `one = two` so `one = 4`. Sum = 8.

**Answer**: 8

---

### Q3: Constructor Overloading — No Default Constructor Match
```java
SomeClass myClass = new SomeClass(3);
myClass.setTwo(1);
System.out.print(myClass.calcDiff());
```
**Trace**:
- `new SomeClass(3)` — there is no single-parameter constructor! Compilation fails.

**Answer**: The program will **not compile**

---

### Q4: UML Class — Object Creation
Given the Employee class from the notes, which would **NOT** cause a compiler error?

```java
A. Employee emp1 = new Employee("845","5034","0101",0);      // ✓ all String + int
B. Employee emp1 = new Employee("Patel","Essex","02085332455","1970");  // ✗ "1970" is String, not int
C. Employee emp1 = new Employee("Patel","Essex","1970");     // ✗ missing 4th arg
D. emp1 Employee = new Employee(...);                         // ✗ syntax flipped
E. Employee emp1 = new Employee("Patel",Essex,02085332455,1970);  // ✗ Essex needs quotes
```
**Answer**: A

---

### Q5: Displaying attribute via getter
Assuming emp1 is created, which displays the address?
```java
A. System.out.print(address);                // ✗ no such variable in scope
B. System.out.print(emp1.Address);           // ✗ private attribute, wrong case
C. System.out.print(emp1.getAddress());      // ✓ correct
D. System.out.print(emp1.getAddress);        // ✗ missing parentheses
E. System.out.print(getAddress());           // ✗ not a standalone function
```
**Answer**: C

---

### Q6: Inheritance
```java
class Pet {
    public void speak() { System.out.println("Pet sound"); }
}
class Dog extends Pet {
    public void speak() { System.out.println("Bark"); }
    public void fetch() { System.out.println("Fetching"); }
}

Pet p = new Dog();
p.speak();
p.fetch();     // what happens?
```
**Answer**: `p.speak()` prints "Bark" (runtime polymorphism / dynamic binding).  
`p.fetch()` gives **compiler error** — reference type is Pet, which doesn't have `fetch()`.

---

### Q7: Access Modifiers
Which modifier allows access from the same class AND subclasses only?

**Answer**: `protected`

---

### Q8: Abstract Class
Which is true about abstract classes?
```java
A. cannot be inherited
B. a mechanism of encapsulation
C. cannot be instantiated        ← correct
D. can contain both abstract and non-abstract methods  ← also correct
```
**Answer**: C and D are both true. If only one choice → C (cannot be instantiated) is the defining property.

---

### Q9: Interface
Which is wrong about interfaces?
```java
A. Like a class, an interface is reference data type.
B. Interface abstract methods are accessed using interface instances.    ← wrong
C. Interface includes abstract methods.
D. One class can implement multiple interfaces.
```
**Answer**: B — interfaces cannot be instantiated directly

---

### Q10: Static Context
```java
public class Hello {
    public static void main(String[] args) {
        System.out.print("Hello ");
        System.out.print("world")
    }
}
```
What's wrong?  
**Answer**: Missing semicolon after `System.out.print("world")` — syntax error. Also `Static` should be `static` (lowercase). So there are **multiple syntax errors**.

---

### Q11: Swing Components
Which container doesn't contain title bar or menu bar but can hold components?
```java
A. Window
B. Frame
C. Panel       ← correct (JPanel)
D. Container
```

---

### Q12: Layout Managers
What is the default layout manager for JFrame?

**Answer**: BorderLayout

What is the default layout manager for JPanel?

**Answer**: FlowLayout

---

### Q13: Event Handling
Which package provides event classes and Listener interfaces?

**Answer**: `java.awt.event`

---

### Q14: GUI Code Understanding
```java
JFrame f = new JFrame("My App");
f.setSize(400, 300);
f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
f.setLayout(new FlowLayout());
f.add(new JButton("Click"));
f.setVisible(true);
```
Which layout is used? **FlowLayout**  
What happens on close? **Application exits**

---

### Q15: OOP Design Scenario
A pet family has common behavior (name), but Dog can fetch while both Dog and Cat can speak. Which OOP principle is suitable?

**Answer**: **Inheritance** — common behavior in Pet parent class, specialized behavior in Dog/Cat subclasses

---

### Q16: Static Members
What is the output?
```java
class Counter {
    static int count = 0;
    Counter() { count++; }
}
public class Test {
    public static void main(String[] args) {
        new Counter();
        new Counter();
        new Counter();
        System.out.println(Counter.count);
    }
}
```
**Answer**: 3 (static `count` is shared, increments with each `new`)

---

### Q17: Method Overriding vs Overloading
Method overriding is a characteristic of which OOP principle?

**Answer**: Polymorphism (runtime polymorphism)

---

### Q18: GUI
What is the first callback method invoked during activity lifecycle?

**Answer**: `onCreate()`

---

## Quick Reference Card

```
OOP FOUR PILLARS
────────────────
Encapsulation — hide data, expose methods (private fields, public getters/setters)
Inheritance   — class extends another class (IS-A relationship)
Polymorphism  — same interface, different behavior (overloading + overriding)
Abstraction   — hide complexity (abstract classes, interfaces)

ACCESS MODIFIERS
────────────────
public    → everywhere
protected → package + subclasses
default   → package only
private   → class only

KEYWORDS
────────
this      → current object
super     → parent class
static    → class-level member
final     → cannot change (variable/class/method)
abstract  → must be overridden/implemented
extends   → inheritance (class)
implements → interface implementation

SWING
─────
JFrame     → top-level window (BorderLayout)
JPanel     → lightweight container (FlowLayout)
JButton    → clickable button
JLabel     → text/image display
JTextField → single-line input
JTextArea  → multi-line input
setBounds(x, y, w, h) → absolute positioning
setLayout(null) → manual layout
add(component) → add to container
```


## Practice Questions (from Question Bank)

### Q254. Child class redefining parent method is called:?

- A) Encapsulation
- B) Abstraction
- C) Overriding
- D) Overloading
  **Answer: C**

### Q255. In a resource-constrained environment, abstract class vs Interface in Java:?

- A) No difference
- B) Interface can be instantiated
- C) Abstract supports multiple
- D) Abstract can have concrete methods
  **Answer: D**

### Q256. Private access modifier makes field accessible:?

- A) Package only
- B) Everywhere
- C) Subclasses only
- D) Within its own class only
  **Answer: D**

### Q257. 'finally' block guarantees:?

- A) Always runs
- B) Runs only if exception thrown
- C) Runs only if no exception
- D) Runs before try block
  **Answer: A**

### Q258. When designing for high performance, how is Single responsibility principle best characterized?

- A) One method per class
- B) Class has only one reason to change
- C) One inheritance level
- D) One class per file
  **Answer: B**

### Q259. How is Filled diamond in uml best characterized?

- A) Simple association
- B) Composition: child cannot exist
- C) Child exists without parent
- D) Interface implementation
  **Answer: B**

### Q260. Compile-time polymorphism is achieved by:?

- A) Dynamic dispatch
- B) Method overriding
- C) Method overloading
- D) Late binding
  **Answer: C**

### Q261. In a resource-constrained environment, java keyword to call parent constructor:?

- A) base
- B) this
- C) super
- D) parent
  **Answer: C**

### Q262. Singleton pattern ensures:?

- A) Thread-safe instances always
- B) No instances
- C) One instance only
- D) Multiple instances
  **Answer: C**

### Q263. ArrayIndexOutOfBoundsException is thrown when:?

- A) Array is null
- B) Index is out of valid range
- C) Array type mismatch
- D) Array is too large
  **Answer: B**

### Q264. Consider a system where mVC Controller is responsible for:?

- A) Storing data
- B) Displaying UI
- C) Database queries
- D) Handling input and
  **Answer: D**

### Q265. Encapsulation primarily protects:?

- A) Method overloading
- B) Data integrity by
- C) Inheritance chain
- D) Object instantiation
  **Answer: B**

### Q266. @Override annotation in Java indicates:?

- A) Method is overloaded
- B) Method is abstract
- C) Method overrides a parent
- D) Method is static
  **Answer: C**

### Q267. When designing for high performance, open/Closed Principle states classes should be:?

- A) Open to modification, closed to extension
- B) Both open to modification and extension
- C) Open to extension, closed to modification
- D) Closed to both
  **Answer: A**

### Q268. Which of the following best describes n abstract method?

- A) Method with empty body {}
- B) Static method
- C) Private method
- D) Method declared without
  **Answer: D**

### Q269. Which OOP concept hides implementation details?

- A) Polymorphism
- B) Encapsulation
- C) Inheritance
- D) Abstraction
  **Answer: B**

### Q270. In a resource-constrained environment, a class cannot be instantiated if it is:?

- A) Public
- B) Abstract
- C) Static
- D) Final and public
  **Answer: B**

### Q271. Multiple inheritance in Java is achieved through:?

- A) Implementing multiple interfaces
- B) Extending multiple classes
- C) Using 'super' multiple times
- D) Abstract classes
  **Answer: A**

### Q272. Identify the correct statement about n object.

- A) Static variable
- B) Instance of a class
- C) Blueprint of a class
- D) Abstract method
  **Answer: B**

### Q273. Consider a system where constructor has which characteristics?

- A) Must be public
- B) Same name as class, no return type
- C) Has return type void
- D) Can be abstract
  **Answer: B**

### Q274. Which of the following best describes destructor used for?

- A) Free resources when
- B) Implement interfaces
- C) Create objects
- D) Override methods
  **Answer: A**

### Q275. 'protected' access modifier allows access to:?

- A) Different packages only
- B) Same class only
- C) Same package and subclasses
- D) Any class
  **Answer: C**

### Q276. In a resource-constrained environment, liskov Substitution Principle states:?

- A) Classes should be closed to extension
- B) Subclass can replace parent without
- C) Interfaces should be small
- D) Dependencies should be injected
  **Answer: B**

### Q277. Interface Segregation Principle states:?

- A) Use one large interface
- B) Clients should not depend on
- C) Interfaces cannot have methods
- D) Interfaces must be public
  **Answer: B**

### Q278. Dependency Inversion Principle states:?

- A) High-level modules depend on low-level
- B) Depend on abstractions not concretions
- C) Classes depend on all other classes
- D) Inject dependencies at compile time
  **Answer: B**

### Q279. When designing for high performance, factory pattern belongs to which category?

- A) Architectural
- B) Structural
- C) Creational
- D) Behavioural
  **Answer: C**

### Q280. Observer pattern belongs to which category?

- A) Creational
- B) Architectural
- C) Behavioural
- D) Structural
  **Answer: C**

### Q281. Decorator pattern belongs to which category?

- A) Structural
- B) Concurrency
- C) Behavioural
- D) Creational
  **Answer: A**

### Q282. Identify the correct statement about difference between aggregation and composition.

- A) Aggregation uses interfaces
- B) No difference
- C) Composition: child can exist
- D) Aggregation: child can exist
  **Answer: D**

### Q283. Which exception type does NOT need to be caught or declared (unchecked)?

- A) RuntimeException
- B) ClassNotFoundException
- C) IOException
- D) SQLException
  **Answer: A**

### Q284. What does 'this' keyword refer to in Java/C++?

- A) Next object to be created
- B) Current object instance
- C) Parent class
- D) Static context
  **Answer: B**

### Q285. Which of the following best describes polymorphism literally meaning?

- A) Many classes
- B) Many parents
- C) Many methods
- D) Many forms/shapes — one
  **Answer: D**

### Q286. Dynamic/runtime polymorphism is achieved through:?

- A) Interface default methods
- B) Method overloading
- C) Method overriding with
- D) Static methods
  **Answer: C**

### Q287. Which design pattern separates object construction from representation?

- A) Factory
- B) Singleton
- C) Builder
- D) Prototype
  **Answer: C**

### Q288. Consider a system where uML 'is-a' relationship is represented by:?

- A) Composition
- B) Inheritance/Generalization
- C) Association
- D) Aggregation
  **Answer: B**

### Q289. UML 'has-a' relationship (loosely) is:?

- A) Aggregation
- B) Realization
- C) Inheritance
- D) Dependency
  **Answer: A**

### Q290. Which of the following best describes late binding?

- A) Binding at compile time
- B) Method call resolved at
- C) Binding in constructor
- D) Binding in static initializer
  **Answer: B**

### Q291. Which keyword prevents a class from being subclassed in Java?

- A) static
- B) final
- C) abstract
- D) sealed
  **Answer: B**

### Q292. Identify the correct statement about checked exception in Java.

- A) Exception must be caught
- B) Exception compiler doesn't check
- C) Exception from null pointers
- D) Exception only in runtime
  **Answer: A**

### Q293. Which of the following best describes DRY principle?

- A) Delete Redundant Years
- B) Data Retrieval Yields
- C) Don't Repeat Yourself —
- D) Dynamic Runtime Yield
  **Answer: C**

### Q294. Which description of n interface in Java primarily used for is accurate?

- A) Creating objects
- B) Defining a contract that
- C) Storing data
- D) Replacing abstract
  **Answer: B**

### Q295. Static methods in a class:?

- A) Belong to the class not instances
- B) Are always abstract
- C) Can access instance variables
- D) Must be private
  **Answer: A**

### Q296. Identify the correct statement about n inner class.

- A) Abstract class
- B) Class with private constructor
- C) Class defined within another class
- D) Class with no methods
  **Answer: C**

### Q297. Which exception is thrown when calling method on null reference?

- A) ArrayIndexOutOfBoundsException
- B) ClassCastException
- C) NullPointerException
- D) StackOverflowError
  **Answer: C**

### Q298. Which description of method chaining is accurate?

- A) Calling overloaded methods
- B) Calling methods sequentially
- C) Overriding multiple methods
- D) Inheriting methods
  **Answer: B**

### Q299. Which pattern notifies multiple objects when state changes?

- A) Command
- B) Factory
- C) Observer
- D) Singleton
  **Answer: C**

### Q300. In a resource-constrained environment, facade pattern purpose:?

- A) Converts interface to another
- B) Controls single instance
- C) Provides simplified interface to
- D) Adds functionality to objects
  **Answer: C**

### Q301. Adapter pattern purpose:?

- A) Converts incompatible
- B) Builds complex objects step by
- C) Creates object families
- D) Clones objects
  **Answer: D**

### Q302. Which description of constructor overload is accurate?

- A) Constructor calling another class
- B) Two constructors with same parameters
- C) Constructor that returns value
- D) Multiple constructors with different
  **Answer: D**

### Q303. In a resource-constrained environment, which description of copy constructor is accurate?

- A) Constructor that creates new object
- B) Default constructor
- C) Constructor that copies parent class
- D) Constructor with no parameters
  **Answer: A**

### Q304. Which description of purpose of a getter method is accurate?

- A) Validates input data
- B) Deletes object
- C) Returns private field value
- D) Sets private field value
  **Answer: C**

### Q305. Which of the following best describes encapsulation's relationship to getters/setters?

- A) Fields are private
- B) Getters/setters are not related
- C) Only one of the two is needed
- D) Setters must be public
  **Answer: A**

### Q306. Which principle says 'program to an interface, not an implementation'?

- A) Liskov Substitution
- B) Open/Closed
- C) Dependency Inversion
- D) Single Responsibility
  **Answer: A**

### Q307. Which description of static variable in OOP is accurate?

- A) Variable only in static methods
- B) Variable that cannot change
- C) Variable shared across all instances of a class
- D) Variable initialized at runtime
  **Answer: D**

### Q308. Template Method pattern:?

- A) Creates objects without specifying class
- B) Wraps objects to add behavior
- C) Manages single instance
- D) Defines skeleton algorithm in base class
  **Answer: C**

### Q309. When designing for high performance, strategy pattern allows:?

- A) Logging all method calls
- B) Selecting algorithm at runtime
- C) Creating object hierarchies
- D) Single algorithm fixed at compile time
  **Answer: A**

### Q310. Command pattern encapsulates:?

- A) Object creation logic
- B) Database queries
- C) Requests as objects
- D) UI rendering
  **Answer: B**

### Q311. Which of the following best describes object composition over inheritance?

- A) Avoid using objects
- B) Always use inheritance
- C) Build complex behavior by
- D) Use abstract classes only
  **Answer: A**

### Q312. Consider a system where in Java, all classes implicitly extend:?

- A) AbstractClass
- B) Object class
- C) Class class
- D) Nothing
  **Answer: C**

### Q313. Which of the following best describes purpose of toString() method in Java?

- A) Compares two objects
- B) Returns string representatio
- C) Converts object to integer
- D) Clones an object
  **Answer: D**

### Q314. Which description of equals() method used for in Java is accurate?

- A) Converts to boolean
- B) Compares memory addresses only
- C) Checks logical equality of objects
- D) Assigns values
  **Answer: A**

### Q315. Which description of difference between == and .equals() in Java is accurate?

- A) No difference
- B) == compares references
- C) Both compare content
- D) .equals compares references
  **Answer: B**

### Q316. Which description of multilevel inheritance is accurate?

- A) Interface extends interface
- B) Class inherits from multiple classes
- C) Class implements multiple interfaces
- D) Chain: A extends B extends C
  **Answer: C**

### Q317. Identify the correct statement about hierarchical inheritance.

- A) Abstract class chain
- B) One child, multiple parents
- C) Interface hierarchy
- D) One parent, multiple child classes
  **Answer: A**

### Q318. When designing for high performance, prototype pattern purpose:?

- A) Creates new objects by cloning
- B) Adds behavior to objects
- C) Defines family of algorithms
- D) Ensures single instance
  **Answer: B**

### Q319. Which description of n access specifier is accurate?

- A) Variable type declaration
- B) Keyword controlling
- C) Method return type
- D) Loop control keyword
  **Answer: D**

### Q320. Which OOP feature allows same method name to behave differently in different classes?

- A) Polymorphism
- B) Encapsulation
- C) Inheritance
- D) Abstraction
  **Answer: A**

### Q321. Which of the following best describes virtual function in C++?

- A) Private abstract function
- B) Function with no body
- C) Function in base class
- D) Function that is never called
  **Answer: B**

### Q322. What does 'new' return in Java?

- A) Null always
- B) Primitive value
- C) Reference to newly
- D) Object on stack
  **Answer: C**

### Q323. Which description of garbage collection is accurate?

- A) Manual memory freeing
- B) Clearing arrays
- C) Automatic reclamation of
- D) Deleting variables
  **Answer: A**

### Q324. Identify the correct statement about purpose of an interface's default method (Java 8+).

- A) Provide default implementation
- B) Force overriding
- C) Replace abstract methods
- D) Enable multiple inheritance of
  **Answer: D**

### Q325. Identify the correct statement about coupling in OOP.

- A) Depth of inheritance tree
- B) Number of methods in a class
- C) Degree to which classes depend on each other
- D) Degree to which a class is self-contained
  **Answer: A**

### Q326. Identify the correct statement about cohesion in OOP.

- A) Depth of inheritance
- B) Degree to which elements within a
- C) Number of parameters per method
- D) How classes depend on each other
  **Answer: B**

### Q327. Consider a system where high cohesion and low coupling is considered:?

- A) Good design principle
- B) Only relevant for databases
- C) Bad design
- D) Only for procedural
  **Answer: C**

### Q328. Identify the correct statement about n anonymous class in Java.

- A) Static inner class
- B) Class defined and instantiated at
- C) Abstract class with no methods
- D) Class with private constructor
  **Answer: A**

### Q329. Which description of lambda expression in Java is accurate?

- A) Loop construct
- B) Short anonymous function
- C) Abstract class shorthand
- D) Recursive function
  **Answer: B**

### Q330. In a resource-constrained environment, iterator pattern provides:?

- A) Undo/redo functionality
- B) Simplified subsystem interface
- C) Single object creation
- D) Way to sequentially access
  **Answer: C**

### Q331. Composite pattern is used to:?

- A) Control object creation
- B) Convert interfaces
- C) Add functionality to objects
- D) Treat individual objects and
  **Answer: A**

### Q332. Which description of n enumeration (enum) in Java is accurate?

- A) Abstract class variant
- B) Type with fixed set of named
- C) Array of objects
- D) Generic type parameter
  **Answer: B**

### Q333. Which of the following best describes purpose of the 'interface' keyword in OOP languages?

- A) Defines contract of methods a
- B) Declares constants only
- C) Extends class hierarchy
- D) Creates concrete classes
  **Answer: C**

### Q334. Bridge pattern separates:?

- A) Model from view
- B) Data from behavior
- C) Input from output
- D) Abstraction from
  **Answer: A**

### Q335. Proxy pattern provides:?

- A) Object composition
- B) Notification mechanism
- C) Alternative algorithm
- D) Placeholder controlling
  **Answer: B**

### Q336. Which of the following best describes difference between a class and an object?

- A) Classes are runtime
- B) Object is blueprint
- C) No difference
- D) Class is blueprint/template
  **Answer: C**

### Q337. Which of the following best describes role of 'super' keyword in inheritance?

- A) References static context
- B) References current object
- C) Creates new object
- D) References parent class constructor
  **Answer: A**

### Q338. Which description of method hiding in Java is accurate?

- A) Using @Override annotation
- B) Making methods private
- C) Static method in subclass hides
- D) Overriding instance methods
  **Answer: B**

### Q339. What does it mean for a method to be 'overridden' correctly?

- A) Different name, same parameters
- B) Same name and parameters in subclass
- C) Private method in subclass
- D) Same name, different parameters
  **Answer: A**

### Q340. Can an abstract class have a constructor?

- A) Only default constructor
- B) Yes, called by subclass
- C) No, never
- D) Only if no abstract methods
  **Answer: A**

### Q341. Which of the following best describes difference between an interface and an abstract class?

- A) Abstract class can have
- B) Abstract class cannot be
- C) Both are identical
- D) Interface can have state
  **Answer: C**

### Q342. When designing for high performance, sOLID is an acronym for which 5 principles?

- A) Single, Overriding, Layered, Integration, Deployment
- B) Single, Open, Liskov, Interface, Dependency
- C) Simple, Open, Large, Inherited, Dynamic
- D) Stable, Object, Linked, Interface, Design
  **Answer: A**

### Q343. What does 'is-a' relationship mean in OOP?

- A) Has a field of another type
- B) Object holds reference to another
- C) Inheritance relationship: subclass
- D) Interface implementation
  **Answer: B**

### Q344. What does 'has-a' relationship mean?

- A) Method overriding
- B) Interface implementation
- C) Inheritance
- D) Composition/Aggregation:
  **Answer: C**

### Q345. What exception is thrown when casting object to incompatible type?

- A) ArrayIndexOutOfBoundsException
- B) ClassCastException
- C) IllegalArgumentException
- D) NullPointerException
  **Answer: B**

### Q346. Identify the correct statement about purpose of 'instanceof' operator in Java.

- A) Returns class of object
- B) Checks if object is instance
- C) Creates new instance
- D) Compares two instances
  **Answer: B**

### Q347. Can interfaces have fields/variables in Java?

- A) Yes, but implicitly public
- B) Yes, any type of field
- C) No fields allowed
- D) Only private fields
  **Answer: C**

### Q348. Identify the correct statement about chain of responsibility pattern.

- A) Method call chain
- B) Sequence of objects where
- C) Chain of inheritance
- D) Loop through handlers
  **Answer: C**

### Q349. Identify the correct statement about State pattern.

- A) Freezes object state
- B) Synchronizes state across threads
- C) Allows object to change behavior when
- D) Stores object state in database
  **Answer: A**

### Q350. Identify the correct statement about refactoring in OOP.

- A) Rewriting code from scratch
- B) Adding new features
- C) Fixing bugs
- D) Restructuring existing
  **Answer: C**

### Q351. When designing for high performance, identify the correct statement about Null Object pattern.

- A) Checks for null references
- B) Returns null instead of object
- C) Provides default object instead
- D) Cleans null pointers
  **Answer: A**

