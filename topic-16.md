# Topic 16: Async/Await

Async/await lets you write asynchronous code that reads like synchronous code while keeping the thread responsive. A Task represents an asynchronous operation. async marks a method as asynchronous; await pauses execution until a Task completes. CancellationToken cooperatively cancels long-running operations. Task.WhenAll and Task.WhenAny enable parallel operations.

## Learn From

Study the async/await fundamentals, Task-based patterns, and CancellationToken for cooperative cancellation.

- https://learn.microsoft.com/en-us/dotnet/csharp/async/
- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/async/
- https://learn.microsoft.com/en-us/dotnet/api/system.threading.cancellationtoken
- https://learn.microsoft.com/en-us/dotnet/csharp/async-in-aspnet-core

## Key Concepts

- async methods return Task or Task<T> (or void for event handlers)
- await suspends the method until the Task completes, then resumes
- ConfigureAwait(false) avoids capturing the synchronization context
- Task.Run offloads CPU-bound work to the thread pool
- Task.WhenAll waits for all tasks to complete
- Task.WhenAny completes when any one task finishes
- CancellationToken enables cooperative cancellation with IsCancellationRequested
- CancellationTokenSource creates and manages the token
- ValueTask is a performance-optimized alternative to Task for hot paths
- Exception handling in async uses normal try/catch around await calls

## Practice Problems & Solutions

### Problem 1

Write an async method that returns Task<string> with a 1-second delay.

```
async Task<string> GetDelayedAsync() { await Task.Delay(1000); return "done"; }
```

**Expected output:**

```
async Task<string> GetDelayedAsync() { await Task.Delay(1000); return "done"; }
```

**Learning points:** 

### Problem 2

Await a Task<int> and store the result.

```
int result = await GetNumberAsync();
```

**Expected output:**

```
int result = await GetNumberAsync();
```

**Learning points:** 

### Problem 3

Run two async operations in parallel using Task.WhenAll.

```
var task1 = GetAsync("a"); var task2 = GetAsync("b"); await Task.WhenAll(task1, task2);
```

**Expected output:**

```
var task1 = GetAsync("a"); var task2 = GetAsync("b"); await Task.WhenAll(task1, task2);
```

**Learning points:** 

### Problem 4

Cancel an async operation using CancellationToken.

```
var cts = new CancellationTokenSource(); await LongRunningAsync(cts.Token);
```

**Expected output:**

```
var cts = new CancellationTokenSource(); await LongRunningAsync(cts.Token);
```

**Learning points:** 

### Problem 5

Check for cancellation inside an async loop.

```
while (!token.IsCancellationRequested) { await Task.Delay(100); }
```

**Expected output:**

```
while (!token.IsCancellationRequested) { await Task.Delay(100); }
```

**Learning points:** 

### Problem 6

Use Task.Run to execute CPU-bound work asynchronously.

```
int result = await Task.Run(() => HeavyComputation());
```

**Expected output:**

```
int result = await Task.Run(() => HeavyComputation());
```

**Learning points:** 

### Problem 7

Use ConfigureAwait(false) to avoid deadlocks in library code.

```
await GetDataAsync().ConfigureAwait(false);
```

**Expected output:**

```
await GetDataAsync().ConfigureAwait(false);
```

**Learning points:** 

### Problem 8

Handle exceptions from an async method with try/catch.

```
try { await RiskyAsync(); } catch (Exception ex) { Console.WriteLine(ex.Message); }
```

**Expected output:**

```
try { await RiskyAsync(); } catch (Exception ex) { Console.WriteLine(ex.Message); }
```

**Learning points:** 

### Problem 9

Cancel a Task after a timeout using CancellationTokenSource.

```
var cts = new CancellationTokenSource(TimeSpan.FromSeconds(5)); await LongOpAsync(cts.Token);
```

**Expected output:**

```
var cts = new CancellationTokenSource(TimeSpan.FromSeconds(5)); await LongOpAsync(cts.Token);
```

**Learning points:** 

### Problem 10

Use Task.WhenAny to get the first completed result from multiple sources.

```
var winner = await Task.WhenAny(task1, task2); var result = await winner;
```

**Expected output:**

```
var winner = await Task.WhenAny(task1, task2); var result = await winner;
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What happens when you call an async method without await?

**A:** The method starts executing synchronously until the first await, then returns an incomplete Task; the caller gets the Task but may not wait for completion.

**Q2:** What is the difference between Task and ValueTask?

**A:** Task is a reference type that allocates on the heap; ValueTask is a struct optimized for scenarios where the result is often available synchronously.

**Q3:** Why use ConfigureAwait(false)?

**A:** It prevents capturing the SynchronizationContext, avoiding deadlocks in library code that does not need to resume on the original thread.

**Q4:** Can you await multiple tasks in parallel?

**A:** Yes; Task.WhenAll waits for all tasks; Task.WhenAny completes when any one finishes.

**Q5:** What is CancellationTokenSource?

**A:** It creates a CancellationToken and provides Cancel() to signal cancellation; it can also accept a timeout.

**Q6:** What is the difference between Task.Run and Task.Factory.StartNew?

**A:** Task.Run is a simpler, recommended API for offloading work; Task.Factory.StartNew offers more control over scheduling and options.

**Q7:** How do you handle exceptions from multiple parallel tasks?

**A:** Task.WhenAll throws AggregateException; use try/catch and inspect the InnerExceptions collection.

**Q8:** What is the async void problem?

**A:** async void methods cannot be awaited and exceptions cannot be caught; use async Task except for event handlers.

**Q9:** What is the synchronization context?

**A:** It determines which thread the continuation runs on; in UI apps it posts to the UI thread; ConfigureAwait(false) skips this.

**Q10:** How do you cancel a running Task?

**A:** Pass a CancellationToken to the async method; check IsCancellationRequested or call token.ThrowIfCancellationRequested().
