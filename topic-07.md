# Topic 7: Methods & Params

Methods are the building blocks of C# programs. They encapsulate reusable logic and can accept parameters by value, by reference (ref), as output (out), or as read-only (in). Default parameter values let callers omit arguments. The params keyword enables variable-length argument lists. Expression-bodied members provide concise syntax for simple methods.

## Learn From

Study the method parameter modifiers reference and practice with ref, out, and params to understand value vs reference semantics.

- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/ref
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/out-parameter-modifier
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/params

## Key Concepts

- Methods are defined with access modifier, return type, name, and parameter list
- Passing by value copies the value; ref passes by reference allowing modification
- out parameters must be assigned inside the method before returning
- in parameters are read-only references; cannot be modified
- Default parameter values let callers omit arguments with matching defaults
- params allows a variable number of arguments as an array
- Expression-bodied members use => for one-liner methods and properties
- Local functions are methods defined inside other methods
- Method overloading allows multiple methods with the same name but different signatures
- Static methods belong to the type, not an instance

## Practice Problems & Solutions

### Problem 1

Write a method Add that takes two ints and returns their sum.

```
int Add(int a, int b) => a + b;
```

**Expected output:**

```
int Add(int a, int b) => a + b;
```

**Learning points:** 

### Problem 2

Write a method DoubleRef that uses ref to double a parameter.

```
void DoubleRef(ref int x) { x *= 2; }
```

**Expected output:**

```
void DoubleRef(ref int x) { x *= 2; }
```

**Learning points:** 

### Problem 3

Write a method TryDivide that returns true via out and the result via a second out.

```
bool TryDivide(int a, int b, out double result) { result = 0; if (b == 0) return false; result = (double)a / b; return true; }
```

**Expected output:**

```
bool TryDivide(int a, int b, out double result) { result = 0; if (b == 0) return false; result = (double)a / b; return true; }
```

**Learning points:** 

### Problem 4

Write a method with a default parameter greeting = "Hello".

```
void Greet(string greeting = "Hello") { Console.WriteLine(greeting); }
```

**Expected output:**

```
void Greet(string greeting = "Hello") { Console.WriteLine(greeting); }
```

**Learning points:** 

### Problem 5

Write a method using params to accept any number of ints and return their sum.

```
int Sum(params int[] numbers) { int total = 0; foreach (var n in numbers) total += n; return total; }
```

**Expected output:**

```
int Sum(params int[] numbers) { int total = 0; foreach (var n in numbers) total += n; return total; }
```

**Learning points:** 

### Problem 6

Write an expression-bodied method that returns the square of an int.

```
int Square(int x) => x * x;
```

**Expected output:**

```
int Square(int x) => x * x;
```

**Learning points:** 

### Problem 7

Write a method that takes an in parameter and prints it without modifying it.

```
void Print(in int value) { Console.WriteLine(value); }
```

**Expected output:**

```
void Print(in int value) { Console.WriteLine(value); }
```

**Learning points:** 

### Problem 8

Overload a method Print to accept either an int or a string.

```
void Print(int n) { Console.WriteLine(n); } void Print(string s) { Console.WriteLine(s); }
```

**Expected output:**

```
void Print(int n) { Console.WriteLine(n); } void Print(string s) { Console.WriteLine(s); }
```

**Learning points:** 

### Problem 9

Write a local function inside a method that calculates factorial.

```
int Factorial(int n) { int fact(int x) => x <= 1 ? 1 : x * fact(x - 1); return fact(n); }
```

**Expected output:**

```
int Factorial(int n) { int fact(int x) => x <= 1 ? 1 : x * fact(x - 1); return fact(n); }
```

**Learning points:** 

### Problem 10

Write a method with named arguments so the caller can pass arguments in any order.

```
void Build(string name, int age) { }
```

**Expected output:**

```
void Build(string name, int age) { }
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between ref and out parameters?

**A:** ref requires the variable to be initialized before calling the method; out does not require pre-initialization but must be assigned inside the method.

**Q2:** Can default parameter values be used with ref or out?

**A:** No; ref, out, and in parameters cannot have default values because they require an explicit variable reference.

**Q3:** What is the purpose of the in parameter modifier?

**A:** It passes a value by reference but prevents modification, useful for large structs to avoid copying while ensuring immutability.

**Q4:** How does params differ from a regular array parameter?

**A:** params lets the caller pass individual arguments that the compiler wraps into an array; a regular array parameter requires the caller to construct the array.

**Q5:** Can you overload methods based on return type alone?

**A:** No; overloading is based on parameter list (name, count, types, modifiers), not on return type.

**Q6:** What is an expression-bodied method?

**A:** A concise syntax using => that replaces the method body with a single expression; the compiler infers the return.

**Q7:** What are named arguments?

**A:** Named arguments let you specify the parameter name when calling a method, allowing arguments to be passed in any order.

**Q8:** What is the difference between a static method and an instance method?

**A:** A static method belongs to the type and can be called without an instance; an instance method requires an object and can access instance members.

**Q9:** What is a local function?

**A:** A function defined inside another method that can capture variables from the enclosing scope, useful for helper logic.

**Q10:** Can you use params with named arguments?

**A:** Yes, but the params array must be the last parameter; named arguments can precede it.
