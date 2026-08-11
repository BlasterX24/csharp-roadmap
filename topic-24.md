# Topic 24: Memory & Performance

Understanding memory management in .NET helps you write performant applications. Span<T> provides a type-safe view over contiguous memory without allocation. stackalloc allocates on the stack for short-lived buffers. ArrayPool<T> reuses arrays to reduce GC pressure. BenchmarkDotNet measures performance accurately.

## Learn From

Study Span<T>, stackalloc, ArrayPool, and BenchmarkDotNet for performance optimization.

- https://learn.microsoft.com/en-us/dotnet/api/system.span-1
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/stackalloc
- https://learn.microsoft.com/en-us/dotnet/api/system.buffers.arraypool-1
- https://benchmarkdotnet.org/

## Key Concepts

- Span<T> is a ref struct that represents a contiguous region of memory
- stackalloc allocates memory on the stack instead of the heap
- ArrayPool<T> provides reusable array buffers to minimize allocations
- BenchmarkDotNet provides accurate, statistical performance measurements
- ValueTask avoids Task allocation when the result is synchronous
- String interpolation handlers optimize string creation in .NET 6+
- ref returns and ref locals avoid copying structs
- Memory<T> is a heap-friendly alternative to Span<T> for async scenarios
- Pooling reduces GC collections and improves throughput
- Use Array.Empty<T>() instead of new T[0] to avoid allocations

## Practice Problems & Solutions

### Problem 1

Create a Span<int> from an array.

```
Span<int> span = arr.AsSpan();
```

**Expected output:**

```
Span<int> span = arr.AsSpan();
```

**Learning points:** 

### Problem 2

Use stackalloc to allocate a buffer of 128 bytes on the stack.

```
Span<byte> buffer = stackalloc byte[128];
```

**Expected output:**

```
Span<byte> buffer = stackalloc byte[128];
```

**Learning points:** 

### Problem 3

Get a shared array from ArrayPool<int>.

```
int[] array = ArrayPool<int>.Shared.Rent(1024);
```

**Expected output:**

```
int[] array = ArrayPool<int>.Shared.Rent(1024);
```

**Learning points:** 

### Problem 4

Return an array to the pool after use.

```
ArrayPool<int>.Shared.Return(array);
```

**Expected output:**

```
ArrayPool<int>.Shared.Return(array);
```

**Learning points:** 

### Problem 5

Slice a Span to get a sub-range.

```
Span<int> slice = span.Slice(2, 5);
```

**Expected output:**

```
Span<int> slice = span.Slice(2, 5);
```

**Learning points:** 

### Problem 6

Use MemoryMarshal to read a struct from a byte span.

```
MyStruct s = MemoryMarshal.Read<MyStruct>(byteSpan);
```

**Expected output:**

```
MyStruct s = MemoryMarshal.Read<MyStruct>(byteSpan);
```

**Learning points:** 

### Problem 7

Use ref return to avoid copying a struct.

```
public ref int GetRef() => ref _field;
```

**Expected output:**

```
public ref int GetRef() => ref _field;
```

**Learning points:** 

### Problem 8

Create a ValueTask that returns a cached result.

```
ValueTask<int> GetCachedAsync(int id) => new ValueTask<int>(cachedValue);
```

**Expected output:**

```
ValueTask<int> GetCachedAsync(int id) => new ValueTask<int>(cachedValue);
```

**Learning points:** 

### Problem 9

Use Array.Empty<T>() to avoid allocating an empty array.

```
return Array.Empty<string>();
```

**Expected output:**

```
return Array.Empty<string>();
```

**Learning points:** 

### Problem 10

Write a BenchmarkDotNet benchmark class.

```
[MemoryDiagnoser] public class MyBenchmark { [Benchmark] public void Method() { } }
```

**Expected output:**

```
[MemoryDiagnoser] public class MyBenchmark { [Benchmark] public void Method() { } }
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is Span<T> and why is it important?

**A:** Span<T> is a ref struct that provides a type-safe view over memory without heap allocation, reducing GC pressure for buffer operations.

**Q2:** What are the limitations of Span<T>?

**A:** It is a ref struct and cannot be used as a field, in async methods, or as a generic type parameter.

**Q3:** When should you use stackalloc?

**A:** For short-lived, small buffers (typically under 1KB) where stack allocation avoids heap pressure.

**Q4:** What is ArrayPool<T>?

**A:** A pool of reusable arrays that reduces allocation and garbage collection overhead for temporary buffers.

**Q5:** What is ValueTask vs Task?

**A:** ValueTask avoids heap allocation when the result is available synchronously; use Task for methods that are always async.

**Q6:** How does BenchmarkDotNet work?

**A:** It runs methods multiple times with statistical analysis, warm-up iterations, and memory diagnostics for accurate measurements.

**Q7:** What is Memory<T>?

**A:** A heap-friendly alternative to Span<T> that can be stored in fields and used in async scenarios.

**Q8:** What is the [MemoryDiagnoser] attribute?

**A:** It tells BenchmarkDotNet to report memory allocations per operation in benchmark results.

**Q9:** How do you avoid boxing with structs?

**A:** Use generic constraints, avoid interface dispatch, and prefer ref returns to prevent value type copying.

**Q10:** What is string interpolation handlers in .NET 6+?

**A:** They optimize string interpolation by avoiding intermediate string allocations when using ISpanFormattable.
