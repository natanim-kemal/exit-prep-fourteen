# Object-Oriented Programming — Study Notes

## 1. OOP Fundamentals

**Class**: blueprint/template for creating objects.
**Object**: instance of a class.

### Three Pillars (Core Concepts):
1. **Encapsulation**: Bundling data + methods; hiding internal details. Fields are private, accessed via public getters/setters. Protects data integrity.
2. **Inheritance**: Child class (subclass) inherits properties/behaviors from parent class (superclass). "is-a" relationship. Use `extends` keyword.
3. **Polymorphism**: Same interface, different implementations. "Many forms." Literally means many forms/shapes — one name, multiple behaviors.
4. **Abstraction**: Hide complexity, show only essentials.

## 2. Access Modifiers
- **private**: accessible only within its own class
- **protected**: accessible within same package and subclasses
- **public**: accessible from anywhere
- **default** (no modifier): accessible within same package only

## 3. Constructors & Destructors
- **Constructor**: same name as class, no return type (not even void). Called when object is created. Can be overloaded (multiple constructors with different parameters).
- **Copy constructor**: creates a new object as a copy of an existing object.
- **this keyword**: refers to the current object instance.
- **super keyword**: calls parent class constructor/methods.
- **Destructor**: frees resources when object is destroyed.

## 4. Method Overloading vs Overriding
| Feature | Overloading | Overriding |
|---------|------------|------------|
| When | Compile-time | Runtime |
| Relationship | Same class | Parent-child |
| Parameters | Must differ | Must match exactly |
| Return type | Can differ | Must match |
| Keyword | — | @Override |
| Purpose | Same operation, different inputs | Subclass-specific behavior |
| Binding | Static/early | Dynamic/late |

**Compile-time polymorphism** = method overloading.
**Runtime polymorphism** = method overriding with virtual functions.

## 5. Abstract Classes vs Interfaces (Java)
| Feature | Abstract Class | Interface |
|---------|---------------|-----------|
| Instantiation | Cannot be instantiated | Cannot be instantiated |
| Methods | Can have concrete + abstract methods | Before Java 8: only abstract; Java 8+: default & static methods |
| Fields | Any type | public static final only |
| Constructor | Yes | No |
| Multiple inheritance | No (single inheritance) | Yes (implement multiple interfaces) |
| Keyword | `abstract` | `interface` |

**A class cannot be instantiated if it is abstract.**

## 6. Relationships in UML
- **"is-a"**: Inheritance/Generalization (empty triangle arrow)
- **"has-a" (loose)**: Aggregation — child can exist without parent (empty diamond)
- **"has-a" (strong)**: Composition — child cannot exist without parent (filled diamond)
- **Implements**: dotted triangle arrow

## 7. SOLID Principles
1. **S**ingle Responsibility: A class should have only one reason to change.
2. **O**pen/Closed: Open for extension, closed for modification.
3. **L**iskov Substitution: Subclass can replace parent without breaking the program.
4. **I**nterface Segregation: Clients should not depend on interfaces they don't use.
5. **D**ependency Inversion: Depend on abstractions, not concretions.

**DRY Principle**: Don't Repeat Yourself.

## 8. Exception Handling
- **try-catch-finally**: `finally` block always runs (regardless of exception).
- **Checked exceptions**: must be caught or declared (IOException, SQLException).
- **Unchecked exceptions (RuntimeException)**: don't need to be caught (NullPointerException, ArrayIndexOutOfBoundsException).
- **Common exceptions**: NullPointerException (null reference), ClassCastException (incompatible cast), ArrayIndexOutOfBoundsException (invalid index).

## 9. Key Java Keywords
- **final**: prevents class from being subclassed, method from being overridden, variable from being reassigned
- **static**: belongs to the class, not instances; shared across all instances
- **instanceof**: checks if object is instance of a given type
- **new**: creates object, returns reference to newly created object
- **equals()**: checks logical equality; `==` compares references
- **toString()**: returns string representation of object
- **Anonymous class**: defined and instantiated at the same time
- **Lambda expression**: short anonymous function (Java 8+)
- **Interface default method**: provides default implementation (Java 8+)

## 10. Design Patterns (GoF — 23 Patterns)

### Creational (5)
- **Singleton**: ensures only one instance globally (private constructor, static getInstance())
- **Factory**: creates objects without specifying exact class
- **Abstract Factory**: creates families of related objects
- **Builder**: separates object construction from representation (step-by-step)
- **Prototype**: creates objects by cloning existing ones

### Structural (7)
- **Adapter**: converts incompatible interfaces to work together
- **Decorator**: dynamically adds behavior to objects (wrapper)
- **Proxy**: placeholder controlling access to another object
- **Facade**: provides simplified interface to complex subsystem
- **Composite**: treats individual objects and compositions uniformly
- **Bridge**: separates abstraction from implementation
- **Flyweight**: shares objects for efficient memory usage

### Behavioral (11)
- **Observer**: notifies multiple objects when state changes (pub-sub)
- **Strategy**: selects algorithm at runtime (interchangeable algorithms)
- **Command**: encapsulates requests as objects (undo/redo)
- **Iterator**: sequentially accesses elements of a collection
- **State**: object changes behavior when internal state changes
- **Template Method**: defines skeleton algorithm in base class
- **Memento**: saves/restores object state (undo)
- **Chain of Responsibility**: passes request along a chain of handlers
- **Mediator**: centralizes communication between objects
- **Visitor**: adds operations without changing classes
- **Interpreter**: defines grammar and interprets sentences
