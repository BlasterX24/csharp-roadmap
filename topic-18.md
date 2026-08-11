# Topic 18: NuGet & Packaging

NuGet is the .NET package manager. It provides a repository of libraries that you can add to your projects. You can create your own NuGet packages to share code with others. Understanding NuGet is essential for managing dependencies and distributing your libraries.

## Learn From

Study NuGet package creation, the dotnet CLI for packaging, and the NuGet.org publishing workflow.

- https://learn.microsoft.com/en-us/nuget/
- https://learn.microsoft.com/en-us/nuget/create-packages/creating-a-package
- https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-pack
- https://learn.microsoft.com/en-us/nuget/quickstart/create-and-publish-a-package

## Key Concepts

- dotnet add package adds a NuGet dependency to a project
- NuGet packages are .nupkg files containing assemblies and metadata
- The .nuspec or .csproj file defines package metadata (version, authors, description)
- PackageReference is the modern way to reference NuGet packages in .csproj
- dotnet pack creates a .nupkg from a project
- dotnet nuget push publishes a package to NuGet.org or a private feed
- Semantic versioning (SemVer) defines version numbering: MAJOR.MINOR.PATCH
- Package dependencies are resolved automatically by NuGet
- Private NuGet feeds can be configured in nuget.config
- Source Link embeds source code links in packages for debugging

## Practice Problems & Solutions

### Problem 1

Add the Newtonsoft.Json package to a project using dotnet CLI.

**Solution:**

```
dotnet add package Newtonsoft.Json
```

**Expected output:**

```
dotnet add package Newtonsoft.Json
```

**Learning points:** 

### Problem 2

Create a NuGet package from a project.

**Solution:**

```
dotnet pack
```

**Expected output:**

```
dotnet pack
```

**Learning points:** 

### Problem 3

Publish a NuGet package to NuGet.org.

**Solution:**

```
dotnet nuget push *.nupkg --api-key <API_KEY> --source https://api.nuget.org/v3/index.json
```

**Expected output:**

```
dotnet nuget push *.nupkg --api-key <API_KEY> --source https://api.nuget.org/v3/index.json
```

**Learning points:** 

### Problem 4

Specify a package version in the .csproj file.

**Solution:**

```
<Version>1.0.0</Version>
```

**Expected output:**

```
<Version>1.0.0</Version>
```

**Learning points:** 

### Problem 5

Add a package dependency with a version range.

**Solution:**

```
<PackageReference Include="Newtonsoft.Json" Version="[13.0.1, 14.0.0)" />
```

**Expected output:**

```
<PackageReference Include="Newtonsoft.Json" Version="[13.0.1, 14.0.0)" />
```

**Learning points:** 

### Problem 6

List installed NuGet packages in a project.

**Solution:**

```
dotnet list package
```

**Expected output:**

```
dotnet list package
```

**Learning points:** 

### Problem 7

Restore NuGet packages for a solution.

**Solution:**

```
dotnet restore
```

**Expected output:**

```
dotnet restore
```

**Learning points:** 

### Problem 8

Create a NuGet package with a specific output directory.

**Solution:**

```
dotnet pack -o ./nupkgs
```

**Expected output:**

```
dotnet pack -o ./nupkgs
```

**Learning points:** 

### Problem 9

Add a private NuGet source.

**Solution:**

```
dotnet nuget add source https://myrepo.com/v3/index.json --name MyFeed
```

**Expected output:**

```
dotnet nuget add source https://myrepo.com/v3/index.json --name MyFeed
```

**Learning points:** 

### Problem 10

Update a specific NuGet package to the latest version.

**Solution:**

```
dotnet add package Newtonsoft.Json --latest
```

**Expected output:**

```
dotnet add package Newtonsoft.Json --latest
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between PackageReference and packages.config?

**A:** PackageReference is the modern format stored in .csproj; packages.config is the legacy format with an XML file listing packages.

**Q2:** What is semantic versioning?

**A:** A versioning scheme using MAJOR.MINOR.PATCH where MAJOR has breaking changes, MINOR adds features, PATCH fixes bugs.

**Q3:** How do you create a NuGet package from a class library?

**A:** Run dotnet pack which generates a .nupkg containing the compiled assemblies and package metadata.

**Q4:** What is a NuGet source?

**A:** A feed URL from which NuGet resolves and downloads packages; NuGet.org is the default public source.

**Q5:** What is the difference between a stable and prerelease package?

**A:** Stable packages have no suffix; prerelease packages include -alpha, -beta, -rc suffixes.

**Q6:** How do you specify a package description?

**A:** In the .csproj file with <Description>My library description</Description>.

**Q7:** What is Source Link?

**A:** A feature that embeds source code URLs in debug symbols, enabling step-through debugging of NuGet packages.

**Q8:** Can you reference a local project as a NuGet package?

**A:** Yes; use ProjectReference for development or create a local .nupkg and reference it as a PackageReference.

**Q9:** What is the difference between dotnet restore and dotnet build?

**A:** Restore downloads package dependencies; build compiles the code. Build implicitly runs restore if needed.

**Q10:** How do you uninstall a NuGet package?

**A:** Run dotnet remove package <PackageName> which removes the PackageReference from the .csproj.
