# Topic 2: Variables & Types

C# is statically typed, meaning every variable has a compile-time type. You can use explicit types like int, double, string, and bool, or let the compiler infer types with var. Constants use const and are evaluated at compile time. The dynamic keyword defers type checking to runtime for interop scenarios.

## Learn From

Review the official C# type reference and the article on implicit typing to understand when to use var versus explicit types.

- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/reference-types
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/var
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/nullable-value-types

## Key Concepts

- Value types (int, double, bool, char, struct) store data directly on the stack
- Reference types (string, class, array, delegate) store a reference on the heap
- var lets the compiler infer the type; the variable is still strongly typed
- const fields must be assigned at declaration and cannot change
- readonly fields can only be assigned in the constructor or field initializer
- dynamic disables compile-time type checking; resolved at runtime
- Nullable value types (int?) add a null value to value types
- Implicit typing with var improves readability when the type is obvious
- String is a reference type but is immutable
- Tuple types let you group multiple values without creating a new class

## Practice Problems & Solutions

### Problem 1

Declare an integer variable named count and initialize it to 42.

```
int count = 42;
```

**Expected output:**

```
int count = 42;
```

**Learning points:** 

### Problem 2

Declare a constant string called APP_NAME with value "MyApp".

```
const string APP_NAME = "MyApp";
```

**Expected output:**

```
const string APP_NAME = "MyApp";
```

**Learning points:** 

### Problem 3

Use var to declare a variable that holds the value 3.14.

```
var pi = 3.14;
```

**Expected output:**

```
var pi = 3.14;
```

**Learning points:** 

### Problem 4

Declare a nullable int variable named age that can be null.

```
int? age = null;
```

**Expected output:**

```
int? age = null;
```

**Learning points:** 

### Problem 5

Write code that converts a string "100" to an integer.

```
int num = int.Parse("100");
```

**Expected output:**

```
int num = int.Parse("100");
```

**Learning points:** 

### Problem 6

Declare a boolean flag set to true.

```
bool flag = true;
```

**Expected output:**

```
bool flag = true;
```

**Learning points:** 

### Problem 7

Create a tuple with a string name and int age.

```
var person = (Name: "Alice", Age: 30);
```

**Expected output:**

```
var person = (Name: "Alice", Age: 30);
```

**Learning points:** 

### Problem 8

Write code that safely tries to parse a string to int, returning a default on failure.

```
int result = int.TryParse("abc", out int val) ? val : 0;
```

**Expected output:**

```
int result = int.TryParse("abc", out int val) ? val : 0;
```

**Learning points:** 

### Problem 9

Declare a dynamic variable and assign a string to it.

```
dynamic item = "hello";
```

**Expected output:**

```
dynamic item = "hello";
```

**Learning points:** 

### Problem 10

What is the default value of an uninitialized bool field in a class?

```
false
```

**Expected output:**

```
false
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between const and readonly?

**A:** const is compile-time constant and implicitly static; readonly is set at runtime (in constructor or field initializer) and is an instance member.

**Q2:** When should you use var instead of an explicit type?

**A:** Use var when the type is obvious from the right side of the assignment, such as new expressions or cast results, to improve readability.

**Q3:** Why is string a reference type but immutable?

**A:** Strings are reference types allocated on the heap, but once created their contents cannot change; any operation that modifies a string returns a new string instance.

**Q4:** What happens when you assign null to a non-nullable value type?

**A:** It causes a compile-time error unless the variable is declared as a nullable value type with the ? suffix.

**Q5:** What is boxing and unboxing?

**A:** Boxing wraps a value type in an object on the heap; unboxing extracts the value type from the object, which can throw InvalidCastException if types mismatch.

**Q6:** What is the difference between string and String?

**A:** string (lowercase) is an alias for System.String; they compile to the same type, but string is the idiomatic C# keyword.

**Q7:** Can a const field be of type DateTime?

**A:** No; const values must be determined at compile time, and DateTime is not a compile-time constant.

**Q8:** What is dynamic and when would you use it?

**A:** dynamic bypasses compile-time type checking; use it for COM interop, dynamic objects like ExpandoObject, or reflection-heavy scenarios.

**Q9:** How do you declare a tuple variable with named elements?

**A:** var t = (Name: "Bob", Score: 95); then access with t.Name or t.Score.

**Q10:** What is the difference between var and object?

**A:** var lets the compiler infer a specific type at compile time; object stores any value but requires casting to use type-specific members.
