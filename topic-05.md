# Topic 5: Arrays & Collections

Arrays and collections store groups of values. Arrays have fixed size, while List<T> and Dictionary<K,V> grow dynamically. LINQ provides a declarative way to query, filter, and transform collections using method syntax (Where, Select, OrderBy) or query syntax (from ... where ... select).

## Learn From

Learn the Array and generic collection classes, then practice with LINQ to manipulate data efficiently.

- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/
- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generic-collections
- https://learn.microsoft.com/en-us/dotnet/csharp/linq/
- https://learn.microsoft.com/en-us/dotnet/api/system.linq

## Key Concepts

- Arrays are fixed-size, zero-indexed, and can be single or multidimensional
- List<T> is a generic, resizable array backed by an internal array
- Dictionary<K,V> stores key-value pairs with O(1) lookup
- Queue<T> is FIFO; Stack<T> is LIFO
- HashSet<T> stores unique elements with O(1) contains checks
- LINQ method syntax uses extension methods like .Where().Select()
- LINQ query syntax uses from, where, orderby, select keywords
- Array.Copy and Array.Resize manipulate array contents
- Collection initializers let you populate collections inline
- Index and Range operators ([^1], 0..3) simplify array slicing

## Practice Problems & Solutions

### Problem 1

Declare and initialize an integer array with values 1, 2, 3.

```
int[] arr = new int[] { 1, 2, 3 };
```

**Expected output:**

```
int[] arr = new int[] { 1, 2, 3 };
```

**Learning points:** 

### Problem 2

Add the number 4 to the end of a List<int> named nums.

```
nums.Add(4);
```

**Expected output:**

```
nums.Add(4);
```

**Learning points:** 

### Problem 3

Use LINQ to select only even numbers from an int array.

```
var evens = arr.Where(x => x % 2 == 0);
```

**Expected output:**

```
var evens = arr.Where(x => x % 2 == 0);
```

**Learning points:** 

### Problem 4

Use LINQ query syntax to order strings alphabetically.

```
var sorted = from s in names orderby s select s;
```

**Expected output:**

```
var sorted = from s in names orderby s select s;
```

**Learning points:** 

### Problem 5

Get the length of a string array.

```
int len = arr.Length;
```

**Expected output:**

```
int len = arr.Length;
```

**Learning points:** 

### Problem 6

Check if a Dictionary<string,int> contains a specific key.

```
bool exists = dict.ContainsKey("Alice");
```

**Expected output:**

```
bool exists = dict.ContainsKey("Alice");
```

**Learning points:** 

### Problem 7

Use LINQ to get the sum of all elements in an int array.

```
int total = arr.Sum();
```

**Expected output:**

```
int total = arr.Sum();
```

**Learning points:** 

### Problem 8

Convert a List<int> to an array.

```
int[] array = nums.ToArray();
```

**Expected output:**

```
int[] array = nums.ToArray();
```

**Learning points:** 

### Problem 9

Use the index operator to get the last element of an array.

```
int last = arr[^1];
```

**Expected output:**

```
int last = arr[^1];
```

**Learning points:** 

### Problem 10

Use the range operator to get the first three elements of an array.

```
int[] first3 = arr[0..3];
```

**Expected output:**

```
int[] first3 = arr[0..3];
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between an array and List<T>?

**A:** Arrays have fixed size; List<T> is a dynamic, resizable collection that internally uses an array and copies elements when capacity is exceeded.

**Q2:** How does Dictionary<K,V> handle hash collisions?

**A:** It uses chaining (linked lists per bucket) or open addressing depending on the .NET version; collisions degrade lookup from O(1) to O(n) in the worst case.

**Q3:** What is the difference between List<T>.Add and List<T>.Insert?

**A:** Add appends to the end; Insert places an element at a specific index, shifting subsequent elements.

**Q4:** How do you iterate over a Dictionary<string,int>?

**A:** Use foreach with KeyValuePair<string,int>, or iterate over dict.Keys or dict.Values directly.

**Q5:** What does LINQ's .Select() do?

**A:** It projects each element into a new form by applying a transform function, returning an IEnumerable of the projected type.

**Q6:** When should you use a HashSet<T>?

**A:** When you need fast O(1) membership checks and want to ensure uniqueness without storing duplicate values.

**Q7:** What is the difference between Queue<T> and Stack<T>?

**A:** Queue<T> is first-in-first-out (FIFO); Stack<T> is last-in-first-out (LIFO).

**Q8:** How do you sort an array in place?

**A:** Use Array.Sort(arr) or arr.Sort() for a List<T>.

**Q9:** What does the 'from' keyword do in LINQ query syntax?

**A:** It introduces a range variable that iterates over the source collection, similar to foreach.

**Q10:** How do you remove all elements matching a condition from a List<T>?

**A:** Use list.RemoveAll(predicate) which removes all elements for which the predicate returns true.
