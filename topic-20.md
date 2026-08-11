# Topic 20: .NET Reflection

Reflection lets you inspect and invoke types, methods, properties, and fields at runtime. The System.Reflection namespace provides Type, MethodInfo, PropertyInfo, and FieldInfo classes. Reflection enables dynamic loading, late binding, and metadata inspection, but incurs a performance cost.

## Learn From

Study the System.Reflection namespace and practice inspecting types and invoking methods dynamically.

- https://learn.microsoft.com/en-us/dotnet/fundamentals/reflection-and-loading
- https://learn.microsoft.com/en-us/dotnet/api/system.type
- https://learn.microsoft.com/en-us/dotnet/api/system.reflection.methodinfo
- https://learn.microsoft.com/en-us/dotnet/api/system.reflection.propertyinfo

## Key Concepts

- typeof(T) and obj.GetType() obtain the Type of a class
- Type.GetMethods() returns all methods; GetProperties() returns all properties
- MethodInfo.Invoke() dynamically calls a method by reflection
- PropertyInfo.GetValue and SetValue read/write properties dynamically
- FieldInfo reads/writes fields at runtime
- Assembly.Load loads assemblies dynamically from bytes or files
- CustomAttributes provides access to attributes on types and members
- BindingFlags control which members are retrieved (public, static, instance)
- Activator.CreateInstance creates instances of types dynamically
- Reflection is used by serialization, ORMs, DI containers, and testing frameworks

## Practice Problems & Solutions

### Problem 1

Get the Type of a string variable using reflection.

**Solution:**

```
Type t = typeof(string);
```

**Expected output:**

```
Type t = typeof(string);
```

**Learning points:** 

### Problem 2

Get all public methods of a type.

**Solution:**

```
MethodInfo[] methods = typeof(MyClass).GetMethods(BindingFlags.Public | BindingFlags.Instance);
```

**Expected output:**

```
MethodInfo[] methods = typeof(MyClass).GetMethods(BindingFlags.Public | BindingFlags.Instance);
```

**Learning points:** 

### Problem 3

Invoke a method by name using MethodInfo.Invoke.

**Solution:**

```
MethodInfo m = typeof(MyClass).GetMethod("DoWork"); m.Invoke(obj, new object[] { });
```

**Expected output:**

```
MethodInfo m = typeof(MyClass).GetMethod("DoWork"); m.Invoke(obj, new object[] { });
```

**Learning points:** 

### Problem 4

Get a property value using PropertyInfo.GetValue.

**Solution:**

```
PropertyInfo p = typeof(MyClass).GetProperty("Name"); string val = (string)p.GetValue(obj);
```

**Expected output:**

```
PropertyInfo p = typeof(MyClass).GetProperty("Name"); string val = (string)p.GetValue(obj);
```

**Learning points:** 

### Problem 5

Create an instance of a type dynamically using Activator.

**Solution:**

```
object instance = Activator.CreateInstance(typeof(MyClass));
```

**Expected output:**

```
object instance = Activator.CreateInstance(typeof(MyClass));
```

**Learning points:** 

### Problem 6

Check if a type implements an interface.

**Solution:**

```
bool implements = typeof(MyClass).IsAssignableFrom(typeof(IMyInterface));
```

**Expected output:**

```
bool implements = typeof(MyClass).IsAssignableFrom(typeof(IMyInterface));
```

**Learning points:** 

### Problem 7

Get custom attributes on a class.

**Solution:**

```
var attrs = typeof(MyClass).GetCustomAttributes(typeof(ObsoleteAttribute), false);
```

**Expected output:**

```
var attrs = typeof(MyClass).GetCustomAttributes(typeof(ObsoleteAttribute), false);
```

**Learning points:** 

### Problem 8

Set a property value dynamically with PropertyInfo.SetValue.

**Solution:**

```
PropertyInfo p = typeof(MyClass).GetProperty("Count"); p.SetValue(obj, 42);
```

**Expected output:**

```
PropertyInfo p = typeof(MyClass).GetProperty("Count"); p.SetValue(obj, 42);
```

**Learning points:** 

### Problem 9

Get all properties of a type that are strings.

**Solution:**

```
var strProps = typeof(MyClass).GetProperties().Where(p => p.PropertyType == typeof(string));
```

**Expected output:**

```
var strProps = typeof(MyClass).GetProperties().Where(p => p.PropertyType == typeof(string));
```

**Learning points:** 

### Problem 10

Use Type.GetConstructor to create an instance with constructor parameters.

**Solution:**

```
var ctor = typeof(MyClass).GetConstructor(new[] { typeof(string) }); object obj = ctor.Invoke(new object[] { "test" });
```

**Expected output:**

```
var ctor = typeof(MyClass).GetConstructor(new[] { typeof(string) }); object obj = ctor.Invoke(new object[] { "test" });
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the performance cost of reflection?

**A:** Reflection is significantly slower than direct calls due to dynamic type checking and boxing; cache reflected members for repeated use.

**Q2:** What are BindingFlags?

**A:** Flags that control which members are retrieved: Public, Private, Static, Instance, DeclaredOnly, FlattenHierarchy.

**Q3:** What is the difference between typeof and GetType?

**A:** typeof(T) is a compile-time operation; GetType() is a runtime method on an object instance.

**Q4:** How does Activator.CreateInstance work?

**A:** It dynamically creates an instance of a type using its constructor; you can pass constructor parameters as arguments.

**Q5:** What is the difference between Property and Field info?

**A:** PropertyInfo wraps properties (get/set accessors); FieldInfo wraps fields directly.

**Q6:** How do you get generic type arguments?

**A:** Use Type.GetGenericArguments() which returns an array of Type objects for the type parameters.

**Q7:** What is dynamic invocation?

**A:** Calling a method or accessing a property by name at runtime using reflection or the dynamic keyword.

**Q8:** What is Assembly.Load used for?

**A:** To dynamically load an assembly from a file or byte array, enabling plugin architectures.

**Q9:** Can reflection access private members?

**A:** Yes; using BindingFlags.NonPublic, reflection can access private fields, methods, and properties.

**Q10:** What are the alternatives to reflection?

**A:** Source generators, expression trees, dynamic keyword, and compiled delegates offer better performance for known types.
