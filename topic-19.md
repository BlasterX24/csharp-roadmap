# Topic 19: ASP.NET Basics

ASP.NET Core is the cross-platform web framework for building APIs and web apps. Minimal APIs provide a lightweight way to define endpoints with minimal ceremony. Controllers offer the traditional MVC pattern. Middleware pipeline processes requests. Routing maps URLs to handlers.

## Learn From

Start with the ASP.NET Core getting-started guide, then explore minimal APIs and middleware.

- https://learn.microsoft.com/en-us/aspnet/core/getting-started/
- https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis
- https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/actions
- https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware

## Key Concepts

- WebApplication.CreateBuilder creates a configurable host
- app.MapGet/MapPost/MapPut/MapDelete define minimal API endpoints
- Controllers use [Route], [HttpGet], [HttpPost] attributes for routing
- Middleware components process requests in a pipeline
- app.Use* adds middleware; app.Map* branches the pipeline
- Dependency injection (DI) registers services in the container
- app.Run() starts the web server
- Request and Response objects provide HTTP data
- Model binding maps request data to method parameters
- Filters intercept controller actions for cross-cutting concerns

## Practice Problems & Solutions

### Problem 1

Create a minimal API that responds GET to /hello with "Hello, World!".

**Solution:**

```
var app = WebApplication.CreateBuilder(args).Build(); app.MapGet("/hello", () => "Hello, World!"); app.Run();
```

**Expected output:**

```
var app = WebApplication.CreateBuilder(args).Build(); app.MapGet("/hello", () => "Hello, World!"); app.Run();
```

**Learning points:** 

### Problem 2

Create a minimal API endpoint that accepts a name parameter.

**Solution:**

```
app.MapGet("/greet/{name}", (string name) => $"Hello, {name}!");
```

**Expected output:**

```
app.MapGet("/greet/{name}", (string name) => $"Hello, {name}!");
```

**Learning points:** 

### Problem 3

Create a minimal API POST endpoint that accepts a JSON body.

**Solution:**

```
app.MapPost("/items", (Item item) => Results.Created($"/items/1", item));
```

**Expected output:**

```
app.MapPost("/items", (Item item) => Results.Created($"/items/1", item));
```

**Learning points:** 

### Problem 4

Configure a service in the DI container.

**Solution:**

```
builder.Services.AddSingleton<IMyService, MyService>();
```

**Expected output:**

```
builder.Services.AddSingleton<IMyService, MyService>();
```

**Learning points:** 

### Problem 5

Add a middleware that logs the request path.

**Solution:**

```
app.Use(async (context, next) => { Console.WriteLine(context.Request.Path); await next(); });
```

**Expected output:**

```
app.Use(async (context, next) => { Console.WriteLine(context.Request.Path); await next(); });
```

**Learning points:** 

### Problem 6

Create a controller with a [Route("api/[controller]")] attribute.

**Solution:**

```
[Route("api/[controller]")] public class UsersController : Controller { }
```

**Expected output:**

```
[Route("api/[controller]")] public class UsersController : Controller { }
```

**Learning points:** 

### Problem 7

Map a route to a controller action using [HttpGet("{id}")].

**Solution:**

```
[HttpGet("{id}")] public IActionResult Get(int id) => Ok(id);
```

**Expected output:**

```
[HttpGet("{id}")] public IActionResult Get(int id) => Ok(id);
```

**Learning points:** 

### Problem 8

Add CORS middleware to allow all origins.

**Solution:**

```
app.UseCors(policy => policy.AllowAnyOrigin().AllowAnyMethod().AllowAnyHeader());
```

**Expected output:**

```
app.UseCors(policy => policy.AllowAnyOrigin().AllowAnyMethod().AllowAnyHeader());
```

**Learning points:** 

### Problem 9

Use app.UseExceptionHandler to add global error handling.

**Solution:**

```
app.UseExceptionHandler(error => { error.Run(async context => { context.Response.StatusCode = 500; }); });
```

**Expected output:**

```
app.UseExceptionHandler(error => { error.Run(async context => { context.Response.StatusCode = 500; }); });
```

**Learning points:** 

### Problem 10

Return a 404 Not Found from a minimal API endpoint.

**Solution:**

```
app.MapGet("/check", () => Results.NotFound());
```

**Expected output:**

```
app.MapGet("/check", () => Results.NotFound());
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between minimal APIs and controllers?

**A:** Minimal APIs are lightweight, attribute-free, and ideal for simple APIs; controllers use attributes and support features like model validation and filters.

**Q2:** How does middleware pipeline work?

**A:** Each middleware component calls next() to pass the request to the next component; if not called, the pipeline short-circuits.

**Q3:** What is dependency injection in ASP.NET?

**A:** The framework creates and injects service instances into constructors, promoting loose coupling and testability.

**Q4:** How do you configure Kestrel to listen on a specific port?

**A:** Use builder.WebHost.ConfigureKestrel(options => options.ListenLocalhost(5000)) or use appsettings.json.

**Q5:** What is model binding?

**A:** The process of mapping request data (query strings, route data, body) to method parameters or model objects.

**Q6:** How do you return JSON from a minimal API?

**A:** Return an object directly; ASP.NET serializes it to JSON automatically with the default JSON serializer.

**Q7:** What is the difference between app.Use and app.Map?

**A:** Use adds middleware to the pipeline; Map branches the pipeline based on a path prefix.

**Q8:** How do you add authentication middleware?

**A:** Use app.UseAuthentication() and app.UseAuthorization() after adding services with AddAuthentication().

**Q9:** What is the Purpose of [FromBody] and [FromQuery] attributes?

**A:** They specify the source of model binding: FromBody reads from the request body; FromQuery reads from query string parameters.

**Q10:** Can minimal APIs use filters?

**A:** Yes; since .NET 7, minimal APIs support endpoint filters for validation and cross-cutting concerns.
