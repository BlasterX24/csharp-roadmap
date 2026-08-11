# Topic 17: Regex in C#

The System.Text.RegularExpressions.Regex class provides powerful pattern matching and text manipulation. You define patterns with metacharacters, use Match and Matches to find results, and extract data with groups. Regex is useful for validation, parsing, and text transformation.

## Learn From

Study the Regex class API and common patterns for emails, URLs, and numeric validation.

- https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expressions
- https://learn.microsoft.com/en-us/dotnet/api/system.text.regularexpressions.regex
- https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference
- https://learn.microsoft.com/en-us/dotnet/standard/base-types/common-techniques

## Key Concepts

- Regex.Match returns the first match; Regex.Matches returns all matches
- Groups capture substrings matched by parenthesized parts of the pattern
- Named groups (?<name>...) let you extract values by name
- Quantifiers: * (zero or more), + (one or more), ? (zero or one), {n,m}
- Character classes: \d (digit), \w (word char), \s (whitespace), [abc]
- Anchors: ^ (start of string), $ (end of string), \b (word boundary)
- RegexOptions.IgnoreCase and RegexOptions.Multiline modify behavior
- Regex.Replace substitutes matched patterns with new text
- Regex.IsMatch checks if a pattern matches (bool)
- Compiled option improves performance for frequently used patterns

## Practice Problems & Solutions

### Problem 1

Check if a string matches the pattern for a valid email address.

```
bool valid = Regex.IsMatch(email, @"^[^\s@]+@[^\s@]+\.[^\s@]+$");
```

**Expected output:**

```
bool valid = Regex.IsMatch(email, @"^[^\s@]+@[^\s@]+\.[^\s@]+$");
```

**Learning points:** 

### Problem 2

Extract all digits from a string using Regex.Matches.

```
MatchCollection matches = Regex.Matches(input, @"\d+");
```

**Expected output:**

```
MatchCollection matches = Regex.Matches(input, @"\d+");
```

**Learning points:** 

### Problem 3

Use a named group to extract a date part from a string.

```
var match = Regex.Match(input, @"(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})"); string year = match.Groups["year"].Value;
```

**Expected output:**

```
var match = Regex.Match(input, @"(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})"); string year = match.Groups["year"].Value;
```

**Learning points:** 

### Problem 4

Replace all spaces in a string with hyphens using Regex.Replace.

```
string result = Regex.Replace(input, @"\s+", "-");
```

**Expected output:**

```
string result = Regex.Replace(input, @"\s+", "-");
```

**Learning points:** 

### Problem 5

Check if a string is a valid US phone number pattern (123-456-7890).

```
bool valid = Regex.IsMatch(phone, @"^\d{3}-\d{3}-\d{4}$");
```

**Expected output:**

```
bool valid = Regex.IsMatch(phone, @"^\d{3}-\d{3}-\d{4}$");
```

**Learning points:** 

### Problem 6

Find all URLs in a string using a regex pattern.

```
var urls = Regex.Matches(text, @"https?://[^\s]+", RegexOptions.IgnoreCase);
```

**Expected output:**

```
var urls = Regex.Matches(text, @"https?://[^\s]+", RegexOptions.IgnoreCase);
```

**Learning points:** 

### Problem 7

Use Regex.Split to split a string on commas or semicolons.

```
string[] parts = Regex.Split(input, @"[,;]+");
```

**Expected output:**

```
string[] parts = Regex.Split(input, @"[,;]+");
```

**Learning points:** 

### Problem 8

Match a string that starts with a capital letter followed by lowercase letters.

```
bool match = Regex.IsMatch(input, @"^[A-Z][a-z]+$");
```

**Expected output:**

```
bool match = Regex.IsMatch(input, @"^[A-Z][a-z]+$");
```

**Learning points:** 

### Problem 9

Extract the first group value from a match.

```
string val = Regex.Match(input, @"(\d+)").Groups[1].Value;
```

**Expected output:**

```
string val = Regex.Match(input, @"(\d+)").Groups[1].Value;
```

**Learning points:** 

### Problem 10

Use Regex with IgnoreCase and Multiline options.

```
var match = Regex.Match(input, @"^hello$", RegexOptions.IgnoreCase | RegexOptions.Multiline);
```

**Expected output:**

```
var match = Regex.Match(input, @"^hello$", RegexOptions.IgnoreCase | RegexOptions.Multiline);
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between Match and Matches?

**A:** Match returns a single Match object for the first match; Matches returns a MatchCollection containing all non-overlapping matches.

**Q2:** How do named groups work?

**A:** The syntax (?<name>pattern) creates a named group; access its value with match.Groups["name"].Value.

**Q3:** What is the difference between \d and [0-9]?

**A:** They are equivalent; \d is a shorthand character class for digits 0-9.

**Q4:** When should you use RegexOptions.Compiled?

**A:** When the regex is used frequently and performance is critical; it pre-compiles the pattern to IL for faster execution.

**Q5:** What is the difference between Regex.IsMatch and Match.Success?

**A:** Regex.IsMatch is a static method that returns bool; Match.Success is a property on a Match object indicating whether a match was found.

**Q6:** How do you escape special characters in a regex?

**A:** Use \ before special characters like . * + ? ^ $ ( ) [ ] { } |, or use Regex.Escape().

**Q7:** What does the ? quantifier mean?

**A:** It makes the preceding element optional (zero or one occurrence).

**Q8:** What is a lazy vs greedy quantifier?

**A:** Greedy quantifiers (* + ?) match as much as possible; lazy quantifiers (*? +? ??) match as little as possible.

**Q9:** What does \b match?

**A:** A word boundary—the position between a word character and a non-word character.

**Q10:** Can you use regex with async code?

**A:** Regex operations are synchronous and CPU-bound; wrap them in Task.Run for async contexts.
