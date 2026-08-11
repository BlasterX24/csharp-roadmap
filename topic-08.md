# Topic 8: OOP: Classes & Objects

Classes are the fundamental building blocks of object-oriented programming in C#. They encapsulate data (fields) and behavior (methods). Properties provide controlled access to fields. Constructors initialize objects. Static members belong to the type itself. Readonly fields ensure immutability after construction.

## Learn From

Review the classes and objects tutorial, then study properties, constructors, and access modifiers in depth.

- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/tutorials/classes
- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties
- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/constructors
- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members

## Key Concepts

- A class is a blueprint for objects; objects are instances of a class
- Fields store data; properties wrap fields with get/set accessors
- Auto-implemented properties { get; set; } generate backing fields automatically
- Constructors are special methods called when creating an object
- Static constructors run once when the type is first used
- Static members belong to the type, not any particular instance
- Readonly fields can only be assigned in the constructor or field initializer
- Access modifiers (public, private, protected, internal) control visibility
- The 'this' keyword refers to the current instance
- Dispose pattern manages unmanaged resources deterministically

## Practice Problems & Solutions

### Problem 1

Create a Person class with Name and Age auto-properties.

**Solution:**

```
class Person { public string Name { get; set; } public int Age { get; set; } }
```

**Expected output:**

```
class Person { public string Name { get; set; } public int Age { get; set; } }
```

**Learning points:** 

### Problem 2

Write a constructor for Person that takes name and age as parameters.

**Solution:**

```
class Person { public string Name { get; set; } public int Age { get; set; } public Person(string name, int age) { Name = name; Age = age; } }
```

**Expected output:**

```
class Person { public string Name { get; set; } public int Age { get; set; } public Person(string name, int age) { Name = name; Age = age; } }
```

**Learning points:** 

### Problem 3

Add a readonly field Id to Person that is set in the constructor.

**Solution:**

```
class Person { public readonly int Id; public Person(int id) { Id = id; } }
```

**Expected output:**

```
class Person { public readonly int Id; public Person(int id) { Id = id; } }
```

**Learning points:** 

### Problem 4

Create a static class MathHelper with a static method Add.

**Solution:**

```
static class MathHelper { public static int Add(int a, int b) => a + b; }
```

**Expected output:**

```
static class MathHelper { public static int Add(int a, int b) => a + b; }
```

**Learning points:** 

### Problem 5

Write a property with only a getter that computes FullName from First and Last.

**Solution:**

```
public string FullName => $"{First} {Last}";
```

**Expected output:**

```
public string FullName => $"{First} {Last}";
```

**Learning points:** 

### Problem 6

Create a private field _count and expose it via a public Count property.

**Solution:**

```
class Counter { private int _count; public int Count { get { return _count; } set { _count = value; } } }
```

**Expected output:**

```
class Counter { private int _count; public int Count { get { return _count; } set { _count = value; } } }
```

**Learning points:** 

### Problem 7

Write an object initializer to create a Person with Name="Alice" and Age=30.

**Solution:**

```
var p = new Person { Name = "Alice", Age = 30 };
```

**Expected output:**

```
var p = new Person { Name = "Alice", Age = 30 };
```

**Learning points:** 

### Problem 8

Create a static constructor that initializes a static field.

**Solution:**

```
class Config { public static string AppName; static Config() { AppName = "MyApp"; } }
```

**Expected output:**

```
class Config { public static string AppName; static Config() { AppName = "MyApp"; } }
```

**Learning points:** 

### Problem 9

Use the 'this' keyword to disambiguate a parameter from a field.

**Solution:**

```
class Person { string name; public Person(string name) { this.name = name; } }
```

**Expected output:**

```
class Person { string name; public Person(string name) { this.name = name; } }
```

**Learning points:** 

### Problem 10

Add a private setter to the Id property so it can only be set internally.

**Solution:**

```
public int Id { get; private set; }
```

**Expected output:**

```
public int Id { get; private set; }
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between a field and a property?

**A:** A field is a variable in a class; a property provides get/set accessors that can add validation, logging, or computed logic.

**Q2:** When is a static constructor called?

**A:** Exactly once, before any static member is accessed or any instance is created.

**Q3:** Can a readonly field be modified after construction?

**A:** No; readonly fields can only be assigned in the constructor or field initializer, not afterward.

**Q4:** What does 'this' refer to in a class?

**A:** It refers to the current instance of the class, allowing access to instance members and disambiguation from local variables.

**Q5:** What is the difference between private and protected access?

**A:** Private members are accessible only within the declaring class; protected members are also accessible in derived classes.

**Q6:** What is an object initializer?

**A:** A syntax that lets you set properties at object creation time without calling a constructor, using { Prop = value } after new.

**Q7:** Can properties have different access levels for get and set?

**A:** Yes; you can write { get; private set; } or { private get; set; } to restrict access on one side.

**Q8:** What is the purpose of the 'new' keyword when hiding a base member?

**A:** It explicitly indicates you are hiding an inherited member; the compiler warns if you omit 'new' when hiding.

**Q9:** What is the dispose pattern?

**A:** A pattern for deterministically releasing unmanaged resources by implementing IDisposable with a Dispose method and optional finalizer.

**Q10:** What is the difference between a struct and a class?

**A:** Structs are value types (copied by value); classes are reference types (copied by reference). Structs do not support inheritance.
