# Topic 25: Capstone Projects

The capstone projects combine everything you have learned—OOP, LINQ, async, file I/O, ASP.NET, security, and performance—into practical applications. Each project targets real-world scenarios and requires integrating multiple C# concepts.

## Learn From

Pick a project, plan the architecture, implement incrementally, and test thoroughly.

- https://learn.microsoft.com/en-us/dotnet/core/project-sdk/msbuild-project-overview
- https://learn.microsoft.com/en-us/dotnet/core/testing/
- https://learn.microsoft.com/en-us/aspnet/core/test/
- https://learn.microsoft.com/en-us/dotnet/core/docker/

## Key Concepts

- Design before coding: define interfaces, data models, and workflows
- Use dependency injection to decouple components
- Write unit tests alongside production code
- Implement proper error handling with try/catch and logging
- Use async/await for I/O-bound operations
- Apply security best practices: input validation, parameterized queries, secrets management
- Profile and optimize performance-critical paths
- Use LINQ for data transformation and querying
- Document your code with XML comments
- Containerize your application with Docker for deployment

## Practice Problems & Solutions

### Problem 1

Build a CLI file organizer that sorts files by extension using File I/O and LINQ.

```
var files = Directory.GetFiles(sourceDir); var grouped = files.GroupBy(f => Path.GetExtension(f));
```

**Expected output:**

```
var files = Directory.GetFiles(sourceDir); var grouped = files.GroupBy(f => Path.GetExtension(f));
```

**Learning points:** 

### Problem 2

Create a REST API with ASP.NET that manages a todo list with CRUD operations.

```
app.MapGet("/todos", () => todos); app.MapPost("/todos", (Todo t) => { todos.Add(t); return Results.Created($"/todos/{t.Id}", t); });
```

**Expected output:**

```
app.MapGet("/todos", () => todos); app.MapPost("/todos", (Todo t) => { todos.Add(t); return Results.Created($"/todos/{t.Id}", t); });
```

**Learning points:** 

### Problem 3

Implement a background task runner using async/await and CancellationToken.

```
var cts = new CancellationTokenSource(); _ = Task.Run(() => ProcessAsync(cts.Token));
```

**Expected output:**

```
var cts = new CancellationTokenSource(); _ = Task.Run(() => ProcessAsync(cts.Token));
```

**Learning points:** 

### Problem 4

Build a JSON configuration manager that reads/writes settings using File I/O.

```
var config = JsonSerializer.Deserialize<AppSettings>(File.ReadAllText(path));
```

**Expected output:**

```
var config = JsonSerializer.Deserialize<AppSettings>(File.ReadAllText(path));
```

**Learning points:** 

### Problem 5

Create a LINQ query engine that filters and sorts a CSV dataset.

```
var results = records.Where(r => r.Age > 18).OrderBy(r => r.Name).Select(r => r.ToDisplayString());
```

**Expected output:**

```
var results = records.Where(r => r.Age > 18).OrderBy(r => r.Name).Select(r => r.ToDisplayString());
```

**Learning points:** 

### Problem 6

Build a plugin system using reflection and interfaces.

```
Assembly.Load(pluginPath); var plugins = assembly.GetTypes().Where(t => typeof(IPlugin).IsAssignableFrom(t));
```

**Expected output:**

```
Assembly.Load(pluginPath); var plugins = assembly.GetTypes().Where(t => typeof(IPlugin).IsAssignableFrom(t));
```

**Learning points:** 

### Problem 7

Implement a custom logger using delegates and events.

```
public event Action<string> OnLog; void Log(string msg) => OnLog?.Invoke(msg);
```

**Expected output:**

```
public event Action<string> OnLog; void Log(string msg) => OnLog?.Invoke(msg);
```

**Learning points:** 

### Problem 8

Build a URL shortener using ASP.NET with in-memory storage.

```
var urls = new Dictionary<string, string>(); app.MapPost("/shorten", (string url) => { var key = Guid.NewGuid().ToString()[..8]; urls[key] = url; return key; });
```

**Expected output:**

```
var urls = new Dictionary<string, string>(); app.MapPost("/shorten", (string url) => { var key = Guid.NewGuid().ToString()[..8]; urls[key] = url; return key; });
```

**Learning points:** 

### Problem 9

Create a parameterized SQL data access layer using ADO.NET.

```
using var cmd = new SqlCommand("SELECT * FROM Users WHERE Id = @id", conn); cmd.Parameters.AddWithValue("@id", userId);
```

**Expected output:**

```
using var cmd = new SqlCommand("SELECT * FROM Users WHERE Id = @id", conn); cmd.Parameters.AddWithValue("@id", userId);
```

**Learning points:** 

### Problem 10

Build a performance-benchmarked caching layer with ArrayPool and ValueTask.

```
[MemoryDiagnoser] public class CacheBenchmark { [Benchmark] public ValueTask<int> GetOrAdd() => new ValueTask<int>(42); }
```

**Expected output:**

```
[MemoryDiagnoser] public class CacheBenchmark { [Benchmark] public ValueTask<int> GetOrAdd() => new ValueTask<int>(42); }
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** How do you approach a capstone project?

**A:** Plan the architecture first, define interfaces, implement incrementally with tests, and refactor as you learn more.

**Q2:** What design patterns are useful in these projects?

**A:** Repository, Strategy, Observer (events), Factory, and Dependency Injection patterns are commonly used.

**Q3:** How do you test a REST API?

**A:** Use integration tests with WebApplicationFactory or HttpClient to send requests and verify responses.

**Q4:** What is the role of dependency injection in a capstone project?

**A:** It decouples components, making the code testable and maintainable by allowing interface-based programming.

**Q5:** How do you handle errors in a production application?

**A:** Use try/catch with logging, return appropriate HTTP status codes, and implement global error handling middleware.

**Q6:** What is the benefit of async/await in I/O-bound operations?

**A:** It keeps threads free for other work during I/O waits, improving scalability and responsiveness.

**Q7:** How do you secure a REST API?

**A:** Use authentication (JWT), authorization (roles/policies), input validation, and HTTPS.

**Q8:** What is the purpose of unit tests?

**A:** They verify individual components work correctly in isolation, enabling refactoring with confidence.

**Q9:** How do you containerize a .NET application?

**A:** Create a Dockerfile with the .NET SDK for building and the runtime image for execution, then build and run.

**Q10:** What should you consider when choosing a capstone project?

**A:** Choose something you are passionate about, that covers multiple topics, and that you can complete within your timeline.
