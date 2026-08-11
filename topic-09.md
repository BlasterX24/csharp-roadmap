# Topic 9: OOP: Inheritance & Interfaces

Inheritance lets a class derive from a base class, inheriting its members. Abstract classes define incomplete contracts that derived classes must fulfill. Interfaces define a contract of members that implementing classes must provide. Together they enable polymorphism, code reuse, and clean architectural separation.

## Learn From

Study inheritance and interface implementation, focusing on virtual/override, abstract classes, and interface default implementations.

- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/tutorials/inheritance
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/abstract
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/interface
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/virtual

## Key Concepts

- A derived class inherits all non-private members from its base class
- virtual members can be overridden in derived classes with override
- abstract members have no implementation and must be overridden
- sealed classes prevent further inheritance
- An interface defines a contract of methods, properties, events, or indexers
- A class can implement multiple interfaces but inherit from only one class
- The 'base' keyword accesses members of the parent class
- Interface default implementations provide fallback code in C# 8+
- Explicit interface implementations resolve ambiguity between multiple interfaces
- The Liskov Substitution Principle requires derived classes to be substitutable for base

## Practice Problems & Solutions

### Problem 1

Create a base class Animal with a virtual Speak method.

**Solution:**

```
class Animal { public virtual void Speak() { Console.WriteLine("..."); } }
```

**Expected output:**

```
class Animal { public virtual void Speak() { Console.WriteLine("..."); } }
```

**Learning points:** 

### Problem 2

Create a Dog class that overrides Animal.Speak to print "Woof!".

**Solution:**

```
class Dog : Animal { public override void Speak() { Console.WriteLine("Woof!"); } }
```

**Expected output:**

```
class Dog : Animal { public override void Speak() { Console.WriteLine("Woof!"); } }
```

**Learning points:** 

### Problem 3

Define an interface ISwim with a Swim method.

**Solution:**

```
interface ISwim { void Swim(); }
```

**Expected output:**

```
interface ISwim { void Swim(); }
```

**Learning points:** 

### Problem 4

Make Duck inherit from Animal and implement ISwim.

**Solution:**

```
class Duck : Animal, ISwim { public void Swim() { Console.WriteLine("Swimming"); } }
```

**Expected output:**

```
class Duck : Animal, ISwim { public void Swim() { Console.WriteLine("Swimming"); } }
```

**Learning points:** 

### Problem 5

Create an abstract class Shape with an abstract Area method.

**Solution:**

```
abstract class Shape { public abstract double Area(); }
```

**Expected output:**

```
abstract class Shape { public abstract double Area(); }
```

**Learning points:** 

### Problem 6

Create a Circle class that inherits Shape and implements Area.

**Solution:**

```
class Circle : Shape { double radius; public Circle(double r) { radius = r; } public override double Area() => Math.PI * radius * radius; }
```

**Expected output:**

```
class Circle : Shape { double radius; public Circle(double r) { radius = r; } public override double Area() => Math.PI * radius * radius; }
```

**Learning points:** 

### Problem 7

Use base to call the parent constructor from a derived class.

**Solution:**

```
class Derived : Base { public Derived(int x) : base(x) { } }
```

**Expected output:**

```
class Derived : Base { public Derived(int x) : base(x) { } }
```

**Learning points:** 

### Problem 8

Seal a class so it cannot be inherited.

**Solution:**

```
sealed class FinalClass { }
```

**Expected output:**

```
sealed class FinalClass { }
```

**Learning points:** 

### Problem 9

Use an interface to require a Calculate method on any implementing class.

**Solution:**

```
interface ICalculator { double Calculate(double a, double b); }
```

**Expected output:**

```
interface ICalculator { double Calculate(double a, double b); }
```

**Learning points:** 

### Problem 10

Explicitly implement an interface method so it is only accessible via the interface type.

**Solution:**

```
class MyClass : IMyInterface { void IMyInterface.DoWork() { } }
```

**Expected output:**

```
class MyClass : IMyInterface { void IMyInterface.DoWork() { } }
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** Why can't C# classes inherit from multiple classes?

**A:** C# uses single inheritance for classes to avoid the diamond problem; multiple interface implementation provides the flexibility of multiple contracts.

**Q2:** What is the difference between abstract and virtual?

**A:** Abstract has no implementation and forces overriding; virtual provides a default implementation that derived classes may optionally override.

**Q3:** Can you create an instance of an abstract class?

**A:** No; abstract classes cannot be instantiated directly; they must be subclassed and their abstract members implemented.

**Q4:** What happens if a class does not implement all interface members?

**A:** It must be declared abstract, or the compiler reports an error for unimplemented members.

**Q5:** What is the sealed keyword used for?

**A:** It prevents a class from being inherited or a virtual/override member from being further overridden.

**Q6:** What is explicit interface implementation?

**A:** It implements an interface member with a fully qualified name, making it accessible only through the interface type, not through the class.

**Q7:** Can an interface have fields?

**A:** No; interfaces can only declare methods, properties, events, and indexers (C# 11 adds default interface methods).

**Q8:** What is the 'base' keyword?

**A:** It accesses the base class's implementation of a method, constructor, or property, useful for extending rather than replacing behavior.

**Q9:** Can a class inherit an interface and provide a default implementation?

**A:** Yes; since C# 8, interfaces can contain default implementations that classes inherit unless overridden.

**Q10:** What is the Liskov Substitution Principle?

**A:** Objects of a derived class should be substitutable for objects of the base class without altering correctness.
