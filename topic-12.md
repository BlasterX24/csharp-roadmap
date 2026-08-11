# Topic 12: Delegates & Events

Delegates are type-safe function pointers that reference methods. Action and Func are built-in generic delegates for common signatures. Events use delegates to implement the publish-subscribe pattern, allowing objects to notify subscribers when something happens. Multicast delegates support multiple method targets.

## Learn From

Study the delegate type, Action/Func signatures, and the event keyword for implementing observers.

- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/delegates/
- https://learn.microsoft.com/en-us/dotnet/api/system.action
- https://learn.microsoft.com/en-us/dotnet/api/system.func-1
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/event

## Key Concepts

- A delegate defines a method signature; any method matching the signature can be assigned
- Action<T> is a delegate that returns void with up to 16 parameters
- Func<T, TResult> is a delegate that returns a value with up to 16 parameters
- Events are delegates that can only be invoked from the declaring class
- The += operator subscribes to an event; -= unsubscribes
- Multicast delegates chain multiple method calls into one delegate instance
- EventHandler<T> is a standard delegate for .NET events
- Delegate.Combine and Delegate.Remove manage multicast chains
- Anonymous methods and lambdas simplify delegate instantiation
- Delegates enable callback patterns, strategy patterns, and LINQ queries

## Practice Problems & Solutions

### Problem 1

Declare a delegate int MathOp(int a, int b).

```
delegate int MathOp(int a, int b);
```

**Expected output:**

```
delegate int MathOp(int a, int b);
```

**Learning points:** 

### Problem 2

Assign a lambda to Action<string> that prints a message.

```
Action<string> print = msg => Console.WriteLine(msg);
```

**Expected output:**

```
Action<string> print = msg => Console.WriteLine(msg);
```

**Learning points:** 

### Problem 3

Create a Func<int, int, int> that returns the sum of two ints.

```
Func<int, int, int> add = (a, b) => a + b;
```

**Expected output:**

```
Func<int, int, int> add = (a, b) => a + b;
```

**Learning points:** 

### Problem 4

Define an event called OnClick using EventHandler.

```
public event EventHandler OnClick;
```

**Expected output:**

```
public event EventHandler OnClick;
```

**Learning points:** 

### Problem 5

Invoke an event safely by checking for null first.

```
OnClick?.Invoke(this, EventArgs.Empty);
```

**Expected output:**

```
OnClick?.Invoke(this, EventArgs.Empty);
```

**Learning points:** 

### Problem 6

Subscribe a method to an event using +=.

```
obj.OnClick += MyHandler;
```

**Expected output:**

```
obj.OnClick += MyHandler;
```

**Learning points:** 

### Problem 7

Create a multicast delegate by combining two Action delegates.

```
Action a = () => Console.WriteLine("A"); Action b = () => Console.WriteLine("B"); Action combined = a + b;
```

**Expected output:**

```
Action a = () => Console.WriteLine("A"); Action b = () => Console.WriteLine("B"); Action combined = a + b;
```

**Learning points:** 

### Problem 8

Pass a Func<int, bool> to a Filter method that returns matching elements.

```
IEnumerable<int> Filter(IEnumerable<int> source, Func<int, bool> predicate) => source.Where(predicate);
```

**Expected output:**

```
IEnumerable<int> Filter(IEnumerable<int> source, Func<int, bool> predicate) => source.Where(predicate);
```

**Learning points:** 

### Problem 9

Declare an event using EventHandler<T> with a custom EventArgs.

```
public event EventHandler<ChangedEventArgs> Changed;
```

**Expected output:**

```
public event EventHandler<ChangedEventArgs> Changed;
```

**Learning points:** 

### Problem 10

Unsubscribe from an event using -=.

```
obj.OnClick -= MyHandler;
```

**Expected output:**

```
obj.OnClick -= MyHandler;
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between a delegate and an event?

**A:** A delegate can be invoked, reassigned, and combined from anywhere; an event can only be invoked from the declaring class and subscribers can only += or -=.

**Q2:** Why use EventHandler instead of a custom delegate?

**A:** EventHandler is a standard .NET convention; it provides a consistent signature and works with EventArgs for event data.

**Q3:** What is a multicast delegate?

**A:** A delegate that holds references to multiple methods; invoking it calls all methods in order.

**Q4:** When should you use Action vs Func?

**A:** Use Action when the method returns void; use Func when it returns a value.

**Q5:** What happens if you invoke a delegate that references a disposed object?

**A:** It depends on the delegate chain; if one target throws, subsequent targets may not be called.

**Q6:** How do you prevent null delegate invocations?

**A:** Use the null-conditional operator: myDelegate?.Invoke(args);

**Q7:** Can events be invoked outside the declaring class?

**A:** No; the event keyword restricts invocation to the class that declared it; external code can only subscribe or unsubscribe.

**Q8:** What is the purpose of EventArgs?

**A:** It provides a base class for passing event-specific data to event handlers.

**Q9:** How do you make a delegate from a static method?

**A:** Assign the method name directly: Action print = MyClass.Print;

**Q10:** Can a delegate reference multiple methods?

**A:** Yes; using multicast delegates with + or +=, you chain multiple methods into one delegate.
