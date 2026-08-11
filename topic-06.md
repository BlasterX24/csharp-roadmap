# Topic 6: Control Flow

Control flow determines the order in which statements execute. C# provides conditional statements (if, else, switch), iteration statements (for, foreach, while, do-while), and jump statements (break, continue, return, goto). Pattern matching in switch expressions adds powerful type-based dispatch.

## Learn From

Review the control flow statements reference and practice with pattern matching in switch expressions.

- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/jump-statements
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/switch

## Key Concepts

- if/else checks a bool condition and branches execution
- switch matches a value against constant or pattern cases
- switch expressions return a value from pattern-matching arms
- for loops use init; condition; iterator for counted iteration
- foreach iterates over any IEnumerable or IEnumerable<T>
- while evaluates its condition before each iteration
- do-while evaluates its condition after each iteration
- break exits the nearest enclosing loop or switch
- continue skips to the next iteration of the nearest enclosing loop
- throw returns from a method and signals an error

## Practice Problems & Solutions

### Problem 1

Write an if/else that prints "positive" if n > 0, else "non-positive".

**Solution:**

```
if (n > 0) Console.WriteLine("positive"); else Console.WriteLine("non-positive");
```

**Expected output:**

```
if (n > 0) Console.WriteLine("positive"); else Console.WriteLine("non-positive");
```

**Learning points:** 

### Problem 2

Write a for loop that prints numbers 1 through 5.

**Solution:**

```
for (int i = 1; i <= 5; i++) Console.WriteLine(i);
```

**Expected output:**

```
for (int i = 1; i <= 5; i++) Console.WriteLine(i);
```

**Learning points:** 

### Problem 3

Write a foreach loop that prints each string in a string array.

**Solution:**

```
foreach (var s in arr) Console.WriteLine(s);
```

**Expected output:**

```
foreach (var s in arr) Console.WriteLine(s);
```

**Learning points:** 

### Problem 4

Write a while loop that decrements a counter until it reaches 0.

**Solution:**

```
while (count > 0) { Console.WriteLine(count); count--; }
```

**Expected output:**

```
while (count > 0) { Console.WriteLine(count); count--; }
```

**Learning points:** 

### Problem 5

Write a switch expression that maps 1 to "One", 2 to "Two", and default to "Other".

**Solution:**

```
string result = num switch { 1 => "One", 2 => "Two", _ => "Other" };
```

**Expected output:**

```
string result = num switch { 1 => "One", 2 => "Two", _ => "Other" };
```

**Learning points:** 

### Problem 6

Write code that breaks out of a foreach loop when a negative number is found.

**Solution:**

```
foreach (var n in nums) { if (n < 0) break; Console.WriteLine(n); }
```

**Expected output:**

```
foreach (var n in nums) { if (n < 0) break; Console.WriteLine(n); }
```

**Learning points:** 

### Problem 7

Write a do-while loop that asks for input until "quit" is entered.

**Solution:**

```
string input; do { input = Console.ReadLine(); } while (input != "quit");
```

**Expected output:**

```
string input; do { input = Console.ReadLine(); } while (input != "quit");
```

**Learning points:** 

### Problem 8

Write an if/else if/else chain that categorizes a score into A, B, C, or F.

**Solution:**

```
if (score >= 90) Console.WriteLine("A"); else if (score >= 80) Console.WriteLine("B"); else if (score >= 70) Console.WriteLine("C"); else Console.WriteLine("F");
```

**Expected output:**

```
if (score >= 90) Console.WriteLine("A"); else if (score >= 80) Console.WriteLine("B"); else if (score >= 70) Console.WriteLine("C"); else Console.WriteLine("F");
```

**Learning points:** 

### Problem 9

Write a switch statement that prints the day name for a DayOfWeek enum value.

**Solution:**

```
switch (day) { case DayOfWeek.Monday: Console.WriteLine("Monday"); break; case DayOfWeek.Friday: Console.WriteLine("Friday"); break; default: Console.WriteLine("Other day"); break; }
```

**Expected output:**

```
switch (day) { case DayOfWeek.Monday: Console.WriteLine("Monday"); break; case DayOfWeek.Friday: Console.WriteLine("Friday"); break; default: Console.WriteLine("Other day"); break; }
```

**Learning points:** 

### Problem 10

Write a continue statement that skips odd numbers in a for loop from 0 to 9.

**Solution:**

```
for (int i = 0; i < 10; i++) { if (i % 2 != 0) continue; Console.WriteLine(i); }
```

**Expected output:**

```
for (int i = 0; i < 10; i++) { if (i % 2 != 0) continue; Console.WriteLine(i); }
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between switch statement and switch expression?

**A:** A switch statement executes statements for each case; a switch expression returns a value and uses pattern-matching arms with => syntax.

**Q2:** Can you use string values in a switch expression?

**A:** Yes; switch expressions support constant patterns for strings and other types that implement equality comparison.

**Q3:** What does the _ (discard) mean in a switch expression?

**A:** It acts as the default case, matching any value not covered by earlier arms.

**Q4:** When should you use a do-while loop instead of while?

**A:** When you need the body to execute at least once before checking the condition, such as menu prompts or input validation.

**Q5:** What is the difference between break and continue?

**A:** break exits the loop entirely; continue skips to the next iteration without finishing the current iteration.

**Q6:** Can you nest switch statements?

**A:** Yes; you can nest any control flow statement inside another, though deep nesting is often better refactored into methods.

**Q7:** What is a fall-through in switch and does C# allow it?

**A:** Fall-through means executing a case without a break; C# does not allow it—every case must end with break, return, throw, or goto.

**Q8:** What is the pattern matching _ in if statements?

**A:** The discard pattern _ matches any value and is used in switch expressions as the default case.

**Q9:** Can foreach iterate over any collection type?

**A:** foreach works on any type that implements IEnumerable or IEnumerable<T>, or has a GetEnumerator method.

**Q10:** What happens if a for loop condition is always true?

**A:** The loop runs forever (infinite loop); you must use break or return to exit it.
