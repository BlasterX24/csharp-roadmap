# Topic 4: Strings

Strings in C# are immutable sequences of characters. The String class provides methods for searching, splitting, replacing, and formatting. String interpolation ($"") lets you embed expressions directly. StringBuilder is used for efficient concatenation in loops. Regular expressions via the Regex class enable complex pattern matching.

## Learn From

Explore the String class reference, string interpolation docs, and StringBuilder for performance-sensitive concatenation.

- https://learn.microsoft.com/en-us/dotnet/csharp/how-to/strings-csharp
- https://learn.microsoft.com/en-us/dotnet/fundamentals/runtime-libraries/system-string
- https://learn.microsoft.com/en-us/dotnet/fundamentals/runtime-libraries/system-text-stringbuilder
- https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expressions

## Key Concepts

- Strings are immutable; every modification creates a new string
- String interpolation with $"" embeds expressions inside { }
- StringBuilder is mutable and efficient for building strings in loops
- Common string methods: Contains, StartsWith, EndsWith, IndexOf, Replace, Split, Trim
- string.Join combines an array/collection into a single string with a separator
- string.Format with numbered placeholders {0} {1} formats output
- Null and empty strings are different; use string.IsNullOrEmpty() to check both
- Verbatim strings @"..." preserve backslashes and allow multi-line text
- Raw string literals """...""" are new in C# 11 for multi-line raw text
- String comparison uses StringComparison enum for culture-aware or ordinal checks

## Practice Problems & Solutions

### Problem 1

Use string interpolation to print "Hello, Alice! You are 30 years old."

**Solution:**

```
string msg = $"Hello, {name}! You are {age} years old.";
```

**Expected output:**

```
string msg = $"Hello, {name}! You are {age} years old.";
```

**Learning points:** 

### Problem 2

Write code that splits a CSV string "a,b,c" into an array.

**Solution:**

```
string[] parts = "a,b,c".Split(',');
```

**Expected output:**

```
string[] parts = "a,b,c".Split(',');
```

**Learning points:** 

### Problem 3

Use StringBuilder to build "aaa" by appending "a" three times.

**Solution:**

```
var sb = new System.Text.StringBuilder(); for (int i = 0; i < 3; i++) sb.Append("a"); string result = sb.ToString();
```

**Expected output:**

```
var sb = new System.Text.StringBuilder(); for (int i = 0; i < 3; i++) sb.Append("a"); string result = sb.ToString();
```

**Learning points:** 

### Problem 4

Check if a string is null or empty.

**Solution:**

```
bool empty = string.IsNullOrEmpty(input);
```

**Expected output:**

```
bool empty = string.IsNullOrEmpty(input);
```

**Learning points:** 

### Problem 5

Replace all spaces in a string with underscores.

**Solution:**

```
string result = input.Replace(" ", "_");
```

**Expected output:**

```
string result = input.Replace(" ", "_");
```

**Learning points:** 

### Problem 6

Convert a string to lowercase and remove leading/trailing whitespace.

**Solution:**

```
string result = input.ToLower().Trim();
```

**Expected output:**

```
string result = input.ToLower().Trim();
```

**Learning points:** 

### Problem 7

Find the index of the first occurrence of "world" in a string.

**Solution:**

```
int idx = "hello world".IndexOf("world");
```

**Expected output:**

```
int idx = "hello world".IndexOf("world");
```

**Learning points:** 

### Problem 8

Join an array of strings with a comma separator.

**Solution:**

```
string csv = string.Join(",", new[] { "a", "b", "c" });
```

**Expected output:**

```
string csv = string.Join(",", new[] { "a", "b", "c" });
```

**Learning points:** 

### Problem 9

Use a verbatim string to assign a path with backslashes.

**Solution:**

```
string path = @"C:\Users\Alice\Documents";
```

**Expected output:**

```
string path = @"C:\Users\Alice\Documents";
```

**Learning points:** 

### Problem 10

Check if a string starts with "http" using case-insensitive comparison.

**Solution:**

```
bool ok = url.StartsWith("http", StringComparison.OrdinalIgnoreCase);
```

**Expected output:**

```
bool ok = url.StartsWith("http", StringComparison.OrdinalIgnoreCase);
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** Why are strings immutable in C#?

**A:** Immutability ensures thread safety, enables string interning, and simplifies hash code computation for dictionary keys.

**Q2:** When should you use StringBuilder over concatenation?

**A:** Use StringBuilder when building strings in loops or with many modifications; each + concatenation creates a new string, while StringBuilder mutates a buffer.

**Q3:** What is the difference between string.Empty and ""?

**A:** They are equivalent; both represent a zero-length string. string.Empty is more readable and avoids allocation of a string literal.

**Q4:** How do you perform a case-insensitive search in a string?

**A:** Use StringComparison.OrdinalIgnoreCase with methods like Contains, IndexOf, or StartsWith.

**Q5:** What is string interpolation's performance impact?

**A:** It is syntactic sugar that the compiler converts to string.Format calls; for tight loops, StringBuilder is still preferred.

**Q6:** What does the @ prefix do in a string literal?

**A:** It creates a verbatim string where backslashes are treated as literal characters and line breaks are preserved.

**Q7:** How do you convert a char array back to a string?

**A:** Use new string(charArray) or string.Concat(charArray).

**Q8:** What is the difference between Replace and Substring?

**A:** Replace swaps all occurrences of a pattern with a replacement; Substring extracts a portion of the string by index and length.

**Q9:** Can you modify a string in place?

**A:** No; strings are immutable. You must create a new string or use StringBuilder to build text incrementally.

**Q10:** What does StringComparison.Ordinal do?

**A:** It performs a byte-by-byte comparison of the string characters, which is fast but culture-unaware.
