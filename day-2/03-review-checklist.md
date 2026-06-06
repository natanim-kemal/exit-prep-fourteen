# Day 2 — OOP Review Checklist

## Mastery Checklist

### OOP Principles
- [ ] Four pillars: Encapsulation, Inheritance, Polymorphism, Abstraction
- [ ] Encapsulation: private fields, public getters/setters
- [ ] IS-A vs HAS-A relationships

### Classes & Objects
- [ ] Class declaration syntax
- [ ] Object creation: `new ClassName(args)`
- [ ] Reference variables vs actual objects
- [ ] `this` keyword usage
- [ ] Object references point to same memory

### Constructors
- [ ] Constructor rules (same name, no return type)
- [ ] Default constructor (provided if none defined)
- [ ] Constructor overloading
- [ ] `this()` for calling another constructor

### Access Modifiers
- [ ] `public`, `private`, `protected`, default
- [ ] Visibility from: class, package, subclass, world

### Static
- [ ] static variables (shared across instances)
- [ ] static methods (no access to instance members)
- [ ] Calling static members: `ClassName.member`

### Inheritance
- [ ] `extends` keyword
- [ ] Single inheritance in Java (class)
- [ ] What is inherited / what is not
- [ ] `super` keyword (parent constructor + methods)
- [ ] Constructor chaining (parent called first)

### Polymorphism
- [ ] Method overloading (compile-time, same name different params)
- [ ] Method overriding (runtime, same signature, different class)
- [ ] Dynamic binding (actual object type determines method)
- [ ] Overloading vs Overriding differences

### Abstract Classes & Interfaces
- [ ] Abstract class: cannot instantiate, can have concrete + abstract methods
- [ ] Interface: all methods abstract (pre-Java 8), multiple implementation
- [ ] `extends` vs `implements`
- [ ] Multiple interface implementation
- [ ] Abstract vs Interface comparison

### UML
- [ ] Class notation: name, attributes, methods
- [ ] Visibility indicators: + public, - private, # protected
- [ ] Inheritance arrow (empty triangle)
- [ ] Implementation arrow (dashed triangle)

### GUI (Swing)
- [ ] AWT vs Swing differences
- [ ] JFrame (top-level, BorderLayout)
- [ ] JPanel (lightweight, FlowLayout)
- [ ] Common components: JButton, JLabel, JTextField, JTextArea
- [ ] Setting bounds, layout, visibility
- [ ] Event delegation model: source → listener → handler
- [ ] `addActionListener()`, `actionPerformed()`
- [ ] Event classes: ActionEvent, MouseEvent
- [ ] Listener interfaces: ActionListener, MouseListener

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **4 Pillars** | **E.I.P.A.** (Elephants In Pink Armor) |
| **Constructor** | "Same name, no return, called on `new`" |
| **Static** | "One copy for all" |
| **Override** | "Same signature, different behavior" |
| **Overload** | "Same name, different params" |
| **Abstract** | "Cannot `new`, must `extend`" |
| **Interface** | "Cannot `new`, must `implement`, can do many" |
| **super()** | "First line or error" |
| **UML visibility** | "+ is public, - is private, # is protected" |
| **BorderLayout** | "North South East West Center" — NSEWC |

---

## Bloom's Taxonomy — OOP/GUI

| Level | What You Must Do |
|-------|------------------|
| **Remember** | Define OOP principles, syntax rules |
| **Understand** | Explain what a class/object relationship means |
| **Apply** | Write a class definition, create objects |
| **Analyze** | Trace code execution, find errors in class design |
| **Evaluate** | Choose appropriate OOP design for a scenario |
| **Create** | Design class hierarchy for a given problem |

---

## 1-Page Cram Sheet

```
OOP PILLARS
═══════════
Encapsulation → private data, public methods
Inheritance   → Child extends Parent
Polymorphism  → overloading (compile) + overriding (runtime)
Abstraction   → abstract classes, interfaces

CLASS STRUCTURE
═══════════════
class ClassName {
    // fields (usually private)
    // constructor(s)
    // methods (usually public)
}

CONSTRUCTOR RULES
═════════════════
- Same name as class
- No return type
- Called with 'new'
- Overloadable
- super() must be first line

ACCESS LEVELS (most → least restrictive)
══════════════════════════════════════
private → default → protected → public

STATIC
══════
static variable = class variable (one copy)
static method  = class method (no 'this', no instance access)
Call: ClassName.staticMember

INHERITANCE
═══════════
Child extends Parent
Single class inheritance
super() calls parent constructor
@Override for method overriding

ABSTRACT vs INTERFACE
═════════════════════
Abstract class: has abstract + concrete methods, has fields
Interface:      all abstract (pre Java 8), constants only
Class can:      extend ONE class, implement MANY interfaces

SWING COMPONENTS
════════════════
JFrame    → window (BorderLayout)
JPanel    → panel (FlowLayout)
JButton   → click
JLabel    → text/image
JTextField → single line input
JTextArea → multi line input

EVENT HANDLING
══════════════
Source.addXxxListener(listener)
listener implements XxxListener
Override handler method (e.g., actionPerformed)

UML NOTATION
════════════
+ public
- private
# protected
▷— inheritance
- - ▷  implementation
```
