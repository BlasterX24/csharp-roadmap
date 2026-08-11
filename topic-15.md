# Topic 15: File I/O

File I/O in C# uses the System.IO namespace to read, write, and manipulate files and directories. The File and Directory static classes provide convenience methods. StreamReader and StreamWriter handle text streams. BinaryReader and BinaryWriter handle binary data. Async methods improve responsiveness for large files.

## Learn From

Study the System.IO namespace, focusing on File, Directory, StreamReader, and async file operations.

- https://learn.microsoft.com/en-us/dotnet/csharp/file-io/
- https://learn.microsoft.com/en-us/dotnet/api/system.io.file
- https://learn.microsoft.com/en-us/dotnet/api/system.io.streamreader
- https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/asynchronous-file-io

## Key Concepts

- File.ReadAllText and File.WriteAllText read/write entire files in one call
- File.ReadAllLines and File.WriteAllLines handle line-by-line I/O
- Directory.CreateDirectory creates a directory path
- Directory.GetFiles and Directory.GetDirectories list directory contents
- StreamReader reads text line-by-line or in chunks
- StreamWriter writes text with automatic buffer flushing
- BinaryReader and BinaryWriter handle primitive type serialization
- FileStream provides low-level byte-level access with buffering
- Async methods (ReadAllTextAsync, CopyToAsync) improve UI responsiveness
- File.Exists and Directory.Exists check for existence before operations

## Practice Problems & Solutions

### Problem 1

Read all text from a file named data.txt.

**Solution:**

```
string content = File.ReadAllText("data.txt");
```

**Expected output:**

```
string content = File.ReadAllText("data.txt");
```

**Learning points:** 

### Problem 2

Write "Hello" to a file named output.txt.

**Solution:**

```
File.WriteAllText("output.txt", "Hello");
```

**Expected output:**

```
File.WriteAllText("output.txt", "Hello");
```

**Learning points:** 

### Problem 3

Read all lines from a file into a string array.

**Solution:**

```
string[] lines = File.ReadAllLines("data.txt");
```

**Expected output:**

```
string[] lines = File.ReadAllLines("data.txt");
```

**Learning points:** 

### Problem 4

Create a directory named reports if it does not exist.

**Solution:**

```
Directory.CreateDirectory("reports");
```

**Expected output:**

```
Directory.CreateDirectory("reports");
```

**Learning points:** 

### Problem 5

Use StreamReader to read a file line-by-line.

**Solution:**

```
using var sr = new StreamReader("data.txt"); while (sr.Peek() >= 0) { string line = sr.ReadLine(); }
```

**Expected output:**

```
using var sr = new StreamReader("data.txt"); while (sr.Peek() >= 0) { string line = sr.ReadLine(); }
```

**Learning points:** 

### Problem 6

Use StreamWriter to append text to a file.

**Solution:**

```
using var sw = new StreamWriter("log.txt", true); sw.WriteLine("New entry");
```

**Expected output:**

```
using var sw = new StreamWriter("log.txt", true); sw.WriteLine("New entry");
```

**Learning points:** 

### Problem 7

Check if a file exists before reading it.

**Solution:**

```
if (File.Exists(path)) { string c = File.ReadAllText(path); }
```

**Expected output:**

```
if (File.Exists(path)) { string c = File.ReadAllText(path); }
```

**Learning points:** 

### Problem 8

Use async to read a file asynchronously.

**Solution:**

```
string content = await File.ReadAllTextAsync("data.txt");
```

**Expected output:**

```
string content = await File.ReadAllTextAsync("data.txt");
```

**Learning points:** 

### Problem 9

Write binary data using BinaryWriter.

**Solution:**

```
using var bw = new BinaryWriter(File.OpenWrite("data.bin")); bw.Write(42);
```

**Expected output:**

```
using var bw = new BinaryWriter(File.OpenWrite("data.bin")); bw.Write(42);
```

**Learning points:** 

### Problem 10

List all .txt files in a directory.

**Solution:**

```
string[] files = Directory.GetFiles("reports", "*.txt");
```

**Expected output:**

```
string[] files = Directory.GetFiles("reports", "*.txt");
```

**Learning points:** 

## Quick Questions & Answers

**Q1:** What is the difference between File.ReadAllText and StreamReader?

**A:** ReadAllText reads the entire file in one call; StreamReader is a stream-based reader that processes content incrementally, useful for large files.

**Q2:** When should you use async file I/O?

**A:** When reading/writing large files or doing I/O on UI threads to keep the application responsive.

**Q3:** What is the purpose of FileMode in FileStream?

**A:** It specifies how the file should be opened: Create, Open, OpenOrCreate, Append, or Truncate.

**Q4:** How do you copy a file in C#?

**A:** Use File.Copy(source, dest) which handles the entire copy operation.

**Q5:** What is the difference between BinaryWriter and StreamWriter?

**A:** BinaryWriter writes primitive types as raw bytes; StreamWriter writes text with encoding.

**Q6:** How do you delete a file?

**A:** Use File.Delete(path) which removes the file; check File.Exists first if needed.

**Q7:** What happens if you try to read a file that does not exist?

**A:** FileNotFoundException is thrown; check File.Exists before reading to avoid this.

**Q8:** What is the difference between File.Open and FileStream constructor?

**A:** File.Open is a static convenience method; new FileStream(path, mode) is the explicit constructor with more options.

**Q9:** How do you write a byte array to a file?

**A:** Use File.WriteAllBytes(path, bytes) or write via FileStream with a BinaryWriter.

**Q10:** What is the using statement's role in file I/O?

**A:** It ensures the stream or file handle is closed and disposed even if an exception occurs.
