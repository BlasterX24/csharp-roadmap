# Topic 14: Exception Handling

Exception handling lets you catch and respond to runtime errors gracefully. The try/catch/finally pattern isolates code that might fail, catches specific exceptions, and guarantees cleanup in finally blocks. Custom exceptions carry domain-specific information. The using statement ensures deterministic disposal of resources.

## Learn From

Study the exception handling reference, best practices for catching exceptions, and the using declaration.

- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/try-catch-finally
- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/creating-and-throwing-exceptions
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/using-statement

## Key Concepts

- try wraps code that might throw an exception
- catch handles specific exception types; multiple catch blocks can handle different types
- finally executes regardless of whether an exception was thrown or caught
- throw raises an exception; throw preserves the original stack trace in catch
- Exception.Message contains the error description; Exception.StackTrace has the call stack
- Custom exceptions inherit from Exception and carry domain-specific data
- using ensures IDisposable objects are disposed even if an exception occurs
- using declaration (C# 8+) uses a scoped using without braces
- NullReferenceException, ArgumentException, and InvalidOperationException are common exceptions
- Exception filters with when let you add conditions to catch blocks

## Practice Problems & Solutions

### Problem 1

Write a try/catch that catches DivideByZeroException and prints the error.

```
try { int r = 10 / 0; } catch (DivideByZeroException ex) { Console.WriteLine(ex.Message); }
```

**Expected output:**

```
try { int r = 10 / 0; } catch (DivideByZeroException ex) { Console.WriteLine(ex.Message); }
```

**Learning points:** 

### Problem 2

Write a try/finally block that closes a file in the finally.

```
try { /* work */ } finally { File.Close(); }
```

**Expected output:**

```
try { /* work */ } finally { File.Close(); }
```

**Learning points:** 

### Problem 3

Throw an ArgumentException with a message.

```
throw new ArgumentException("Invalid name", nameof(name));
```

**Expected output:**

```
throw new ArgumentException("Invalid name", nameof(name));
```

**Learning points:** 

### Problem 4

Create a custom exception class called OrderNotFoundException.

```
class OrderNotFoundException : Exception { public OrderNotFoundException(string msg) : base(msg) { } }
```

**Expected output:**

```
class OrderNotFoundException : Exception { public OrderNotFoundException(string msg) : base(msg) { } }
```

**Learning points:** 

### Problem 5

Use a using statement to read all text from a file.

```
using (var sr = new StreamReader(path)) { string content = sr.ReadToEnd(); }
```

**Expected output:**

```
using (var sr = new StreamReader(path)) { string content = sr.ReadToEnd(); }
```

**Learning points:** 

### Problem 6

Use a using declaration (C# 8+) for a file stream.

```
using var fs = File.OpenRead(path);
```

**Expected output:**

```
using var fs = File.OpenRead(path);
```

**Learning points:** 

### Problem 7

Catch multiple exception types in order from most to least specific.

```
try { /* code */ } catch (InvalidOperationException ex) { } catch (Exception ex) { }
```

**Expected output:**

```
try { /* code */ } catch (InvalidOperationException ex) { } catch (Exception ex) { }
```

**Learning points:** 

### Problem 8

Use a when filter to catch only exceptions with a specific HRESULT.

```
catch (COMException ex) when (ex.ErrorCode == -2147024809) { }
```

**Expected output:**

```
catch (COMException ex) when (ex.ErrorCode == -2147024809) { }
```

**Learning points:** 

### Problem 9

Rethrow an exception preserving the original stack trace.

```
catch (Exception) { throw; }
```

**Expected output:**

```
catch (Exception) { throw; }
```

**Learning points:** 

### Problem 10

Use try/catch with async code and await.

```
try { await Task.Run(() => RiskyOperation()); } catch (Exception ex) { Console.WriteLine(ex.Message); }
```

**Expected output:**

```
try { await Task.Run(() => RiskyOperation()); } catch (Exception ex) { Console.WriteLine(ex.Message); }
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** Why should you catch specific exceptions instead of Exception?

**A:** Catching specific exceptions prevents accidentally handling unrelated errors and makes debugging easier.

**Q2:** What is the difference between throw and throw ex?

**A:** throw preserves the original stack trace; throw ex resets the stack trace to the current location, losing debugging information.

**Q3:** What does the finally block guarantee?

**A:** It executes whether or not an exception was thrown or caught, making it ideal for cleanup code.

**Q4:** When should you create a custom exception?

**A:** When you need to convey domain-specific error information that standard exceptions do not carry.

**Q5:** What is the using statement?

**A:** It ensures that an IDisposable object is disposed when the block exits, even if an exception occurs.

**Q6:** Can you have multiple catch blocks?

**A:** Yes; you can have multiple catch blocks, each handling a different exception type, ordered from most specific to most general.

**Q7:** What is Exception.InnerException?

**A:** It provides access to the original exception that caused the current exception, forming an exception chain.

**Q8:** What is the difference between Exception.Data and Exception.Message?

**A:** Message is a string description of the error; Data is an IDictionary for arbitrary key-value pairs of diagnostic information.

**Q9:** Why is catching exceptions control flow considered bad practice?

**A:** Exceptions are expensive and should signal unexpected errors; use conditional checks (if) for expected conditions.

**Q10:** How do you implement IDisposable with using?

**A:** Implement a Dispose method that cleans up resources; using calls Dispose when the block exits.
