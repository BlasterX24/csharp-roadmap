# Topic 1: Setup & .NET Intro

C# is a modern, object-oriented language that runs on .NET. You begin by installing the .NET SDK, creating a project with `dotnet new console`, and writing your first `Main` method. The CLI manages build, run, and test workflows so you can focus on code from day one.

## Learn From

Start with the official .NET getting-started guide, then explore the CLI reference and the Roslyn compiler docs.

- https://learn.microsoft.com/en-us/dotnet/core/get-started
- https://learn.microsoft.com/en-us/dotnet/core/tools/
- https://learn.microsoft.com/en-us/dotnet/csharp/
- https://learn.microsoft.com/en-us/dotnet/core/introduction

## Key Concepts

- dotnet new console creates a new project with a Program.cs and .csproj file
- Main is the entry point; it can be top-level or a traditional method
- Console.WriteLine writes output to the terminal
- dotnet build compiles; dotnet run builds and executes
- Namespaces organize code; using directives import them
- Project file (.csproj) defines target framework, dependencies, and settings
- dotnet test runs unit tests from the project
- dotnet restore downloads NuGet package dependencies
- Global using directives reduce boilerplate in .NET 6+
- The entry point is discovered by the compiler when no explicit Main is defined

## Practice Problems & Solutions

### Problem 1

What command creates a new C# console project named MyApp?

**Solution:**

```
dotnet new console -n MyApp
```

**Expected output:**

```
dotnet new console -n MyApp
```

**Learning points:** 

### Problem 2

Write a Program.cs that prints Hello, World! to the console.

**Solution:**

```
Console.WriteLine("Hello, World!");
```

**Expected output:**

```
Console.WriteLine("Hello, World!");
```

**Learning points:** 

### Problem 3

How do you compile and run a project from the project directory?

**Solution:**

```
dotnet run
```

**Expected output:**

```
dotnet run
```

**Learning points:** 

### Problem 4

Write a top-level statement Main that prints the current date.

**Solution:**

```
Console.WriteLine(DateTime.Now);
```

**Expected output:**

```
Console.WriteLine(DateTime.Now);
```

**Learning points:** 

### Problem 5

What command restores NuGet packages for a project?

**Solution:**

```
dotnet restore
```

**Expected output:**

```
dotnet restore
```

**Learning points:** 

### Problem 6

Create a namespace called MyApp.Models and put a class inside it.

**Solution:**

```
namespace MyApp.Models { public class User { public string Name { get; set; } } }
```

**Expected output:**

```
namespace MyApp.Models { public class User { public string Name { get; set; } } }
```

**Learning points:** 

### Problem 7

Write code that prints the .NET runtime version to the console.

**Solution:**

```
Console.WriteLine(System.Environment.Version);
```

**Expected output:**

```
Console.WriteLine(System.Environment.Version);
```

**Learning points:** 

### Problem 8

What is the extension of a C# project file?

**Solution:**

```
.csproj
```

**Expected output:**

```
.csproj
```

**Learning points:** 

### Problem 9

Write a using directive to import the System namespace.

**Solution:**

```
using System;
```

**Expected output:**

```
using System;
```

**Learning points:** 

### Problem 10

What command lists installed .NET SDK versions?

**Solution:**

```
dotnet --list-sdks
```

**Expected output:**

```
dotnet --list-sdks
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between dotnet build and dotnet run?

**A:** dotnet build compiles the project into an assembly but does not execute it; dotnet run compiles and then executes the resulting program.

**Q2:** Can a C# program have more than one Main method?

**A:** Only one entry point per project is allowed; the compiler will report an error if multiple Main methods exist without explicit configuration.

**Q3:** What does the .csproj file control?

**A:** It defines the target framework, package references, compiler options, output type, and other MSBuild settings for the project.

**Q4:** What is a top-level statement in C#?

**A:** It lets you write executable code directly in Program.cs without an explicit Main method or class; the compiler wraps it in a Program class and Main method.

**Q5:** How do you add a NuGet package from the CLI?

**A:** Run dotnet add package <PackageName> which adds a PackageReference to the .csproj and restores.

**Q6:** What is the purpose of global using directives?

**A:** They let you place a using statement in one file so it is available across all files in the project, reducing repetitive imports.

**Q7:** What target framework moniker does a new console project use by default?

**A:** net8.0 (or the latest LTS version installed, such as net6.0).

**Q8:** What is the role of the Roslyn compiler?

**A:** Roslyn (Microsoft.CodeAnalysis) is the C# compiler that compiles source code into IL assemblies and provides rich code analysis APIs.

**Q9:** How do you create a class library project?

**A:** dotnet new classlib -n MyLibrary produces a project that compiles to a DLL instead of an executable.

**Q10:** What is the difference between console and classlib project templates?

**A:** Console produces an executable with an entry point; classlib produces a reusable DLL with no entry point.
