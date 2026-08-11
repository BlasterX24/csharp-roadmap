# Topic 21: IL (Intermediate Language)

Intermediate Language (IL) is the low-level instruction set that C# compiles to before the JIT converts it to native code. Understanding IL helps you understand how language constructs work under the hood and is essential for decompilation and security analysis.

## Learn From

Study IL opcodes with the Common Intermediate Language reference and use ildasm to inspect assemblies.

- https://learn.microsoft.com/en-us/dotnet/api/system.reflection.emit
- https://learn.microsoft.com/en-us/dotnet/framework/tools/ildasm-exe
- https://learn.microsoft.com/en-us/dotnet/standard/assembly/
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/stackalloc

## Key Concepts

- IL is a stack-based instruction set; operations push and pop values from an evaluation stack
- Common opcodes: ldloc (load local), stloc (store local), ldc (load constant), call, ret
- The JIT compiler converts IL to native machine code at runtime
- Metadata in assemblies describes types, methods, fields, and references
- ildasm is the IL Disassembler that displays assembly contents as IL
- Assembly contains a manifest, type definitions, and IL code
- Value types are boxed/unboxed when moving to/from the IL stack
- Exception handling in IL uses try/catch/filter blocks
- The CLR manages memory, type safety, and security through IL verification
- Understanding IL helps identify obfuscation and reverse-engineering techniques

## Practice Problems & Solutions

### Problem 1

Use ildasm to view the IL of a compiled assembly.

**Solution:**

```
ildasm MyApp.dll
```

**Expected output:**

```
ildasm MyApp.dll
```

**Learning points:** 

### Problem 2

Identify the IL opcode for loading an integer constant onto the stack.

**Solution:**

```
ldc.i4 <value>
```

**Expected output:**

```
ldc.i4 <value>
```

**Learning points:** 

### Problem 3

What IL opcode is used to call a static method?

**Solution:**

```
call
```

**Expected output:**

```
call
```

**Learning points:** 

### Problem 4

What IL opcode returns from a method?

**Solution:**

```
ret
```

**Expected output:**

```
ret
```

**Learning points:** 

### Problem 5

What is the IL for a simple if/else statement?

**Solution:**

```
brfalse/brtrue to jump past the false branch, then br to skip the true branch
```

**Expected output:**

```
brfalse/brtrue to jump past the false branch, then br to skip the true branch
```

**Learning points:** 

### Problem 6

What IL opcode stores a value into a local variable?

**Solution:**

```
stloc
```

**Expected output:**

```
stloc
```

**Learning points:** 

### Problem 7

What is a metadata token in IL?

**Solution:**

```
A numeric identifier that references a type, method, field, or string in the assembly metadata
```

**Expected output:**

```
A numeric identifier that references a type, method, field, or string in the assembly metadata
```

**Learning points:** 

### Problem 8

What is the difference between box and unbox IL opcodes?

**Solution:**

```
box converts a value type to an object reference on the heap; unbox extracts a value type from an object
```

**Expected output:**

```
box converts a value type to an object reference on the heap; unbox extracts a value type from an object
```

**Learning points:** 

### Problem 9

How does the CLR verify IL for type safety?

**Solution:**

```
The verifier checks that operations are type-safe, stack is balanced, and no invalid casts occur before JIT compilation
```

**Expected output:**

```
The verifier checks that operations are type-safe, stack is balanced, and no invalid casts occur before JIT compilation
```

**Learning points:** 

### Problem 10

What is the purpose of the .locals directive in IL?

**Solution:**

```
Declares local variables for a method, specifying their types and init flag
```

**Expected output:**

```
Declares local variables for a method, specifying their types and init flag
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** Why should a security researcher understand IL?

**A:** IL reveals the true behavior of compiled code, enabling detection of hidden logic, backdoors, and obfuscation techniques.

**Q2:** What is the difference between JIT and AOT compilation?

**A:** JIT compiles IL to native code at runtime; AOT (Ahead-of-Time) compiles to native code before deployment, reducing startup time.

**Q3:** How does IL enforce type safety?

**A:** The CLR verifier checks IL operations at load time to ensure no type violations or memory corruption.

**Q4:** What is a metadata token?

**A:** A 32-bit value that references a type, method, field, or string in the assembly's metadata tables.

**Q5:** What is the difference between call and callvirt IL opcodes?

**A:** call invokes a method directly; callvirt invokes virtually, supporting polymorphic dispatch and null checks.

**Q6:** How do loops translate to IL?

**A:** Loops use conditional branches (brtrue, brfalse) and unconditional branches (br) to create循环 structures.

**Q7:** What is the purpose of the ldloc opcode?

**A:** It loads the value of a local variable onto the evaluation stack for use by subsequent instructions.

**Q8:** What is the role of the .entrypoint directive?

**A:** It specifies the method that serves as the assembly's entry point, typically Main.

**Q9:** How does exception handling work in IL?

**A:** IL uses .try/catch/filter directives to define exception regions, with leave instructions to transfer control.

**Q10:** What is the difference between valuetype and class in IL?

**A:** valuetype instances are stored on the stack or inline; class instances are reference types stored on the managed heap.
