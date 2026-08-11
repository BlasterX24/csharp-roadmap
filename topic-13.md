# Topic 13: Lambda & Functional

Lambda expressions are anonymous functions that can capture variables from their enclosing scope (closures). They are the foundation of LINQ queries, delegate instantiation, and functional programming patterns in C#. Lambdas can be assigned to delegates, passed as arguments, and used in expression trees.

## Learn From

Study lambda syntax, closures, and how lambdas integrate with delegates and LINQ.

- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions
- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-operator
- https://learn.microsoft.com/en-us/dotnet/csharp/advanced-topics/expression-trees/

## Key Concepts

- Lambda expressions use => to define anonymous methods
- Single-line lambdas can omit braces and the return keyword
- Multi-line lambdas use braces and an explicit return statement
- Lambdas capture variables from the enclosing scope (closures)
- Captured variables are shared across all invocations of the lambda
- Lambdas can be converted to delegates or expression trees
- Expression trees store the lambda as data, enabling translation to SQL or other languages
- Local variables captured by lambdas live as long as the delegate
- Lambdas enable functional patterns like map, filter, and reduce via LINQ
- Discard parameters _ let you ignore unused lambda arguments

## Practice Problems & Solutions

### Problem 1

Write a lambda that takes an int and returns its square.

**Solution:**

```
Func<int, int> square = x => x * x;
```

**Expected output:**

```
Func<int, int> square = x => x * x;
```

**Learning points:** 

### Problem 2

Write a lambda that captures a variable and adds it to each element.

**Solution:**

```
int addend = 10; Func<int, int> add = n => n + addend;
```

**Expected output:**

```
int addend = 10; Func<int, int> add = n => n + addend;
```

**Learning points:** 

### Problem 3

Use a lambda with Select to convert strings to uppercase.

**Solution:**

```
var upper = names.Select(n => n.ToUpper());
```

**Expected output:**

```
var upper = names.Select(n => n.ToUpper());
```

**Learning points:** 

### Problem 4

Write a multi-line lambda that calculates factorial.

**Solution:**

```
Func<int, int> fact = n => { int r = 1; for (int i = 2; i <= n; i++) r *= i; return r; };
```

**Expected output:**

```
Func<int, int> fact = n => { int r = 1; for (int i = 2; i <= n; i++) r *= i; return r; };
```

**Learning points:** 

### Problem 5

Use a lambda as a predicate in Where to filter odd numbers.

**Solution:**

```
var odds = nums.Where(x => x % 2 != 0);
```

**Expected output:**

```
var odds = nums.Where(x => x % 2 != 0);
```

**Learning points:** 

### Problem 6

Pass a lambda to Array.Find to find the first negative number.

**Solution:**

```
int first = Array.Find(arr, x => x < 0);
```

**Expected output:**

```
int first = Array.Find(arr, x => x < 0);
```

**Learning points:** 

### Problem 7

Use a lambda with OrderBy to sort by string length.

**Solution:**

```
var sorted = names.OrderBy(n => n.Length);
```

**Expected output:**

```
var sorted = names.OrderBy(n => n.Length);
```

**Learning points:** 

### Problem 8

Write a lambda that returns a tuple with the input and its square.

**Solution:**

```
Func<int, (int, int)> pair = x => (x, x * x);
```

**Expected output:**

```
Func<int, (int, int)> pair = x => (x, x * x);
```

**Learning points:** 

### Problem 9

Use a discard in a lambda to ignore the second parameter.

**Solution:**

```
Func<int, int, int> first = (a, _) => a;
```

**Expected output:**

```
Func<int, int, int> first = (a, _) => a;
```

**Learning points:** 

### Problem 10

Create a Func<string, bool> lambda that checks if a string contains "test".

**Solution:**

```
Func<string, bool> containsTest = s => s.Contains("test");
```

**Expected output:**

```
Func<string, bool> containsTest = s => s.Contains("test");
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is a closure in C#?

**A:** A closure is a lambda that captures variables from its enclosing scope; the captured variables are shared across calls.

**Q2:** Why do captured variables live longer than the enclosing method?

**A:** The compiler moves captured variables to a compiler-generated class on the heap, so they survive as long as the delegate referencing them.

**Q3:** What is the difference between expression lambdas and statement lambdas?

**A:** Expression lambdas (x => x + 1) are single expressions; statement lambdas ({ return x + 1; }) use braces and can have multiple statements.

**Q4:** Can lambdas be converted to expression trees?

**A:** Yes; assigning a lambda to Expression<Func<T>> stores it as a data structure, enabling translation to SQL or other query languages.

**Q5:** What is a common pitfall with closures in loops?

**A:** Capturing a loop variable in a lambda captures the variable itself, not its value; all lambdas share the final value unless you create a local copy.

**Q6:** When should you use a statement lambda over an expression lambda?

**A:** When the logic requires multiple statements, local variables, or complex control flow that cannot be expressed in a single expression.

**Q7:** What is a Func delegate?

**A:** A built-in generic delegate that represents a method with parameters and a return value, e.g., Func<int, string>.

**Q8:** What is an Action delegate?

**A:** A built-in generic delegate for methods that return void, e.g., Action<string> or Action<int, int>.

**Q9:** How does LINQ use lambdas?

**A:** LINQ operators like Where, Select, and OrderBy accept lambda expressions as predicates or projections, enabling declarative queries.

**Q10:** Can a lambda capture a ref or out parameter?

**A:** No; lambdas cannot capture ref or out parameters by design; you must assign the value to a local variable first.
