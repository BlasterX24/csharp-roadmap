# Topic 23: Secure Coding in C#

Secure coding prevents vulnerabilities like SQL injection, XSS, and secrets exposure. Parameterized queries prevent SQL injection. Input validation rejects malicious data. The Secret Manager and Azure Key Vault handle secrets securely. HTTPS, CORS, and authentication protect web applications.

## Learn From

Study OWASP Top 10, parameterized queries, and .NET security best practices.

- https://learn.microsoft.com/en-us/dotnet/standard/security/
- https://learn.microsoft.com/en-us/aspnet/core/security/
- https://learn.microsoft.com/en-us/dotnet/core/app-secrets
- https://learn.microsoft.com/en-us/azure/key-vault/

## Key Concepts

- Always use parameterized queries to prevent SQL injection
- Validate and sanitize all user input on the server side
- Use built-in validation attributes ([Required], [StringLength], [Range])
- Store secrets in Secret Manager, environment variables, or Key Vault, never in code
- Enable HTTPS and HSTS for all web applications
- Use Content Security Policy (CSP) to prevent XSS
- Hash passwords with PBKDF2, bcrypt, or Argon2, never MD5/SHA1
- Apply the principle of least privilege for database and file access
- Use anti-forgery tokens to prevent CSRF attacks
- Log security events without exposing sensitive data

## Practice Problems & Solutions

### Problem 1

Write a parameterized SQL query to prevent injection.

```
cmd.Parameters.AddWithValue("@name", inputName);
```

**Expected output:**

```
cmd.Parameters.AddWithValue("@name", inputName);
```

**Learning points:** 

### Problem 2

Validate an email input using [EmailAddress] attribute.

```
[EmailAddress] public string Email { get; set; }
```

**Expected output:**

```
[EmailAddress] public string Email { get; set; }
```

**Learning points:** 

### Problem 3

Store a secret using dotnet user-secrets.

```
dotnet user-secrets set "ApiKey" "mykey123"
```

**Expected output:**

```
dotnet user-secrets set "ApiKey" "mykey123"
```

**Learning points:** 

### Problem 4

Read a secret from configuration.

```
string key = config["ApiKey"];
```

**Expected output:**

```
string key = config["ApiKey"];
```

**Learning points:** 

### Problem 5

Hash a password with BCrypt.

```
string hash = BCrypt.Net.BCrypt.HashPassword(password);
```

**Expected output:**

```
string hash = BCrypt.Net.BCrypt.HashPassword(password);
```

**Learning points:** 

### Problem 6

Validate input length using [StringLength].

```
[StringLength(100, MinimumLength = 3)] public string Name { get; set; }
```

**Expected output:**

```
[StringLength(100, MinimumLength = 3)] public string Name { get; set; }
```

**Learning points:** 

### Problem 7

Use [Range] to validate a numeric input.

```
[Range(1, 100)] public int Quantity { get; set; }
```

**Expected output:**

```
[Range(1, 100)] public int Quantity { get; set; }
```

**Learning points:** 

### Problem 8

Enable CORS with a specific allowed origin.

```
builder.Services.AddCors(options => options.AddPolicy("Policy", policy => policy.WithOrigins("https://example.com")));
```

**Expected output:**

```
builder.Services.AddCors(options => options.AddPolicy("Policy", policy => policy.WithOrigins("https://example.com")));
```

**Learning points:** 

### Problem 9

Use [Authorize] to protect an API endpoint.

```
[Authorize] public IActionResult Secret() => Ok("secret");
```

**Expected output:**

```
[Authorize] public IActionResult Secret() => Ok("secret");
```

**Learning points:** 

### Problem 10

Sanitize HTML input to prevent XSS.

```
string safe = WebUtility.HtmlEncode(input);
```

**Expected output:**

```
string safe = WebUtility.HtmlEncode(input);
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is SQL injection and how do you prevent it?

**A:** SQL injection inserts malicious SQL via user input; prevent it with parameterized queries, stored procedures, and ORM frameworks.

**Q2:** Why is MD5 not recommended for password hashing?

**A:** MD5 is fast and vulnerable to rainbow table attacks; use PBKDF2, bcrypt, or Argon2 which are slow and salted.

**Q3:** What is the Secret Manager tool?

**A:** A development tool that stores sensitive data in a local JSON file outside the project, avoiding secrets in source control.

**Q4:** How does input validation prevent attacks?

**A:** It rejects malformed or malicious input before it reaches business logic, preventing injection and buffer overflow attacks.

**Q5:** What is CSRF and how do you prevent it?

**A:** CSRF tricks users into submitting unwanted requests; prevent it with anti-forgery tokens and SameSite cookies.

**Q6:** What is Content Security Policy (CSP)?

**A:** An HTTP header that restricts which resources (scripts, styles, images) can be loaded, preventing XSS.

**Q7:** Why should you never store secrets in source code?

**A:** They become visible in version control, log files, and decompiled assemblies; use secure storage instead.

**Q8:** What is the principle of least privilege?

**A:** Grant only the minimum permissions needed to perform a task, reducing the impact of a compromise.

**Q9:** How do you secure API communication?

**A:** Use HTTPS with TLS, validate JWT tokens, and implement proper authentication and authorization.

**Q10:** What is the difference between authentication and authorization?

**A:** Authentication verifies identity; authorization determines what an authenticated user is allowed to do.
