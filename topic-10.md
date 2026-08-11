# Topic 10: OOP: Polymorphism & Generics

Polymorphism lets you treat derived types as their base type, with the correct behavior dispatched at runtime. Override replaces base behavior, new hides it, and sealed prevents further overriding. Generics let you write type-safe, reusable code that works with any type while avoiding boxing and casts.

## Learn From

Study runtime polymorphism (virtual/override), compile-time hiding (new), and generic type constraints.

- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/polymorphism
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/new-modifier
- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/generics/generic-type-parameters
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/where-clause

## Key Concepts

- Polymorphism allows a base reference to hold a derived object and invoke the correct method
- override replaces the base implementation; the runtime determines which method to call
- new explicitly hides an inherited member without polymorphic dispatch
- sealed override prevents further overriding of a virtual member in a derived class
- Generics enable type-safe, reusable code without boxing or casting
- Generic type constraints (where T : class, struct, new()) restrict what types can be used
- Generic methods can be called with explicit type arguments or inferred types
- Covariance (out) and contravariance (in) allow flexibility in generic type assignment
- A generic class can have multiple type parameters
- Open generics allow runtime type construction while closed generics are fully specified

## Practice Problems & Solutions

### Problem 1

Write a base class Animal with virtual Speak and a Dog that overrides it.

**Solution:**

```
class Animal { public virtual void Speak() { } } class Dog : Animal { public override void Speak() { Console.WriteLine("Woof"); } }
```

**Expected output:**

```
class Animal { public virtual void Speak() { } } class Dog : Animal { public override void Speak() { Console.WriteLine("Woof"); } }
```

**Learning points:** 

### Problem 2

Use new to hide a base method in a derived class.

**Solution:**

```
class Base { public void Do() { } } class Derived : Base { public new void Do() { } }
```

**Expected output:**

```
class Base { public void Do() { } } class Derived : Base { public new void Do() { } }
```

**Learning points:** 

### Problem 3

Create a generic List<T> and add three integers to it.

**Solution:**

```
var list = new List<int> { 1, 2, 3 };
```

**Expected output:**

```
var list = new List<int> { 1, 2, 3 };
```

**Learning points:** 

### Problem 4

Write a generic method Max<T> that returns the larger of two values, constrained to IComparable<T>.

**Solution:**

```
T Max<T>(T a, T b) where T : IComparable<T> => a.CompareTo(b) > 0 ? a : b;
```

**Expected output:**

```
T Max<T>(T a, T b) where T : IComparable<T> => a.CompareTo(b) > 0 ? a : b;
```

**Learning points:** 

### Problem 5

Seal an override so no further subclass can override it.

**Solution:**

```
class Base { public virtual void Do() { } } class Middle : Base { public sealed override void Do() { } }
```

**Expected output:**

```
class Base { public virtual void Do() { } } class Middle : Base { public sealed override void Do() { } }
```

**Learning points:** 

### Problem 6

Create a generic Pair<T> class with First and Second properties.

**Solution:**

```
class Pair<T> { public T First { get; set; } public T Second { get; set; } }
```

**Expected output:**

```
class Pair<T> { public T First { get; set; } public T Second { get; set; } }
```

**Learning points:** 

### Problem 7

Use a generic constraint to require that T is a reference type with a parameterless constructor.

**Solution:**

```
class Factory<T> where T : class, new() { public T Create() => new T(); }
```

**Expected output:**

```
class Factory<T> where T : class, new() { public T Create() => new T(); }
```

**Learning points:** 

### Problem 8

Demonstrate covariance using IEnumerable<out T>.

**Solution:**

```
IEnumerable<Derived> derived = new List<Derived>(); IEnumerable<Base> bases = derived;
```

**Expected output:**

```
IEnumerable<Derived> derived = new List<Derived>(); IEnumerable<Base> bases = derived;
```

**Learning points:** 

### Problem 9

Write a generic Repository<T> with a GetById method.

**Solution:**

```
class Repository<T> where T : class { public T GetById(int id) { return default; } }
```

**Expected output:**

```
class Repository<T> where T : class { public T GetById(int id) { return default; } }
```

**Learning points:** 

### Problem 10

Use typeof to get the Type of a generic parameter at runtime.

**Solution:**

```
Type t = typeof(T);
```

**Expected output:**

```
Type t = typeof(T);
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between override and new?

**A:** Override replaces the virtual method and is called polymorphically; new hides the base member and is called based on the compile-time type, not the runtime type.

**Q2:** When should you use sealed override?

**A:** When you want to prevent further derived classes from overriding a virtual method, sealing the implementation.

**Q3:** What are generic type constraints?

**A:** They restrict which types can be used as generic arguments using where clauses like class, struct, new(), or interface constraints.

**Q4:** Why are generics better than using object?

**A:** Generics are type-safe at compile time, avoid boxing/unboxing overhead, and eliminate the need for explicit casts.

**Q5:** What is covariance in generics?

**A:** Covariance (out) allows an interface or delegate to return a more derived type; IEnumerable<Derived> can be assigned to IEnumerable<Base>.

**Q6:** What is contravariance in generics?

**A:** Contravariance (in) allows a parameter to accept a less derived type; Action<Base> can be assigned to Action<Derived>.

**Q7:** Can a generic class implement an interface?

**A:** Yes; for example, List<T> implements IEnumerable<T>, allowing type-safe iteration over any element type.

**Q8:** What is an open generic type?

**A:** A generic type with unresolved type parameters, such as List<T>; it becomes a closed generic when fully specified as List<int>.

**Q9:** How do you call a generic method with explicit type arguments?

**A:** Use the syntax Method<Type>(args), e.g., Max<int>(1, 2).

**Q10:** What is the default(T) expression?

**A:** It returns the default value for a generic type: null for reference types, 0 for numeric types, false for bool, etc.
