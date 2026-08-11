# Topic 3: Operators & Expressions

Operators let you perform calculations, compare values, combine conditions, and work with nulls. C# provides arithmetic (+, -, *, /, %), relational (==, !=, <, >), logical (&&, ||, !), and special operators like null coalescing (??) and pattern matching (is). Understanding operator precedence is essential for writing correct expressions.

## Learn From

Study the operator precedence table and practice with pattern matching and null-conditional operators.

- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/pattern-matching
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-coalescing-operator
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators

## Key Concepts

- Arithmetic operators (+, -, *, /, %) work on numeric types
- Comparison operators (==, !=, <, >, <=, >=) return bool
- Logical operators (&&, ||, !) combine boolean expressions
- Null coalescing ?? returns the left operand if it is not null, otherwise the right
- Null conditional ?. safely accesses members or indexes on null references
- Pattern matching with is checks types and extracts values
- The ternary operator ?: provides inline if-else expressions
- Compound assignment (+=, -=, *=, /=) combines operation with assignment
- Type-testing patterns include type patterns and constant patterns
- Property patterns let you match on nested properties

## Practice Problems & Solutions

### Problem 1

Write an expression that returns the remainder of 17 divided by 5.

```
17 % 5
```

**Expected output:**

```
17 % 5
```

**Learning points:** 

### Problem 2

Write a null coalescing expression that assigns name "default" if n is null.

```
string name = n ?? "default";
```

**Expected output:**

```
string name = n ?? "default";
```

**Learning points:** 

### Problem 3

Use the null conditional operator to safely get the length of a possibly null string.

```
int? len = s?.Length;
```

**Expected output:**

```
int? len = s?.Length;
```

**Learning points:** 

### Problem 4

Write a pattern matching expression that checks if obj is an int and prints it.

```
if (obj is int i) Console.WriteLine(i);
```

**Expected output:**

```
if (obj is int i) Console.WriteLine(i);
```

**Learning points:** 

### Problem 5

Write a ternary expression that sets x to 10 if y is greater than 5, else 0.

```
int x = y > 5 ? 10 : 0;
```

**Expected output:**

```
int x = y > 5 ? 10 : 0;
```

**Learning points:** 

### Problem 6

Write a compound assignment that doubles the value of count.

```
count *= 2;
```

**Expected output:**

```
count *= 2;
```

**Learning points:** 

### Problem 7

Write a switch expression that maps true to "Yes" and false to "No".

```
string result = val switch { true => "Yes", false => "No" };
```

**Expected output:**

```
string result = val switch { true => "Yes", false => "No" };
```

**Learning points:** 

### Problem 8

Write an expression that returns the larger of two integers a and b.

```
int max = a > b ? a : b;
```

**Expected output:**

```
int max = a > b ? a : b;
```

**Learning points:** 

### Problem 9

Use a relational pattern to check if a temperature is between 20 and 30 inclusive.

```
if (temp is >= 20 and <= 30) Console.WriteLine("Comfortable");
```

**Expected output:**

```
if (temp is >= 20 and <= 30) Console.WriteLine("Comfortable");
```

**Learning points:** 

### Problem 10

Write code that uses the ??= operator to assign a value only if the variable is null.

```
list ??= new List<string>();
```

**Expected output:**

```
list ??= new List<string>();
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the precedence order of arithmetic vs comparison vs logical operators?

**A:** Arithmetic (* / %) have highest precedence, then relational (< > == !=), then logical AND (&&), then logical OR (||), then assignment (= += ??=).

**Q2:** What does the ??= operator do?

**A:** It assigns the right-hand value to the left-hand variable only if the variable is currently null.

**Q3:** How does the null conditional ?. differ from a normal member access?

**A:** ?. short-circuits; if the left operand is null, the entire expression evaluates to null instead of throwing NullReferenceException.

**Q4:** Can you use pattern matching to check multiple types in a switch expression?

**A:** Yes; each arm can use type patterns, constant patterns, or property patterns to match and extract values.

**Q5:** What is the difference between == and .Equals()?

**A:** == can be overloaded and may have different behavior for reference types; .Equals() is the virtual method on Object that compares values.

**Q6:** What does the 'is' operator do in pattern matching?

**A:** It checks if a value matches a pattern (type, constant, property, or relational) and optionally assigns the matched value to a variable.

**Q7:** Why does C# use short-circuit evaluation for && and ||?

**A:** The right side is only evaluated if needed; this prevents unnecessary computation and avoids side effects.

**Q8:** What is the difference between = and ==?

**A:** = is the assignment operator; == is the equality comparison operator.

**Q9:** Can you define custom operators in C#?

**A:** Yes, you can overload most operators using the operator keyword for user-defined types.

**Q10:** What does the 'and' keyword do in pattern matching?

**A:** It combines two patterns; both patterns must match for the combined pattern to succeed.
