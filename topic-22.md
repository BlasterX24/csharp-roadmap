# Topic 22: .NET Reversing with dnSpy/ILSpy

Decompilers like dnSpy and ILSpy reverse-engineer compiled .NET assemblies back into readable C# code. They are essential tools for security researchers analyzing third-party libraries, finding hardcoded secrets, understanding proprietary logic, and auditing code for vulnerabilities.

## Learn From

Install dnSpy or ILSpy, open an assembly, and practice navigating the decompiled code structure.

- https://github.com/dnSpy/dnSpy
- https://github.com/icsharpcode/ILSpy
- https://learn.microsoft.com/en-us/dotnet/standard/assembly/
- https://learn.microsoft.com/en-us/dotnet/framework/tools/

## Key Concepts

- dnSpy supports both decompilation and live editing/decompiling of assemblies
- ILSpy offers a lightweight, open-source alternative with plugin support
- Decompilers reconstruct C# source from IL metadata and opcodes
- Obfuscation tools like ConfuserEx and Dotfuscator make decompiled code harder to read
- Hardcoded secrets (API keys, connection strings, passwords) are visible in decompiled code
- String encryption obfuscation stores encrypted strings that are decrypted at runtime
- Method body analysis reveals algorithm logic and control flow
- Assembly references show which libraries and frameworks are used
- Metadata analysis reveals types, attributes, and versioning information
- Debug symbols (.pdb files) enable source-level debugging of decompiled code

## Practice Problems & Solutions

### Problem 1

Open an assembly in dnSpy and navigate to the Main method.

**Solution:**

```
File > Open > select the assembly > expand the tree > navigate to Program.cs > Main
```

**Expected output:**

```
Navigate to Program.Main in dnSpy
```

**Learning points:** 

### Problem 2

Decompile a DLL and find all string literals.

**Solution:**

```
Use Analyze > search for string references, or search for String in the search bar
```

**Expected output:**

```
Search for string references in the decompiled assembly
```

**Learning points:** 

### Problem 3

Identify a hardcoded API key in decompiled code.

**Solution:**

```
Look for string assignments with suspicious values like "sk-..." or "api_key=..."
```

**Expected output:**

```
Find string constants containing API keys or secrets
```

**Learning points:** 

### Problem 4

Use ILSpy to view the IL of a method.

**Solution:**

```
Right-click method > IL Instructions
```

**Expected output:**

```
View IL instructions in ILSpy
```

**Learning points:** 

### Problem 5

Find all methods that call a specific external method.

**Solution:**

```
Use the Analyze tab > References to find callers
```

**Expected output:**

```
Find references to the target method
```

**Learning points:** 

### Problem 6

Search for all types in an assembly that implement an interface.

**Solution:**

```
Use the search bar with IInterfaceName
```

**Expected output:**

```
Find implementing classes via search
```

**Learning points:** 

### Problem 7

Decompile and find the assembly version.

**Solution:**

```
Check Assembly Properties or the AssemblyInfo attribute
```

**Expected output:**

```
Read the AssemblyVersion attribute
```

**Learning points:** 

### Problem 8

Identify obfuscated class names in a decompiled assembly.

**Solution:**

```
Look for classes with names like <Module>, <>c, or random strings
```

**Expected output:**

```
Identify compiler-generated or obfuscated types
```

**Learning points:** 

### Problem 9

Find all configuration strings (connection strings, keys).

**Solution:**

```
Search for strings containing "Server=", "Password=", or "key="
```

**Expected output:**

```
Search for configuration-related string literals
```

**Learning points:** 

### Problem 10

Export decompiled source code from ILSpy.

**Solution:**

```
File > Save Code > select output directory
```

**Expected output:**

```
Export decompiled source to files
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between dnSpy and ILSpy?

**A:** dnSpy includes a debugger and editor; ILSpy is lighter and open-source with plugin support. Both decompile .NET assemblies.

**Q2:** How do decompilers reconstruct C# code?

**A:** They read IL opcodes and metadata, then apply heuristics to reconstruct high-level constructs like classes, methods, and properties.

**Q3:** What is string encryption obfuscation?

**A:** A technique where string literals are encrypted and decrypted at runtime, making static analysis harder.

**Q4:** How do you find hardcoded secrets?

**A:** Search for string literals in decompiled code; look for patterns like API keys, passwords, and connection strings.

**Q5:** What are debug symbols (.pdb files)?

**A:** Files that map IL instructions to source code lines, enabling step-through debugging of decompiled assemblies.

**Q6:** How do you handle obfuscated code?

**A:** Use deobfuscators like de4dot, or analyze IL directly to understand the true behavior.

**Q7:** What information can you extract from assembly metadata?

**A:** Version numbers, dependencies, type definitions, custom attributes, and security permissions.

**Q8:** Can you modify and recompile a decompiled assembly?

**A:** Yes; dnSpy supports editing and recompiling method bodies directly.

**Q9:** What is the difference between IL and decompiled C#?

**A:** IL is the low-level instruction set; decompiled C# is a reconstruction that approximates the original source code.

**Q10:** How do you analyze a .NET assembly without decompiling?

**A:** Use ildasm for raw IL, monodis for Mono assemblies, or dotPeek for quick decompilation.
