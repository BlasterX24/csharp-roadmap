# Topic 11: LINQ

LINQ (Language Integrated Query) provides a unified syntax for querying data from any source—arrays, lists, databases, XML. It offers two styles: method syntax (fluent) using extension methods like Where, Select, OrderBy, and query syntax using from, where, orderby, select keywords. Both compile to the same IL.

## Learn From

Start with the LINQ overview, then practice converting between method and query syntax.

- https://learn.microsoft.com/en-us/dotnet/linq/
- https://learn.microsoft.com/en-us/dotnet/csharp/linq/write-linq-queries
- https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators
- https://learn.microsoft.com/en-us/dotnet/csharp/linq/method-syntax-vs-query-syntax

## Key Concepts

- Where filters elements based on a predicate
- Select projects elements into a new form
- OrderBy and OrderByDescending sort elements
- GroupBy groups elements by a key
- Sum, Count, Average aggregate numeric values
- First, Last, Single retrieve individual elements
- Any and All test conditions across collections
- Distinct removes duplicates
- Join pairs elements from two sequences based on matching keys
- Deferred execution means queries are not evaluated until enumerated

## Practice Problems & Solutions

### Problem 1

Use LINQ to filter numbers greater than 5 from an array.

**Solution:**

```
var result = arr.Where(x => x > 5);
```

**Expected output:**

```
var result = arr.Where(x => x > 5);
```

**Learning points:** 

### Problem 2

Use Select to square each number in an int array.

**Solution:**

```
var squares = arr.Select(x => x * x);
```

**Expected output:**

```
var squares = arr.Select(x => x * x);
```

**Learning points:** 

### Problem 3

Order a string array alphabetically using LINQ.

**Solution:**

```
var sorted = arr.OrderBy(s => s);
```

**Expected output:**

```
var sorted = arr.OrderBy(s => s);
```

**Learning points:** 

### Problem 4

Group numbers by whether they are even or odd.

**Solution:**

```
var groups = arr.GroupBy(x => x % 2 == 0 ? "Even" : "Odd");
```

**Expected output:**

```
var groups = arr.GroupBy(x => x % 2 == 0 ? "Even" : "Odd");
```

**Learning points:** 

### Problem 5

Count how many strings in an array start with "a".

**Solution:**

```
int count = arr.Count(s => s.StartsWith("a"));
```

**Expected output:**

```
int count = arr.Count(s => s.StartsWith("a"));
```

**Learning points:** 

### Problem 6

Use LINQ query syntax to select names longer than 3 characters.

**Solution:**

```
var result = from n in names where n.Length > 3 select n;
```

**Expected output:**

```
var result = from n in names where n.Length > 3 select n;
```

**Learning points:** 

### Problem 7

Use First to get the first element greater than 10.

**Solution:**

```
int first = arr.First(x => x > 10);
```

**Expected output:**

```
int first = arr.First(x => x > 10);
```

**Learning points:** 

### Problem 8

Use Any to check if any element is negative.

**Solution:**

```
bool hasNegative = arr.Any(x => x < 0);
```

**Expected output:**

```
bool hasNegative = arr.Any(x => x < 0);
```

**Learning points:** 

### Problem 9

Use Sum to total all elements in an int array.

**Solution:**

```
int total = arr.Sum();
```

**Expected output:**

```
int total = arr.Sum();
```

**Learning points:** 

### Problem 10

Use Distinct to remove duplicate integers from a list.

**Solution:**

```
var unique = list.Distinct();
```

**Expected output:**

```
var unique = list.Distinct();
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is deferred execution in LINQ?

**A:** The query is not evaluated when defined; it is executed when enumerated (e.g., in a foreach), allowing lazy evaluation.

**Q2:** What forces immediate execution?

**A:** Methods like ToList(), ToArray(), Count(), First(), and Sum() force the query to execute immediately.

**Q3:** What is the difference between First and FirstOrDefault?

**A:** First throws InvalidOperationException if no element matches; FirstOrDefault returns default(T) instead.

**Q4:** How does GroupBy work?

**A:** It groups elements by a key selector and returns an IEnumerable<IGrouping<TKey, TElement>> where each group has a Key and elements.

**Q5:** What is the difference between method syntax and query syntax?

**A:** Method syntax uses extension methods (Where, Select); query syntax uses SQL-like keywords (from, where, select). They compile to the same code.

**Q6:** How do you flatten a collection of collections?

**A:** Use SelectMany or query syntax with multiple from clauses.

**Q7:** What does the AsEnumerable() method do?

**A:** It returns the source as IEnumerable<T>, switching to LINQ to Objects from a more specific provider like IQueryable<T>.

**Q8:** Can you chain multiple LINQ operators?

**A:** Yes; LINQ operators return IEnumerable<T>, so you can chain Where, Select, OrderBy, etc. in a fluent pipeline.

**Q9:** What is the difference between All and Any?

**A:** All returns true if every element satisfies the predicate; Any returns true if at least one element satisfies it.

**Q10:** How do you get the maximum value with LINQ?

**A:** Use arr.Max() or arr.Max(x => x.Property) to find the maximum element or maximum projected value.
