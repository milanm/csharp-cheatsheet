# C# Programming Cheat Sheet (2025 Edition)

## Introduction

This comprehensive C# cheat sheet serves as a quick reference guide for C# developers at all skill levels. It covers the core language features, modern patterns, and best practices as of 2025. 

The cheat sheet organizes **fundamental concepts into more advanced topics**,** making it useful for learning and reference.

C# has evolved significantly since its inception, with regular updates introducing powerful new features while maintaining backward compatibility.

This guide incorporates the latest language enhancements **through C# 13 and beyond**, as well as code organization, and development approaches that have become standard in the .NET ecosystem.

🔖 Feel free to **bookmark this page** and refer to it whenever you need to refresh your knowledge of C# language features or modern development techniques.

The image below show an **overview of the C# language features and concepts** covered in this cheat sheet:

![C# Mind map](csharp-mindmap.png)

## Support my work

If you find this repository helpful, consider supporting me on Patreon:

[![Patreon](patreon.png)](https://www.patreon.com/techworld_with_milan)

## Give a Star! :star:

If you like or are using this project to learn or start your solution, please give it a star. Thanks!

## Table of contents

- [Comments](#comments)
- [Strings](#strings)
- [Basic types and literals](#basic-types-and-literals)
- [Statements](#statements)
  - [Control flow](#control-flow)
  - [Loops](#loops)
  - [Lock statement](#lock-statement)
  - [Using statement](#using-statement)
  - [Unsafe code](#unsafe-code)
  - [Yield statement](#yield-statement)
- [Methods and functions](#methods-and-functions)
  - [Basic method syntax](#basic-method-syntax)
  - [Expression-bodied members](#expression-bodied-members-c-60)
  - [Method parameters](#method-parameters)
  - [Local functions](#local-functions-c-70)
  - [Extension methods](#extension-methods)
  - [Lambda expressions](#lambda-expressions)
  - [Method overloading](#method-overloading)
- [Delegates and events](#delegates-and-events)
- [Data types](#data-types)
  - [Classes](#classes)
  - [Structs](#structs)
  - [Records](#records-c-90)
  - [Record structs](#record-structs-c-100)
  - [Interfaces](#interfaces)
  - [Enums](#enums)
  - [Tuples](#tuples)
  - [Nullable types](#nullable-types)
- [Generics](#generics)
  - [Generic classes](#generic-classes) 
  - [Generic methods](#generic-methods)
  - [Constraints](#constraints)  
- [Classes and inheritance](#classes-and-inheritance)
  - [Constructors and initialization](#constructors-and-initialization)
  - [Primary constructors](#primary-constructors-c-12)
  - [Inheritance](#inheritance)
  - [Abstract classes](#abstract-classes)
  - [Sealed classes and members](#sealed-classes-and-members)
  - [Polymorphism](#polymorphism)
- [Collections](#collections)
  - [Collection expressions](#collection-expressions-c-12)
  - [Arrays](#arrays)
  - [Lists](#lists)
  - [Dictionary](#dictionary)
  - [HashSet](#hashset)
  - [Queue and Stack](#queue-and-stack)
  - [LINQ](#linq-language-integrated-query)
- [Pattern matching](#pattern-matching)
  - [Type patterns](#type-patterns)
  - [Property patterns](#property-patterns)
  - [Tuple patterns](#tuple-patterns)
  - [Logical patterns](#logical-patterns)
  - [List patterns](#list-patterns-c-110)
  - [Discard patterns](#discard-pattern)
- [Exceptions](#exceptions)
  - [Try-Catch-Finally](#try-catch-finally)
  - [Throwing exceptions](#throwing-exceptions)
  - [Custom exceptions](#custom-exceptions)
- [Asynchronous programming](#asynchronous-programming)
  - [Async and await basics](#async-and-await-basics)
  - [Task-based asynchronous pattern](#task-based-asynchronous-pattern)
  - [Exception handling in async code](#exception-handling-in-async-code)
  - [Cancellation in async operations](#cancellation-in-async-operations)
  - [ValueTask and async streams](#valuetask-and-async-streams-c-80)
- [Code organization](#code-organization)
  - [Namespaces](#namespaces)
  - [Using directives](#using-directives)
  - [File-scoped types](#file-scoped-types-c-11)
  - [Partial classes](#partial-classes)
  - [Access modifiers](#access-modifiers)
  - [Properties and indexers](#properties-and-indexers)

<div id="comments"></div>

# Comments

Comments in C# provide ways to document your code, explain complex logic, and temporarily disable code during development. C# supports three types of comments: single-line, multi-line, and XML documentation comments. Good commenting practices are essential for code maintainability, especially in team environments.

```csharp
// This is a single-line comment

/* This is a 
   multi-line comment */

/// <summary>
/// XML documentation comment used to generate documentation
/// </summary>
public void DocumentedMethod() { }
```

XML documentation comments can include various tags to document parameters, return values, exceptions, etc.

```csharp
/// <summary>
/// Adds two integers and returns the result
/// </summary>
/// <param name="a">First integer</param>
/// <param name="b">Second integer</param>
/// <returns>The sum of the two integers</returns>
/// <exception cref="OverflowException">Thrown when the sum is too large</exception>
public int Add(int a, int b) => a + b;
```

**Additional resources:**

- [Microsoft Docs: XML Documentation Comments](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/)
- [C# Coding Conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)

<div id="strings"></div>

# Strings

Strings in C# are immutable sequences of Unicode characters represented by the `string` type (an alias for `System.String`). C# offers a rich set of string manipulation features, from basic concatenation to advanced interpolation and raw string literals. The language has evolved significantly to make string handling more intuitive and efficient.

```csharp
// Basic string creation
string greeting = "Hello";
string name = "World";
string message = greeting + " " + name; // "Hello World"

// String interpolation (C# 6.0+)
string interpolated = $"{greeting} {name}!"; // "Hello World!"

// Verbatim strings (preserves formatting and ignores escape sequences except "")
string path = @"C:\Users\UserName\Documents";
string multiline = @"This is a
multi-line string
that preserves formatting";

// Verbatim string interpolation
string verbatimInterpolated = $@"User {name}
Path: {path}";

// Raw string literals (C# 11+) - no escape sequences, preserves formatting
string json = """
{
    "name": "John Doe",
    "age": 30,
    "isActive": true
}
""";

// Raw string interpolation (C# 11+)
string name = "Jane";
string rawInterpolated = $"""
{
    "name": "{{name}}",
    "created": "{{DateTime.Now}}"
}
""";

// Common string methods
string text = "Hello, World!";
bool contains = text.Contains("World"); // true
string upper = text.ToUpper(); // "HELLO, WORLD!"
string lower = text.ToLower(); // "hello, world!"
string replaced = text.Replace("Hello", "Hi"); // "Hi, World!"
string trimmed = "  text  ".Trim(); // "text"
string[] split = text.Split(','); // ["Hello", " World!"]
int length = text.Length; // 13

// String comparison
bool equals = string.Equals("abc", "ABC", StringComparison.OrdinalIgnoreCase); // true
int comparison = string.Compare("abc", "ABC", StringComparison.Ordinal); // not equal
```

For better performance with repeated string concatenation (as String is immutable type), use `StringBuilder`:

```csharp
using System.Text;

StringBuilder sb = new StringBuilder();
for (int i = 0; i < 100; i++)
{
    sb.Append($"Item {i}, ");
}
string result = sb.ToString();
```

**Additional resources:**

- [String class (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/api/system.string)
- [String interpolation (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated)
- [Raw String literals (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-11.0/raw-string-literal)
- [String performance best practices](https://learn.microsoft.com/en-us/dotnet/standard/base-types/best-practices-strings)

<div id="basic-types-and-literals"></div>

# Basic types and literals

C# is a strongly-typed language with a comprehensive type system that forms the foundation of all C# programs. Understanding these basic types is essential for writing efficient and type-safe code. 

C# types are categorized as **value types (stored on the stack)** and **reference types (stored on the heap)**, each with different memory and performance characteristics.

```csharp
// Integer types
byte byteValue = 255;                // 8-bit unsigned integer (0 to 255)
sbyte sbyteValue = -128;             // 8-bit signed integer (-128 to 127)
short shortValue = -32768;           // 16-bit signed integer (-32,768 to 32,767)
ushort ushortValue = 65535;          // 16-bit unsigned integer (0 to 65,535)
int intValue = -2147483648;          // 32-bit signed integer (-2,147,483,648 to 2,147,483,647)
uint uintValue = 4294967295;         // 32-bit unsigned integer (0 to 4,294,967,295)
long longValue = -9223372036854775808; // 64-bit signed integer (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)
ulong ulongValue = 18446744073709551615; // 64-bit unsigned integer (0 to 18,446,744,073,709,551,615)

// Integer literals
int decimalLiteral = 42;             // Decimal (base 10)
int hexLiteral = 0x2A;               // Hexadecimal (base 16)
int binaryLiteral = 0b101010;        // Binary (base 2)
int withSeparator = 1_000_000;       // Digit separator for readability

// Floating point types
float floatValue = 3.14f;            // 32-bit floating-point (7 significant digits precision)
double doubleValue = 3.14159265359;  // 64-bit floating-point (15-16 significant digits precision)
decimal decimalValue = 3.14159265359m; // 128-bit high-precision decimal (28-29 significant digits)

// Boolean type
bool trueValue = true;
bool falseValue = false;

// Character type
char charValue = 'A';                // Unicode character
char unicodeChar = '\u0041';         // Unicode escape sequence for 'A'
char escapeChar = '\n';              // Newline escape sequence

// DateTime and TimeSpan
DateTime now = DateTime.Now;
DateTime utcNow = DateTime.UtcNow;
DateOnly today = DateOnly.FromDateTime(DateTime.Today); // Date without time (C# 10+)
TimeOnly noon = new TimeOnly(12, 0, 0);                 // Time without date (C# 10+)
DateTime specific = new DateTime(2023, 1, 1);
TimeSpan oneHour = TimeSpan.FromHours(1);
TimeSpan duration = TimeSpan.FromMinutes(90);

// Nullable types (can be null)
int? nullableInt = null;
bool? nullableBool = null;

// Default values
int defaultInt = default;            // 0
bool defaultBool = default;          // false
string defaultString = default;      // null
DateTime defaultDateTime = default;  // 0001-01-01 00:00:00

// Numeric type aliases (C# 12+)
using intptr = nint;               // Native-sized integer
using uintptr = nuint;             // Unsigned native-sized integer
using index = System.Index;        // Type alias for Index
```

Type inference with `var` (compile-time determined):

```csharp
var inferredInt = 42;                // Compiler infers int
var inferredString = "Hello";        // Compiler infers string
var inferredList = new List<int>();  // Compiler infers List<int>
```

Constants and readonly:

```csharp
// Compile-time constants (must be primitive types or string)
const double Pi = 3.14159;
const string AppName = "MyApp";

// Runtime constants
readonly DateTime StartTime = DateTime.Now;

// Static readonly - initialized only once at runtime
public static readonly HttpClient SharedClient = new HttpClient();

// Init-only setter - can only be set during initialization
public string Id { get; init; } = Guid.NewGuid().ToString();

// Read-only fields/properties with field/property initializers
public required string Name { get; init; }
```

**Additional resources:**

- [Built-in types (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types)
- [Value types (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types)
- [Reference types (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/reference-types)
- [Constants (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/const)
- [DateOnly and timeOnly types (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-6#dateonly-and-timeonly)

<div id="statements"></div>

# Statements

Statements are the building blocks of C# code execution, controlling the flow of your program and dictating how operations are carried out. Understanding these core language constructs is essential for effective C# programming.

## Control flow

Control flow statements allow you to make decisions and execute different code paths based on conditions.

### If-else statements

If-else statements execute different code blocks based on boolean conditions. They form the foundation of decision-making in C#.

```csharp
// Basic if statement
if (condition)
{
    // Code executed if condition is true
}

// If-else
if (temperature > 30)
{
    Console.WriteLine("It's hot outside");
}
else
{
    Console.WriteLine("It's not too hot");
}

// If-else if-else chain
if (temperature > 30)
{
    Console.WriteLine("It's hot outside");
}
else if (temperature > 20)
{
    Console.WriteLine("It's warm outside");
}
else if (temperature > 10)
{
    Console.WriteLine("It's cool outside");
}
else
{
    Console.WriteLine("It's cold outside");
}

// Conditional (ternary) operator - shorthand for simple if-else
string message = age >= 18 ? "Adult" : "Minor";

// Null-coalescing operator (??) - returns the left operand if it's not null, otherwise the right
string name = userName ?? "Anonymous";

// Null-conditional operator (?.) - safely accesses members of potentially null objects
int? length = customer?.Name?.Length;

// Null-coalescing assignment (??=) - C# 8.0+
// Assigns the right operand only if the left operand is null
userName ??= "Anonymous";
```

### Switch statements and expressions

Switch statements provide a way to handle multiple possible conditions for a single value. Modern C# also offers powerful switch expressions.

```csharp
// Traditional switch statement
switch (dayOfWeek)
{
    case DayOfWeek.Monday:
        Console.WriteLine("Start of work week");
        break;
    case DayOfWeek.Friday:
        Console.WriteLine("End of work week");
        break;
    case DayOfWeek.Saturday:
    case DayOfWeek.Sunday:
        Console.WriteLine("Weekend");
        break;
    default:
        Console.WriteLine("Midweek");
        break;
}

// Switch expression (C# 8.0+)
string GetDayType(DayOfWeek day) => day switch
{
    DayOfWeek.Monday => "Start of work week",
    DayOfWeek.Friday => "End of work week",
    DayOfWeek.Saturday or DayOfWeek.Sunday => "Weekend",
    _ => "Midweek"  // Default case
};

// Switch expression with pattern matching
string GetShapeDescription(object shape) => shape switch
{
    Circle c when c.Radius > 10 => "Large circle",
    Circle _ => "Circle",
    Rectangle { Width: 0 } => "Line",
    Rectangle { Length: var l, Width: var w } when l == w => "Square",
    Rectangle _ => "Rectangle",
    null => "No shape",
    _ => "Unknown shape"
};
```

## Loops

Loops allow you to execute a block of code repeatedly until a condition is met.

### For loops

For loops are ideal when you know the number of iterations in advance.

```csharp
// Basic for loop
for (int i = 0; i < 10; i++)
{
    Console.WriteLine($"Iteration {i}");
}

// Multiple loop variables
for (int i = 0, j = 10; i < j; i++, j--)
{
    Console.WriteLine($"i = {i}, j = {j}");
}

// Nested for loops
for (int i = 0; i < 3; i++)
{
    for (int j = 0; j < 3; j++)
    {
        Console.WriteLine($"Position [{i},{j}]");
    }
}

// Breaking out of a loop
for (int i = 0; i < 100; i++)
{
    if (i > 10)
        break;  // Exits the loop
    
    Console.WriteLine(i);
}

// Skipping an iteration
for (int i = 0; i < 10; i++)
{
    if (i % 2 == 0)
        continue;  // Skips to the next iteration
    
    Console.WriteLine($"Odd number: {i}");
}
```

### Foreach loops

Foreach loops are designed for iterating through collections and are simpler to use than for loops when the iteration count isn't important.

```csharp
// Basic foreach loop
foreach (string name in names)
{
    Console.WriteLine(name);
}

// Using index with foreach (C# 9.0+)
foreach (string name in names.Select((value, index) => new { value, index }))
{
    Console.WriteLine($"{name.index}: {name.value}");
}

// Iterating through key-value pairs
foreach (KeyValuePair<string, int> pair in dictionary)
{
    Console.WriteLine($"{pair.Key}: {pair.Value}");
}

// Using deconstruction with foreach (C# 7.0+)
foreach (var (key, value) in dictionary)
{
    Console.WriteLine($"{key}: {value}");
}

// Breaking and continuing also work in foreach
foreach (var item in collection)
{
    if (ShouldSkip(item))
        continue;
    
    if (ShouldStop(item))
        break;
    
    Process(item);
}
```

### While and do-while Loops

While loops check the condition before executing the loop body, while do-while loops execute the body at least once before checking the condition.

```csharp
// While loop - may execute zero times
while (condition)
{
    // Loop body
}

// Example: reading until a condition is met
while (!Console.KeyAvailable)
{
    // Process until a key is pressed
    ProcessData();
}

// Do-while loop - always executes at least once
do
{
    // Loop body
} while (condition);

// Example: menu system
string choice;
do
{
    DisplayMenu();
    choice = Console.ReadLine();
    ProcessChoice(choice);
} while (choice != "exit");
```

## Lock statement

The lock statement prevents multiple threads from accessing a shared resource simultaneously, helping to avoid race conditions in multithreaded code.

```csharp
// Define a lock object (private to avoid external locking)
private readonly object _lockObject = new object();

// Using the lock statement
public void AddItem(string item)
{
    lock (_lockObject)
    {
        // This code can only be executed by one thread at a time
        _items.Add(item);
        _count++;
    }
}

```

**Best practices for locks:**
1. Use a private object for locking
2. Keep the locked section as small as possible
3. Avoid locking on 'this' or public objects
4. Don't execute long-running or blocking operations inside a lock
5. Consider using higher-level synchronization primitives for complex scenarios

## Using statement

The `using` statement ensures that disposable resources are properly cleaned up, even if exceptions occur. It's an essential pattern for working with resources like files, network connections, and database connections that need to be explicitly released.

```csharp
// Traditional using statement
using (StreamReader reader = new StreamReader("file.txt"))
{
    string content = reader.ReadToEnd();
    // reader is automatically disposed here, even if an exception occurs
}

// Using declaration (C# 8.0+)
using StreamWriter writer = new StreamWriter("output.txt");
writer.WriteLine("Hello, World!");
// writer is disposed at the end of the scope

// Multiple resources in one using statement
using (var connection = new SqlConnection(connectionString))
using (var command = new SqlCommand(queryString, connection))
{
    connection.Open();
    using (var reader = command.ExecuteReader())
    {
        // Process data
    }
}

// Using declaration with multiple resources (C# 8.0+)
using var fileStream = new FileStream("data.bin", FileMode.Create);
using var binaryWriter = new BinaryWriter(fileStream);
binaryWriter.Write(42);
// Both binaryWriter and fileStream are disposed at end of scope
```

## Unsafe code

The unsafe keyword allows you to write code that directly manipulates memory. This is primarily used for performance-critical operations or interop with native code.

```csharp
// Must enable unsafe code in project settings or compiler options
// <AllowUnsafeBlocks>true</AllowUnsafeBlocks> in .csproj

// Unsafe method
public unsafe void ProcessBuffer(byte[] buffer)
{
    fixed (byte* ptr = buffer)
    {
        // Direct memory manipulation
        for (int i = 0; i < buffer.Length; i++)
        {
            *(ptr + i) = (byte)(*(ptr + i) * 2);
        }
    }
}

// Unsafe context with pointer operations
unsafe
{
    int value = 10;
    int* pointer = &value;
    
    Console.WriteLine($"Value: {*pointer}");
    
    // Increment the value through the pointer
    *pointer = 20;
    Console.WriteLine($"Updated value: {value}");
}

// sizeof operator (only allowed in unsafe context)
unsafe
{
    Console.WriteLine($"Size of int: {sizeof(int)} bytes");
    Console.WriteLine($"Size of double: {sizeof(double)} bytes");
}
```

## Yield statement

The yield statement is used in iterator methods to provide values one at a time, enabling deferred execution and efficient handling of sequences.

```csharp
// Simple iterator method
public IEnumerable<int> GetNumbers(int count)
{
    for (int i = 0; i < count; i++)
    {
        yield return i;
    }
}

// Iterator method with conditional logic
public IEnumerable<int> GetEvenNumbers(int max)
{
    for (int i = 0; i <= max; i++)
    {
        if (i % 2 == 0)
        {
            yield return i;
        }
    }
}

// Yield break to exit early
public IEnumerable<int> GetNumbersUntil(int max, int stopAt)
{
    for (int i = 0; i <= max; i++)
    {
        if (i == stopAt)
        {
            yield break;  // Exit the iterator
        }
        
        yield return i;
    }
}

// Using yield to implement filtering
public IEnumerable<T> Where<T>(IEnumerable<T> source, Func<T, bool> predicate)
{
    foreach (var item in source)
    {
        if (predicate(item))
        {
            yield return item;
        }
    }
}
```

### Benefits of yield:

1. **Lazy evaluation**: Results are computed only when needed
2. **Memory efficiency**: No need to build the entire collection at once
3. **Composability**: Iterator methods can be chained together
4. **Simplicity**: Easier to write than manually implementing IEnumerator

**Additional resources:**
- [C# Statements (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/statements)
- [Control Flow (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements)
- [Iteration statements (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements)
- [Lock statement (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/lock)
- [Using statement (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/using)
- [Unsafe code (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/unsafe)
- [Yield (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/yield)

<div id="methods-and-functions"></div>

# Methods and functions

Methods are the fundamental building blocks of C# programs that encapsulate behavior and logic. They provide a way to organize code into reusable units, improving maintainability and readability. 

C# offers various ways to define methods with different parameter types, return values, and syntax options to accommodate different programming styles and needs.

## Basic method syntax

```csharp
// Instance method
public int Add(int a, int b)
{
    return a + b;
}

// Static method
public static double CalculateArea(double radius)
{
    return Math.PI * radius * radius;
}

// Void method (no return value)
public void PrintMessage(string message)
{
    Console.WriteLine(message);
}
```

## Expression-bodied members (C# 6.0+)

Expression-bodied members provide a concise syntax for methods, properties, and other members that can be represented by a single expression.

```csharp
// Expression-bodied method (one-line methods)
public int Multiply(int a, int b) => a * b;

// Expression-bodied property
public string FullName => $"{FirstName} {LastName}";
```

## Method parameters

C# provides flexible parameter passing options to handle different programming scenarios.

```csharp
// Optional parameters
public void Greet(string name, string greeting = "Hello")
{
    Console.WriteLine($"{greeting}, {name}!");
}

// Named arguments
Greet(greeting: "Hi", name: "Alice");

// Ref parameters (pass by reference)
public void Swap(ref int a, ref int b)
{
    int temp = a;
    a = b;
    b = temp;
}
// Usage: Swap(ref x, ref y);

// Out parameters (for returning multiple values)
public bool TryParse(string input, out int result)
{
    return int.TryParse(input, out result);
}
// Usage: bool success = TryParse("123", out int number);

// In parameters (read-only reference - C# 7.2+)
public double CalculateDistance(in Point p1, in Point p2)
{
    // p1 and p2 cannot be modified
    return Math.Sqrt(Math.Pow(p2.X - p1.X, 2) + Math.Pow(p2.Y - p1.Y, 2));
}

// Params array (variable number of arguments)
public int Sum(params int[] numbers)
{
    int total = 0;
    foreach (int number in numbers)
    {
        total += number;
    }
    return total;
}
// Usage: Sum(1, 2, 3, 4, 5);
```

## Local functions (C# 7.0+)

Local functions allow you to define methods inside other methods, encapsulating helper logic that is only relevant to the containing method.

```csharp
public int Factorial(int n)
{
    // Local function defined inside another method
    int CalculateFactorial(int number)
    {
        if (number <= 1) return 1;
        return number * CalculateFactorial(number - 1);
    }
    
    return CalculateFactorial(n);
}
```

## Extension methods

Extension methods allow you to add methods to existing types without modifying the original type, making them particularly useful for extending types you don't control.

```csharp
// Must be defined in a non-nested, non-generic static class
public static class StringExtensions
{
    // Extension method for string type
    public static bool IsNullOrEmpty(this string value)
    {
        return string.IsNullOrEmpty(value);
    }
    
    // Extension method with parameters
    public static string Truncate(this string value, int maxLength)
    {
        if (string.IsNullOrEmpty(value)) return value;
        return value.Length <= maxLength ? value : value.Substring(0, maxLength);
    }
}

// Usage
string text = "Hello, World!";
bool isEmpty = text.IsNullOrEmpty(); // false
string truncated = text.Truncate(5); // "Hello"
```

## Lambda expressions

Lambda expressions provide a concise way to create anonymous functions, especially useful for LINQ queries, event handlers, and functional programming patterns.

```csharp
// Func delegate (takes parameters, returns a value)
Func<int, int, int> add = (a, b) => a + b;
int sum = add(2, 3); // 5

// Action delegate (takes parameters, returns void)
Action<string> print = message => Console.WriteLine(message);
print("Hello!"); // Prints "Hello!"

// Predicate delegate (takes parameters, returns bool)
Predicate<int> isEven = number => number % 2 == 0;
bool result = isEven(4); // true

// Multi-line lambda
Func<int, int> factorial = n =>
{
    int result = 1;
    for (int i = 1; i <= n; i++)
    {
        result *= i;
    }
    return result;
};
```

### Default parameters in lambdas (C# 12)

Lambdas can now have default values for parameters:

```csharp
Func<int, int, int> add = (x, y = 10) => x + y;
int result = add(5); // 15
```

## Method overloading

Method overloading allows multiple methods with the same name but different parameter lists, providing flexibility in how a method can be called.

```csharp
// Method overloading (same name, different parameters)
public void Display(int value)
{
    Console.WriteLine($"Integer: {value}");
}

public void Display(string value)
{
    Console.WriteLine($"String: {value}");
}

public void Display(int value, string format)
{
    Console.WriteLine($"Formatted: {value.ToString(format)}");
}
```

**Additional resources:**

- [Methods (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/methods)
- [Expression-bodied members (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members)
- [Method parameters (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters)
- [Extension methods (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)
- [Lambda expressions (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions)

<div id="delegates-and-events"></div>

# Delegates and events

**Delegates** are type-safe pointers to methods, enabling flexible method invocation. They are often used for callbacks, event handling, and implementing the observer pattern. Delegates can point to static or instance methods and can be multicast (pointing to multiple methods).

```csharp
public delegate int Operation(int x, int y);

public int Add(int a, int b) => a + b;
public int Multiply(int a, int b) => a * b;

// Usage
Operation op = Add;
int result = op(3, 4); // 7
op += Multiply; // Multicast delegate
```

**Events** are built on delegates and provide a way for classes to notify subscribers when something happens. Events are typically used in GUI applications and other scenarios where you want to decouple the event source from the event handler.

```csharp:
public class Button
{
    public event EventHandler Clicked;

    protected virtual void OnClicked() =>
        Clicked?.Invoke(this, EventArgs.Empty);
}

// Usage
var button = new Button();
button.Clicked += (sender, args) => Console.WriteLine("Clicked!");
```

**Additional resources**:

- [Delegates (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/delegates/)
- [Events (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/events-overview)

<div id="data-types"></div>

# Data types

C# supports a variety of composite data types to organize and represent data.

## Classes

Classes are reference types that encapsulate data and behavior.

```csharp
// Basic class definition
public class Person
{
    // Fields
    private string name;
    private int age;
    
    // Properties
    public string Name 
    { 
        get { return name; }
        set { name = value; } 
    }
    
    // Auto-implemented property
    public int Age { get; set; }
    
    // Read-only property
    public bool IsAdult => Age >= 18;
    
    // Constructors
    public Person()
    {
        // Default constructor
    }
    
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
    
    // Methods
    public void Introduce()
    {
        Console.WriteLine($"Hello, my name is {Name} and I'm {Age} years old.");
    }
    
    public string GetDescription() => $"{Name}, {Age} years old";
    
    // Static members
    public static int MinimumAge { get; } = 0;
    
    public static bool IsValidAge(int age)
    {
        return age >= MinimumAge;
    }
}

// Usage
Person person = new Person();
person.Name = "Alice";
person.Age = 30;
person.Introduce();

Person bob = new Person("Bob", 25);
string description = bob.GetDescription();
bool isAdult = bob.IsAdult;

bool isValid = Person.IsValidAge(20);
```

## Structs

Structs are value types and are suitable for small, immutable data structures.

Note that you cannot give initial values to a struct unless you make it static or const.

```csharp
// Basic struct definition
public struct Point
{
    // Fields
    public double X { get; set; }
    public double Y { get; set; }
    
    // Constructor
    public Point(double x, double y)
    {
        X = x;
        Y = y;
    }
    
    // Methods
    public double DistanceFromOrigin()
    {
        return Math.Sqrt(X * X + Y * Y);
    }
    
    // Override ToString method
    public override string ToString() => $"({X}, {Y})";
}

// Usage
Point point = new Point(3, 4);
double distance = point.DistanceFromOrigin(); // 5
```

## Records (C# 9.0+)

Records are reference types designed for representing immutable data.

```csharp
// Positional record (concise syntax)
public record Person(string FirstName, string LastName, int Age);

// Usage
var person1 = new Person("John", "Doe", 30);
var person2 = new Person("John", "Doe", 30);

// Records have value-based equality
bool areEqual = person1 == person2; // true

// Non-destructive mutation with 'with' expression
var person3 = person1 with { Age = 31 };

// Records can also be defined with standard syntax for more flexibility
public record Employee
{
    public string FirstName { get; init; }
    public string LastName { get; init; }
    public int Id { get; init; }
    
    // Additional members can be defined
    public string FullName => $"{FirstName} {LastName}";
}
```

## Record structs (C# 10.0+)

Record structs combine the value semantics of structs with the special features of records.

```csharp
// Record struct
public record struct Point(double X, double Y);

// Mutable record struct
public record struct MutablePoint
{
    public double X { get; set; }
    public double Y { get; set; }
    
    public double Distance => Math.Sqrt(X * X + Y * Y);
}
```

## Interfaces

Interfaces define a contract that classes can implement.

```csharp
// Interface definition
public interface IShape
{
    double Area { get; }
    double Perimeter { get; }
    void Draw();
    string GetDescription() => $"Shape with area {Area} and perimeter {Perimeter}"; // Default implementation (C# 8.0+)
}

// Implementing an interface
public class Circle : IShape
{
    public double Radius { get; }
    
    public Circle(double radius)
    {
        Radius = radius;
    }
    
    public double Area => Math.PI * Radius * Radius;
    public double Perimeter => 2 * Math.PI * Radius;
    
    public void Draw()
    {
        Console.WriteLine("Drawing a circle");
    }
    
    // Override default implementation
    public string GetDescription() => $"Circle with radius {Radius}";
}
```

From C# 8.0, interfaces can have **default implementations for methods and properties**, allowing you to provide a base implementation that can be overridden by implementing classes.

```csharp
public interface ILogger
{
    void Log(string message);
    
    // Default implementation
    void LogError(string message) => Log($"ERROR: {message}");
    void LogWarning(string message) => Log($"WARNING: {message}");
    
    // Static method in interface
    static string FormatMessage(string level, string message) => $"[{level}] {message}";
}

// Implement only required methods
public class MinimalLogger : ILogger
{
    public void Log(string message)
    {
        Console.WriteLine(message);
    }
    
    // Other methods use default implementations
}
```

## Enums

Enums define a set of named constants.

```csharp
// Basic enum
public enum DayOfWeek
{
    Sunday,     // 0
    Monday,     // 1
    Tuesday,    // 2
    Wednesday,  // 3
    Thursday,   // 4
    Friday,     // 5
    Saturday    // 6
}

// Enum with explicit values
public enum HttpStatusCode
{
    OK = 200,
    Created = 201,
    BadRequest = 400,
    Unauthorized = 401,
    NotFound = 404,
    InternalServerError = 500
}

// Enum with flags attribute (for bitwise operations)
[Flags]
public enum Permissions
{
    None = 0,
    Read = 1,
    Write = 2,
    Execute = 4,
    All = Read | Write | Execute
}

// Usage
DayOfWeek today = DayOfWeek.Monday;
HttpStatusCode status = HttpStatusCode.OK;

// Convert between enum and integer
int dayValue = (int)today;
DayOfWeek convertedDay = (DayOfWeek)3; // Wednesday

// Parsing from string
DayOfWeek parsed = Enum.Parse<DayOfWeek>("Friday");
bool success = Enum.TryParse("Sunday", out DayOfWeek result);

// Using flags
Permissions userPermissions = Permissions.Read | Permissions.Write;
bool canRead = userPermissions.HasFlag(Permissions.Read); // true
bool canExecute = userPermissions.HasFlag(Permissions.Execute); // false
```

## Tuples

Tuples group multiple values without defining a specific type.

```csharp
// Creating tuples (C# 7.0+)
(int, string) pair = (1, "one");
var person = (Name: "Alice", Age: 30);

// Accessing tuple elements
int id = pair.Item1;
string value = pair.Item2;
string name = person.Name;
int age = person.Age;

// Tuple deconstruction
var (newId, newValue) = pair;
var (newName, newAge) = person;

// Using tuples as method return values
(int Min, int Max) FindMinMax(int[] numbers)
{
    return (numbers.Min(), numbers.Max());
}

var result = FindMinMax(new[] { 1, 2, 3, 4, 5 });
Console.WriteLine($"Min: {result.Min}, Max: {result.Max}");

// Tuple as method parameter
void ProcessData((string Name, int Age) person)
{
    Console.WriteLine($"Processing data for {person.Name}, {person.Age}");
}
```

## Nullable types

Nullable types represent values that can be null.

```csharp
// Nullable value types
int? nullableInt = null;
double? nullableDouble = 3.14;

// Checking for null
if (nullableInt.HasValue)
{
    int value = nullableInt.Value;
}

// Null-coalescing operator
int result = nullableInt ?? 0; // If nullableInt is null, use 0

// Nullable reference types (C# 8.0+)
// Enable with: #nullable enable
string? nullableString = null;
string nonNullableString = "Hello"; // Cannot be null

// Null-conditional operator
int? length = nullableString?.Length; // null if nullableString is null

// Null-coalescing assignment (C# 8.0+)
nullableString ??= "Default";
```

<div id="generics"></div>

# Generics

Generics let you define type-safe, reusable classes, methods, and interfaces. They improve code reuse, type safety, and performance by avoiding boxing/unboxing overhead.

**Generic class**:

```csharp
public class Repository<T>
{
    private readonly List<T> _items = new();

    public void Add(T item) => _items.Add(item);
    public T Get(int index) => _items[index];
}

// Usage
var intRepo = new Repository<int>();
intRepo.Add(42);
int number = intRepo.Get(0);
```

**Generic methods**:

```csharp
public T Echo<T>(T input) => input;

// Usage
string message = Echo("Hello");
int number = Echo(123);
```

**Constraints (limit generic types)**:

```csharp
public class EmployeeRepository<T> where T : Employee, new()
{
    public T Create() => new T();
}
```

**Additional resources**:

- [Generics (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/generics)

<div id="classes-and-inheritance"></div>

# Classes and Inheritance

**Classes** are the foundation of object-oriented programming in C#, serving as blueprints for creating objects that encapsulate data and behavior. 

**Inheritance** is a powerful mechanism that enables code reuse and polymorphism by allowing classes to inherit attributes and methods from parent classes. 

Proper use of these features helps create maintainable, extensible code with clear hierarchies.

## Constructors and initialization

Constructors are special methods that initialize objects. They set initial state, enforce invariants, and can chain to other constructors to share initialization logic. Understanding constructor patterns is essential for creating maintainable class hierarchies.

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
    
    // Default constructor
    public Person()
    {
        Name = "Unknown";
        Age = 0;
    }
    
    // Parameterized constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
    
    // Static constructor (called once before type is used)
    static Person()
    {
        Console.WriteLine("Person type initialized");
    }
}

// Constructor chaining
public class Employee : Person
{
    public string Department { get; set; }
    
    // Call the base class constructor
    public Employee(string name, int age, string department) 
        : base(name, age)
    {
        Department = department;
    }
    
    // Chain to another constructor in the same class
    public Employee(string name, int age)
        : this(name, age, "General")
    {
    }
}
```

## Primary constructors (C# 12+)

Primary constructors are a new feature in C# 12 that simplify class initialization by allowing constructor parameters to be defined directly in the class declaration. This reduces boilerplate code and makes the relationship between constructor parameters and class members more explicit.

```csharp
// Class with primary constructor
public class Person(string name, int age)
{
    // Properties initialized by primary constructor parameters
    public string Name { get; } = name;
    public int Age { get; } = age;
    
    // Can use constructor parameters directly in methods
    public string Introduce() => $"My name is {name} and I'm {age} years old";
    
    // Can still have additional constructors
    public Person(string name) : this(name, 0)
    {
        Console.WriteLine("Created a person with default age");
    }
}

// Inheritance with primary constructors
public class Employee(string name, int age, string department) : Person(name, age)
{
    public string Department { get; } = department;
    
    // Using base constructor parameters
    public override string Introduce() => $"{base.Introduce()} working in {department}";
}

// Usage
var alice = new Person("Alice", 30);
var bob = new Employee("Bob", 25, "Engineering");
```

## Inheritance

Inheritance allows a class (derived class) to inherit properties, methods, and events from another class (base class). This promotes code reuse and establishes an "is-a" relationship between classes. In C#, a class can inherit from only one base class but can implement multiple interfaces.

```csharp
// Base class
public class Animal
{
    public string Name { get; set; }
    
    public Animal(string name)
    {
        Name = name;
    }
    
    public virtual void MakeSound()
    {
        Console.WriteLine("Some generic animal sound");
    }
    
    // Non-overridable method
    public void Sleep()
    {
        Console.WriteLine($"{Name} is sleeping");
    }
}

// Derived class
public class Dog : Animal
{
    public string Breed { get; set; }
    
    public Dog(string name, string breed) : base(name)
    {
        Breed = breed;
    }
    
    // Override base class method
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
    
    // New method
    public void Fetch()
    {
        Console.WriteLine($"{Name} is fetching the ball");
    }
}
```

## Abstract classes

Abstract classes serve as incomplete templates that cannot be instantiated directly but must be inherited by concrete classes. They're useful when you want to define common functionality while forcing derived classes to implement specific methods. An abstract class can have both abstract members (without implementation) and concrete members (with implementation).

```csharp
// Abstract class
public abstract class Shape
{
    // Abstract property (must be implemented)
    public abstract double Area { get; }
    
    // Abstract method (must be implemented)
    public abstract double Perimeter();
    
    // Concrete method
    public void PrintInfo()
    {
        Console.WriteLine($"Area: {Area}, Perimeter: {Perimeter()}");
    }
}

// Concrete implementation
public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }
    
    public Rectangle(double width, double height)
    {
        Width = width;
        Height = height;
    }
    
    public override double Area => Width * Height;
    
    public override double Perimeter() => 2 * (Width + Height);
}
```

## Sealed classes and members

Sealed classes prevent inheritance, making them useful for security-sensitive classes or when inheritance would break functionality. Sealed methods prevent further overriding in derived classes, ensuring that specific implementations remain unchanged throughout the inheritance chain.

```csharp
// Sealed class (cannot be inherited)
public sealed class Utility
{
    public static void DoSomething() { }
}

public class Base
{
    // Virtual method that can be overridden
    public virtual void Method1() { }
    
    // Virtual method that can be overridden
    public virtual void Method2() { }
}

public class Derived : Base
{
    public override void Method1() { }
    
    // Sealed method (can't be overridden further in inheritance chain)
    public sealed override void Method2() { }
}

public class Further : Derived
{
    public override void Method1() { } // OK
    // public override void Method2() { } // Error: cannot override sealed method
}
```

## Polymorphism

Polymorphism allows objects to be treated as instances of their parent class rather than their actual type. This enables more flexible and extensible code by letting you write methods that operate on base classes but respond differently based on the actual object type at runtime.

```csharp
// Base class reference can refer to derived class objects
Animal myPet = new Dog("Fido", "Beagle");
myPet.MakeSound(); // Outputs "Woof!"

// Array of base class can hold derived objects
Animal[] animals = new Animal[]
{
    new Dog("Fido", "Beagle"),
    new Cat("Whiskers"),
    new Rabbit("Hopper")
};

// Polymorphic behavior
foreach (Animal animal in animals)
{
    Console.WriteLine($"{animal.Name} says:");
    animal.MakeSound(); // Each animal makes its own sound
}

// Type checking and casting
if (animals[0] is Dog dog)
{
    dog.Fetch(); // Access Dog-specific method
}

// Explicit casting
Dog anotherDog = (Dog)animals[0];
```

When designing class hierarchies, consider these guidelines:
- Use inheritance when there is a true "is-a" relationship between classes
- Prefer composition over inheritance for "has-a" relationships
- Use abstract classes when you want to provide common behavior with forced specialization
- Use sealed classes for security-sensitive code or to prevent unintended inheritance
- Implement interfaces for defining capabilities that can be shared across unrelated classes

**Additional resources:**

- [Classes and objects (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/classes-and-objects)
- [Inheritance (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/inheritance)
- [Abstract classes and methods (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/abstract)
- [Primary constructors (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-12.0/primary-constructors)
- [C# object-oriented programming best practices (Microsoft Learn)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/object-oriented-programming)


<div id="collections"></div>

# Collections

Collections in C# provide powerful ways to store, manage, and manipulate groups of related objects. The .NET framework offers various collection types optimized for different scenarios, from simple arrays to complex specialized collections. Choosing the right collection type is essential for writing efficient and maintainable code.

## Collection Expressions (C# 12+)

Collection expressions are a concise way to initialize collections, introduced in C# 12. They provide a unified syntax for creating and initializing different collection types.

```csharp
// Creating collections with the new collection expressions syntax
int[] numbers = [1, 2, 3, 4, 5];                   // Array
List<string> names = ["Alice", "Bob", "Charlie"];  // List
HashSet<char> letters = ['a', 'b', 'c'];           // HashSet
Dictionary<string, int> ages = [                   // Dictionary
    "Alice" => 30,
    "Bob" => 25,
    "Charlie" => 35
];

// Spread operator - combining collections
int[] moreNumbers = [0, .. numbers, 6];     // [0, 1, 2, 3, 4, 5, 6]
string[] firstThree = [.. names[0..3]];     // ["Alice", "Bob", "Charlie"]

// Pattern matching with collection expressions
bool IsValidPoint(int[] point) => point is [var x, var y] && x >= 0 && y >= 0;
```

## Arrays

Arrays are fixed-size collections of elements of the same type. They provide efficient random access but have a predetermined size that cannot change after creation.

```csharp
// Declaration and initialization
int[] numbers = new int[5];                      // Array of 5 integers with default values (0)
int[] initialized = new int[] { 1, 2, 3, 4, 5 }; // Initialized array
int[] shorthand = { 1, 2, 3, 4, 5 };             // Shorthand initialization
string[] names = { "Alice", "Bob", "Charlie" };

// Accessing elements
int firstNumber = numbers[0];                     // First element (zero-based indexing)
numbers[0] = 10;                                  // Assign value to first element

// Multi-dimensional arrays
int[,] matrix = new int[3, 3];                    // 3x3 2D array
matrix[0, 0] = 1;                                 // Assign to specific position
int[,] initialized2D = {                          // Initialize 2D array
    { 1, 2, 3 },
    { 4, 5, 6 },
    { 7, 8, 9 }
};

// Jagged arrays (arrays of arrays)
int[][] jagged = new int[3][];
jagged[0] = new int[] { 1, 2, 3 };
jagged[1] = new int[] { 4, 5 };
jagged[2] = new int[] { 6, 7, 8, 9 };

// Array properties and methods
int length = numbers.Length;                      // Number of elements
Array.Sort(numbers);                              // Sort array in-place
Array.Reverse(numbers);                           // Reverse array in-place
int index = Array.IndexOf(names, "Bob");          // Find index of element
bool exists = Array.Exists(numbers, n => n > 10); // Check if condition exists
```

## Lists

Lists are dynamic arrays that can grow or shrink in size. They provide flexibility and are generally the go-to collection type for most scenarios when you need a sequence of elements.

```csharp
using System.Collections.Generic;

// Create a list
List<string> names = new List<string>();          // Empty list
List<int> numbers = new List<int> { 1, 2, 3 };    // Initialized list

// Add elements  
names.Add("Alice");                               // Add single element
names.AddRange(new[] { "Bob", "Charlie" });       // Add multiple elements

// Access elements
string first = names[0];                          // Access by index
names[0] = "Alicia";                              // Modify by index

// Remove elements
names.Remove("Bob");                              // Remove specific element
names.RemoveAt(0);                                // Remove element at index
names.RemoveAll(x => x.StartsWith("C"));          // Remove all that match condition
names.Clear();                                    // Remove all elements

// Search and query
bool contains = numbers.Contains(2);              // Check if contains value
int index = numbers.IndexOf(3);                   // Find index of element
List<int> filtered = numbers.FindAll(n => n > 1); // Find all matching elements
int found = numbers.Find(n => n > 2);             // Find first matching element

// Other operations
int count = numbers.Count;                       // Number of elements
numbers.Sort();                                  // Sort list in-place
numbers.Reverse();                               // Reverse list in-place
numbers.ForEach(n => Console.WriteLine(n));      // Perform action on each element
```

## Dictionary

Dictionaries store key-value pairs for fast lookups by key. They are essential when you need to quickly access values based on unique identifiers.

```csharp
using System.Collections.Generic;

// Create a dictionary
Dictionary<string, int> ages = new Dictionary<string, int>();
Dictionary<string, string> capitals = new Dictionary<string, string>
{
    { "USA", "Washington D.C." },
    { "UK", "London" },
    ["France"] = "Paris"              // Alternative initialization syntax
};

// Add entries
ages.Add("Alice", 30);
ages["Bob"] = 25;                     // Add or update using indexer

// Access values
int aliceAge = ages["Alice"];         // Access by key (throws if not found)
bool success = ages.TryGetValue("Charlie", out int charlieAge); // Safe access

// Check existence
bool containsKey = ages.ContainsKey("Alice");
bool containsValue = ages.ContainsValue(25);

// Remove entries
bool removed = ages.Remove("Bob");

// Iterate through dictionary
foreach (KeyValuePair<string, int> pair in ages)
{
    Console.WriteLine($"{pair.Key}: {pair.Value}");
}

// Or using deconstruction (C# 7.0+)
foreach (var (name, age) in ages)
{
    Console.WriteLine($"{name}: {age}");
}
```

## HashSet

HashSets store unique elements with fast lookup, insertion, and deletion. They're ideal for maintaining collections of unique items or performing set operations.

```csharp
using System.Collections.Generic;

// Create a HashSet
HashSet<int> uniqueNumbers = new HashSet<int>();
HashSet<string> fruits = new HashSet<string> { "Apple", "Banana", "Orange" };

// Add elements
uniqueNumbers.Add(1);                 // Returns true if added
uniqueNumbers.Add(1);                 // Returns false (already exists)
uniqueNumbers.UnionWith(new[] { 2, 3, 4 }); // Add multiple elements

// Check membership
bool contains = fruits.Contains("Apple"); // Fast lookup

// Remove elements
bool removed = fruits.Remove("Banana");

// Set operations
HashSet<int> setA = new HashSet<int> { 1, 2, 3 };
HashSet<int> setB = new HashSet<int> { 3, 4, 5 };

setA.UnionWith(setB);                 // Union: { 1, 2, 3, 4, 5 }
setA.IntersectWith(setB);             // Intersection: { 3 }
setA.ExceptWith(setB);                // Difference: { 1, 2 }
setA.SymmetricExceptWith(setB);       // Symmetric difference: { 1, 2, 4, 5 }

bool isSubset = setA.IsSubsetOf(setB);
bool isSuperset = setA.IsSupersetOf(setB);
```

## Queue and Stack

Queues (FIFO - first in, first out) and Stacks (LIFO - last in, first out) are specialized collections that support specific access patterns common in many algorithms and data processing scenarios.

```csharp
using System.Collections.Generic;

// Queue (First In, First Out)
Queue<string> queue = new Queue<string>();
queue.Enqueue("First");               // Add to end
queue.Enqueue("Second");
queue.Enqueue("Third");

string next = queue.Peek();           // View next item without removing
string dequeued = queue.Dequeue();    // Remove and return next item
int count = queue.Count;              // Number of items
bool contains = queue.Contains("Second");

// Stack (Last In, First Out)
Stack<int> stack = new Stack<int>();
stack.Push(1);                        // Add to top
stack.Push(2);
stack.Push(3);

int top = stack.Peek();               // View top item without removing
int popped = stack.Pop();             // Remove and return top item
int stackCount = stack.Count;         // Number of items
bool stackContains = stack.Contains(2);
```

## LINQ (Language Integrated Query)

LINQ provides powerful query capabilities for collections, making it easier to filter, transform, and aggregate data. It brings database-like query operations to in-memory collections.

```csharp
using System.Linq;

List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

// Filtering
var evens = numbers.Where(n => n % 2 == 0);        // [2, 4, 6, 8, 10]
var greaterThanFive = numbers.Where(n => n > 5);   // [6, 7, 8, 9, 10]

// Transformation
var doubled = numbers.Select(n => n * 2);          // [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
var numberObjects = numbers.Select(n => new { Value = n, IsEven = n % 2 == 0 });

// Ordering
var ascending = numbers.OrderBy(n => n);           // [1, 2, 3, ...]
var descending = numbers.OrderByDescending(n => n); // [10, 9, 8, ...]
var complex = numbers.OrderBy(n => n % 3).ThenByDescending(n => n); // Multiple criteria

// Aggregation
int sum = numbers.Sum();                           // 55
int min = numbers.Min();                           // 1
int max = numbers.Max();                           // 10
double average = numbers.Average();                // 5.5
int product = numbers.Aggregate((a, b) => a * b);  // 3628800 (factorial of 10)

// Quantifiers
bool allEven = numbers.All(n => n % 2 == 0);       // false
bool anyEven = numbers.Any(n => n % 2 == 0);       // true
bool containsSeven = numbers.Contains(7);          // true

// Partitioning
var firstThree = numbers.Take(3);                  // [1, 2, 3]
var skipFirstThree = numbers.Skip(3);              // [4, 5, 6, 7, 8, 9, 10]
var takeLast = numbers.TakeLast(2);                // [9, 10]
var skipLast = numbers.SkipLast(2);                // [1, 2, 3, 4, 5, 6, 7, 8]

// Element operations
int first = numbers.First();                       // 1
int firstEven = numbers.First(n => n % 2 == 0);    // 2
int lastOdd = numbers.Last(n => n % 2 != 0);       // 9
int single = numbers.Where(n => n == 5).Single();  // 5

// Grouping
var groups = numbers.GroupBy(n => n % 3);          // Groups by remainder when divided by 3
foreach (var group in groups)
{
    Console.WriteLine($"Remainder {group.Key}: {string.Join(", ", group)}");
}

// Query syntax (alternative to method syntax)
var queryResult = from n in numbers
                  where n > 5
                  orderby n descending
                  select n * 2;
```

**Additional resources:**

- [Collections overview (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/standard/collections/)
- [Collection expressions (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/collection-expressions)
- [LINQ (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/)
- [Choosing a collection type (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/standard/collections/selecting-a-collection-class)
- [System.Collections.Generic Namespace (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic)

<div id="pattern-matching"></div>

# Pattern matching

C# supports various pattern matching techniques for more expressive conditional logic.

## Type patterns

```csharp
// Type pattern - check if object is of a specific type
object value = "Hello";

if (value is string text)
{
    // 'text' is the value cast to string, available in this scope
    Console.WriteLine(text.ToUpper());
}

// Switch expression with type patterns (C# 8.0+)
string GetDisplayName(object item) => item switch
{
    Person p => $"Person: {p.Name}",
    DateTime d => $"Date: {d.ToShortDateString()}",
    int i => $"Number: {i}",
    string s => $"Text: {s}",
    null => "Null value",
    _ => "Unknown type" // Default case
};
```

## Property patterns

```csharp
// Property pattern to match object properties
if (person is { Name: "Alice", Age: >= 30 })
{
    Console.WriteLine("Found Alice who is 30 or older");
}

// Switch expression with property patterns
string GetAgeCategory(Person person) => person switch
{
    { Age: < 13 } => "Child",
    { Age: < 20 } => "Teenager",
    { Age: < 65 } => "Adult",
    _ => "Senior"
};

// Nested property patterns
if (order is { Customer: { Name: "Alice" } })
{
    Console.WriteLine("This is Alice's order");
}
```

## Tuple patterns

```csharp
// Tuple pattern
(int x, int y) = (5, 10);

string GetQuadrant(int x, int y) => (x, y) switch
{
    (> 0, > 0) => "First quadrant",
    (< 0, > 0) => "Second quadrant",
    (< 0, < 0) => "Third quadrant",
    (> 0, < 0) => "Fourth quadrant",
    (0, 0) => "Origin",
    (_, 0) => "X-axis",
    (0, _) => "Y-axis"
};
```

## Logical patterns

```csharp
// 'and', 'or', and 'not' patterns (C# 9.0+)
if (person is { Age: > 20 and < 30, Name: "Alice" or "Bob" })
{
    Console.WriteLine("Person is between 20-30 and named Alice or Bob");
}

// In switch expression
string CheckValue(int value) => value switch
{
    > 0 and < 10 => "Single digit positive",
    >= 10 and < 100 => "Double digit positive",
    < 0 and not -1 => "Negative, but not -1",
    0 or -1 => "Zero or negative one",
    _ => "Other"
};
```

## List patterns (C# 11.0+)

```csharp
// List pattern in C# 11
var numbers = new[] { 1, 2, 3, 4 };

bool IsFirstTwoPositive(int[] numbers) => numbers is [> 0, > 0, ..];

string DescribeArray(int[] arr) => arr switch
{
    [] => "Empty array",
    [var single] => $"Single item: {single}",
    [var first, var second] => $"Two items: {first}, {second}",
    [var first, .. var middle, var last] => $"Multiple items, starts with {first}, ends with {last}",
    _ => "Unknown pattern"
};
```

## Discard pattern

```csharp
// Discard pattern (underscore) to ignore values
string GetSign(int number) => number switch
{
    < 0 => "Negative",
    > 0 => "Positive",
    _ => "Zero"
};

// Multiple discards
(string, int) person = ("Alice", 30);
var (name, _) = person; // Discard the age
```

<div id="exceptions"></div>

# Exceptions

Exception handling is a critical aspect of robust C# applications, which allows you to manage errors and unexpected conditions. Well-designed exception handling balances providing useful feedback to users, maintaining application stability, and preserving valuable diagnostic information for developers.

## Try-Catch-Finally

The try-catch-finally pattern forms the backbone of exception handling in C#. Code that might throw exceptions is placed in the `try` block, specific exception types are caught and handled in `catch` blocks, and cleanup code that should always execute (regardless of exceptions) goes in the `finally` block.

```csharp
try
{
    // Code that might throw an exception
    int result = 10 / 0; // Will throw DivideByZeroException
    File.ReadAllText("nonexistent.txt"); // Will throw FileNotFoundException
}
catch (DivideByZeroException ex)
{
    // Handle specific exception
    Console.WriteLine($"Math error: {ex.Message}");
    // Log the exception details for developers
    Logger.LogError(ex, "Division by zero occurred");
    // Provide user-friendly message
    ShowUserErrorMessage("A calculation error occurred. Please try different input values.");
}
catch (FileNotFoundException ex) when (ex.FileName.Contains("nonexistent"))
{
    // Exception filter (C# 6.0+) allows conditionals to catch blocks
    Console.WriteLine($"File not found: {ex.FileName}");
}
catch (IOException ex)
{
    // Handle another specific exception
    Console.WriteLine($"IO error: {ex.Message}");
}
catch (Exception ex)
{
    // Catch all other exceptions
    Console.WriteLine($"Unexpected error: {ex.Message}");
    throw; // Re-throw the exception to preserve stack trace
}
finally
{
    // Code that always executes, whether an exception occurred or not
    Console.WriteLine("This always runs");
    // Common cleanup operations:
    // - Close file handles
    // - Release database connections
    // - Dispose of unmanaged resources
    // - Return pooled objects
}
```

## When to use different Exception approaches

1. **Specific vs. general Exception catching**:
   - Catch specific exceptions when you can handle them in a meaningful way
   - Only catch `Exception` as a last resort to log unexpected errors or provide generic fallbacks
   - Avoid empty catch blocks that swallow exceptions without handling them

2. **Exception filters**:
   - Use when you only want to catch exceptions that meet certain criteria
   - Helps avoid unnecessary exception handling and maintain more precise control flow

3. **Re-throwing Exceptions**:
   - Use `throw;` (without specified exception) to preserve the original stack trace
   - Only use `throw ex;` when you want to deliberately reset the stack trace (rarely needed)

4. **Exception prevention**:
   - Use `TryParse` patterns and null checking to prevent exceptions when possible
   - Reserve exception handling for truly exceptional conditions, not for normal control flow
   - Consider validation before operations that might throw exceptions

## Throwing Exceptions

Throwing exceptions should be done deliberately and with consideration for the calling code. This includes choosing appropriate exception types, providing meaningful messages, and including relevant context.

```csharp
// Throw exceptions
void ProcessData(string data)
{
    if (data == null)
    {
        throw new ArgumentNullException(nameof(data), "Data cannot be null.");
    }
    
    if (data.Length == 0)
    {
        throw new ArgumentException("Data cannot be empty.", nameof(data));
    }
    
    if (!IsValidFormat(data))
    {
        throw new FormatException($"Data '{data}' is not in the required format.");
    }
    
    // Process valid data...
}

// Rethrowing exceptions
try
{
    ProcessData(null);
}
catch (Exception ex)
{
    // Log the exception
    Console.WriteLine($"Error: {ex.Message}");
    
    // Preserve stack trace when rethrowing
    throw;
    
    // This would reset the stack trace (usually undesirable):
    // throw ex;
}
```

## Guidelines for Exception types:

1. **System.ArgumentException**: Use when a method argument is invalid
2. **System.ArgumentNullException**: Use when an argument is unexpectedly null
3. **System.InvalidOperationException**: Use when the object state doesn't allow the operation 
4. **System.NotImplementedException**: Use for methods that aren't implemented yet
5. **System.NotSupportedException**: Use for operations that won't be implemented
6. **System.IO.IOException**: Use for file system and I/O errors
7. **System.FormatException**: Use when string format is incorrect for the expected type
8. **Custom exceptions**: Create when built-in exceptions don't appropriately describe your error

## Custom Exceptions

Custom exceptions allow you to create domain-specific error types that provide more meaningful context about what went wrong in your application. They should be created when built-in exception types don't adequately capture the specific error condition.

```csharp
// Define custom exception
public class CustomerNotFoundException : Exception
{
    public int CustomerId { get; }
    
    public CustomerNotFoundException(int customerId)
        : base($"Customer with ID {customerId} was not found")
    {
        CustomerId = customerId;
    }
    
    public CustomerNotFoundException(int customerId, Exception innerException)
        : base($"Customer with ID {customerId} was not found", innerException)
    {
        CustomerId = customerId;
    }
    
    // For serialization support (important for distributed applications)
    protected CustomerNotFoundException(System.Runtime.Serialization.SerializationInfo info,
        System.Runtime.Serialization.StreamingContext context) : base(info, context)
    {
        CustomerId = info.GetInt32(nameof(CustomerId));
    }
    
    // Override GetObjectData for proper serialization
    public override void GetObjectData(System.Runtime.Serialization.SerializationInfo info,
        System.Runtime.Serialization.StreamingContext context)
    {
        base.GetObjectData(info, context);
        info.AddValue(nameof(CustomerId), CustomerId);
    }
}

// Usage
void ProcessCustomer(int customerId)
{
    if (!customerDatabase.Exists(customerId))
    {
        throw new CustomerNotFoundException(customerId);
    }
    
    // Process customer...
}
```
## Performance considerations

Exception handling has performance implications that should be considered in your design:

1. The `try` block itself has minimal overhead when no exceptions occur
2. Throwing and catching exceptions is relatively expensive and should not be used for normal control flow
3. Use patterns like `TryParse` and null checking to avoid throwing exceptions in expected scenarios
4. Reserve exceptions for truly exceptional conditions that shouldn't happen in normal operation
5. Consider using status return codes or `Result<T>` pattern for expected error conditions in performance-critical code

**Additional resources:**

- [Exception handling (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/)
- [Best practices for Exceptions (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Creating and throwing Exceptions (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/standard/exceptions/how-to-create-user-defined-exceptions)
- [IDisposable pattern (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/implementing-dispose)
- [Exception handling in async code (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/exception-handling-task-asynchronous-pattern)

<div id="asynchronous-programming"></div>

# Asynchronous Programming

Asynchronous programming in C# allows you to write non-blocking code that can improve responsiveness and throughput, particularly in I/O-bound and network operations. Modern C# provides elegant syntax with async/await that makes asynchronous code almost as straightforward to write as synchronous code, while maintaining the performance benefits.

## When to use asynchronous programming

Understanding when to use async code is crucial. Use async code for **I/O-bound operations**:
- Network requests
- Database operations
- File system operations
- Web API calls
- User input

Don't use it for **CPU-bound operations**. For computationally intensive work, use:
- `Task.Run` to offload work to a background thread
- Parallel processing APIs for data parallelism

## Async and await basics

```csharp
// Async method declaration
public async Task<string> DownloadDataAsync(string url)
{
    // Create HTTP client
    using HttpClient client = new HttpClient();
    
    // Asynchronously wait for the HTTP request
    string result = await client.GetStringAsync(url);
    
    return result;
}

// Calling async methods
public async Task ProcessDataAsync()
{
    Console.WriteLine("Starting data download...");
    
    // Await the asynchronous operation
    string data = await DownloadDataAsync("https://example.com/api/data");
    
    Console.WriteLine($"Downloaded {data.Length} bytes");
}

// Void async methods (event handlers)
public async void Button_Click(object sender, EventArgs e)
{
    try
    {
        await ProcessDataAsync();
        MessageBox.Show("Download complete!");
    }
    catch (Exception ex)
    {
        MessageBox.Show($"Error: {ex.Message}");
    }
}
```

## Guidelines for async methods:

1. **Naming convention**: Append "Async" to method names that return Task or Task<T>
2. **Return types**:
    - Use Task<T> for methods that return a value
    - Use Task for methods that don't return a value
    - Avoid async void except for event handlers
3. **Async all the way**: Convert entire call chains to async to avoid blocking
4. **ConfigureAwait**: Use ConfigureAwait(false) in library code to avoid forcing context

## Task-based asynchronous pattern

The Task-based asynchronous pattern (TAP) is the recommended approach for asynchronous programming in C#. It uses `Task` and `Task<T>` to represent ongoing work and provides rich composition capabilities.

```csharp
// Create and return a Task
public Task<int> CalculateAsync(int a, int b)
{
    return Task.Run(() =>
    {
        // Simulate CPU-bound work
        Thread.Sleep(1000);
        return a + b;
    });
}

// Task.WhenAll - run multiple tasks in parallel
public async Task ProcessMultipleAsync()
{
    Task<string> task1 = DownloadDataAsync("https://example.com/api/1");
    Task<string> task2 = DownloadDataAsync("https://example.com/api/2");
    Task<string> task3 = DownloadDataAsync("https://example.com/api/3");
    
    // Wait for all tasks to complete
    string[] results = await Task.WhenAll(task1, task2, task3);
    
    // Process results
    foreach (string result in results)
    {
        Console.WriteLine($"Result length: {result.Length}");
    }
}

// Task.WhenAny - wait for the first task to complete
public async Task<string> GetFastestResponseAsync()
{
    Task<string> task1 = DownloadDataAsync("https://example.com/api/1");
    Task<string> task2 = DownloadDataAsync("https://example.com/api/2");
    
    // Wait for the first task to complete
    Task<string> completedTask = await Task.WhenAny(task1, task2);
    
    // Get the result from the completed task
    return await completedTask;
}
```

When to use different task composition methods:
1. **Task.WhenAll**: Use when you need the results of all operations and they can run concurrently
2. **Task.WhenAny**: Use for implementing timeouts, racing operations, or taking the first available result
3. **Task.Run**: Use for CPU-bound work that needs to be offloaded from the current thread
4. **Task.Delay**: Use for implementing timeouts or periodic operations in async methods

## Exception handling in async code

```csharp
public async Task ExceptionHandlingExampleAsync()
{
    try
    {
        // Multiple awaits in one try block
        string data = await DownloadDataAsync("https://example.com/api/data");
        int result = await ProcessDataAsync(data);
        await SaveResultAsync(result);
    }
    catch (HttpRequestException ex)
    {
        // Handle network-related exceptions
        Console.WriteLine($"Network error: {ex.Message}");
    }
    catch (JsonException ex)
    {
        // Handle JSON parsing exceptions
        Console.WriteLine($"Invalid data format: {ex.Message}");
    }
    catch (Exception ex)
    {
        // Handle all other exceptions
        Console.WriteLine($"Unexpected error: {ex.Message}");
    }
}

// Aggregate exceptions with Task.WhenAll
public async Task HandleMultipleExceptionsAsync()
{
    var tasks = new List<Task>();
    
    for (int i = 0; i < 5; i++)
    {
        int taskNumber = i;
        tasks.Add(Task.Run(async () =>
        {
            if (taskNumber % 2 == 0)
            {
                await Task.Delay(100);
                throw new Exception($"Task {taskNumber} failed");
            }
        }));
    }
    
    try
    {
        await Task.WhenAll(tasks);
    }
    catch (Exception)
    {
        // Check for all exceptions
        foreach (var task in tasks)
        {
            if (task.Exception != null)
            {
                Console.WriteLine(task.Exception.InnerException.Message);
            }
        }
    }
}
```

## Async exception handling best practices:

1. Always handle exceptions in async methods, especially in async void methods
2. Be aware that `Task.WhenAll` throws only the first exception; check all tasks for exceptions
3. Use `AggregateException.Flatten()` to simplify handling multiple exceptions
4. Consider using a global exception handler for unhandled exceptions in async code
5. Remember that exceptions in async methods are captured and placed on the returned Task

## Cancellation in async operations

Cancellation allows long-running operations to be stopped gracefully. The `CancellationToken` mechanism provides a standardized way to implement cancellation in async methods.

```csharp
public async Task DemonstrateCancellationAsync()
{
    // Create cancellation token source
    using CancellationTokenSource cts = new CancellationTokenSource();
    
    // Set timeout after 5 seconds
    cts.CancelAfter(TimeSpan.FromSeconds(5));
    
    try
    {
        await LongRunningOperationAsync(cts.Token);
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Operation was canceled");
    }
}

public async Task LongRunningOperationAsync(CancellationToken cancellationToken)
{
    for (int i = 0; i < 100; i++)
    {
        // Check cancellation before doing work
        cancellationToken.ThrowIfCancellationRequested();
        
        // Perform some work
        Console.WriteLine($"Working on step {i}");
        
        // Wait with cancellation support
        await Task.Delay(100, cancellationToken);
    }
}

// Example of cancelling a web request
public async Task<string> DownloadWithTimeoutAsync(string url, TimeSpan timeout)
{
    using CancellationTokenSource cts = new CancellationTokenSource(timeout);
    using HttpClient client = new HttpClient();
    
    try
    {
        return await client.GetStringAsync(url, cts.Token);
    }
    catch (OperationCanceledException)
    {
        throw new TimeoutException($"The request to {url} timed out after {timeout.TotalSeconds} seconds");
    }
}
```

## ValueTask and async streams (C# 8.0+)

`ValueTask` and async streams are newer features that enhance async programming in specific scenarios by improving performance and extending the asynchronous model to sequences.

```csharp
// ValueTask for potentially synchronous, high-performance scenarios
public ValueTask<int> GetValueAsync(bool alreadyCached, int cachedValue)
{
    if (alreadyCached)
    {
        // Return immediately without allocating a Task
        return new ValueTask<int>(cachedValue);
    }
    
    // Fall back to async path
    return new ValueTask<int>(GetValueSlowlyAsync());
}

private async Task<int> GetValueSlowlyAsync()
{
    await Task.Delay(100);
    return 42;
}

// Async streams with IAsyncEnumerable
public async IAsyncEnumerable<string> GetDataStreamAsync(
    [EnumeratorCancellation] CancellationToken cancellationToken = default)
{
    for (int i = 0; i < 10; i++)
    {
        // Check cancellation
        cancellationToken.ThrowIfCancellationRequested();
        
        // Simulate work
        await Task.Delay(100, cancellationToken);
        
        // Yield a result
        yield return $"Item {i}";
    }
}

// Consuming async streams
public async Task ConsumeAsyncStreamAsync()
{
    await foreach (string item in GetDataStreamAsync())
    {
        Console.WriteLine(item);
    }
    
    // With cancellation
    using CancellationTokenSource cts = new CancellationTokenSource(TimeSpan.FromSeconds(1));
    
    try
    {
        await foreach (string item in GetDataStreamAsync().WithCancellation(cts.Token))
        {
            Console.WriteLine(item);
        }
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Stream processing was canceled");
    }
}
```

<div id="code-organization"></div>

# Code organization

How you organize your C# code significantly impacts its readability, maintainability, and extensibility. Well-organized code follows consistent patterns, respects separation of concerns, and leverages language features to create clear boundaries between components. 

Modern C# includes numerous features that help enforce good code organization principles.

## Namespaces

Namespaces in C# provide a way to organize code into logical groups and prevent naming conflicts. They create a hierarchical structure for your types (yes, they can be nested), making large codebases more manageable and allowing for intuitive navigation.

```csharp
// Namespace declaration
namespace MyApplication.DataAccess
{
    public class Database
    {
        // Class implementation
    }
}

// File-scoped namespaces (C# 10.0+)
namespace MyApplication.Business;

public class Customer
{
    // Class implementation
}
```

### Namespace organization best practices:

1. Structure namespaces to reflect logical organization, not folder structure
2. Consider using a company or project name as the top-level namespace
3. Group related functionality within namespace hierarchies
4. Avoid deeply nested namespaces (more than 3-4 levels)
5. Don't put different functionality in the same namespace just because they're in the same assembly

## Using directives

Using directives specify which namespaces are referenced in your code, allowing you to use types from those namespaces without fully qualifying them. They improve code readability by reducing repetition.

```csharp
// Import namespace
using System;
using System.Collections.Generic;
using System.Linq;

// Alias namespace
using IO = System.IO;

// Static imports (C# 6.0+)
using static System.Math;
using static System.Console;

// Combined with global using (C# 10.0+)
global using System;
global using System.Collections.Generic;

// Using aliases for types (C# 12+)
using Point = (int X, int Y);
using CustomerName = string;
using RGB = (byte Red, byte Green, byte Blue);

// Multiple global using directives in a single file (GlobalUsings.cs)
global using System.Collections.Generic;
global using System.Linq;
global using System.Threading;
global using System.Threading.Tasks;
```

### Using directives best practices:

1. Place `using` directives at the top of the file, outside of namespace declarations
2. Order `using` directives alphabetically, with System namespaces first
3. Use `global using` for commonly used namespaces across many files
4. Use static imports sparingly and only for frequently used static members
5. Consider using aliases to improve readability or avoid ambiguity

## File-scoped types (C# 11+)

File-scoped types are accessible only within the file where they're defined, allowing you to create helper classes, interfaces, or enums that are truly private to their implementation file. This reduces the public API surface and prevents accidental usage.

```csharp
// File: UserService.cs
namespace MyApp.Services;

// File-scoped type - only accessible within this file
file class UserValidator
{
    public bool Validate(User user) => !string.IsNullOrEmpty(user.Name);
}

// Public class that can use the file-scoped type
public class UserService
{
    private readonly UserValidator _validator = new();
    
    public bool RegisterUser(User user)
    {
        if (!_validator.Validate(user))
            return false;
            
        // Register user logic
        return true;
    }
}

// File: Utils.cs
file static class StringExtensions  // Only visible in this file
{
    public static bool IsValidEmail(this string email) =>
        email.Contains('@') && email.Contains('.');
}
```

## Partial classes

Partial classes allow splitting a class, struct, or interface definition across multiple files. This can be useful for separating generated code from hand-written code or dividing large classes by functionality.

```csharp
// File: Customer.cs
public partial class Customer
{
    public int Id { get; set; }
    public string Name { get; set; }
    
    public void Save()
    {
        // Implementation
    }
}

// File: Customer.Orders.cs
public partial class Customer
{
    public List<Order> Orders { get; } = new List<Order>();
    
    public void AddOrder(Order order)
    {
        Orders.Add(order);
    }
}

// File: Customer.Validation.cs
public partial class Customer
{
    public bool Validate()
    {
        // Validation logic
        return !string.IsNullOrEmpty(Name);
    }
}
```

## Access modifiers

Access modifiers control the visibility and accessibility of types and type members. Properly applied access modifiers create clear boundaries and enforce encapsulation.

```csharp
// Access modifiers
public class AccessModifierDemo
{
    public int PublicField;                        // Accessible from anywhere
    private int _privateField;                     // Accessible only within the class
    protected int ProtectedField;                  // Accessible within the class and derived classes
    internal int InternalField;                    // Accessible within the same assembly
    protected internal int ProtectedInternalField; // Accessible within the same assembly or derived classes
    private protected int PrivateProtectedField;   // Accessible within the same assembly from derived classes
}
```

### Access modifier guidelines:

1. **public**: Use for types and members that form your public API
2. **internal**: Use for types and members that should be available within your assembly but not externally
3. **private**: Use for implementation details inside a class that shouldn't be accessible elsewhere
4. **protected**: Use for members that should be accessible to derived classes for customization
5. **protected internal**: Use when both derived classes and code within the assembly need access
6. **private protected**: Use when derived classes within the same assembly (but not external ones) need access

## Properties and indexers

Properties provide a way to expose fields while adding validation, computed values, or extra logic during access. They're a fundamental part of C# that enables proper encapsulation in object-oriented design.

```csharp
public class PropertyDemo
{
    // Auto-implemented property
    public string Name { get; set; }
    
    // Property with backing field
    private int _age;
    public int Age
    {
        get { return _age; }
        set { _age = value < 0 ? 0 : value; }
    }
    
    // Expression-bodied property (C# 6.0+)
    public bool IsAdult => Age >= 18;
    
    // Property with different access levels
    public string Email { get; private set; }
    
    // Init-only property (C# 9.0+)
    public string Id { get; init; }
    
    // Required property (C# 11.0+)
    public required string Username { get; set; }
    
    // Indexers
    private string[] _data = new string[10];
    
    public string this[int index]
    {
        get => _data[index];
        set => _data[index] = value;
    }
    
    public string this[string key]
    {
        get => key switch
        {
            "first" => _data[0],
            "last" => _data[^1],                               // The “Hat” Operator (^) is used as a prefix to count indexes starting from the end of a list.
            _ => throw new ArgumentException("Invalid key")
        };
    }
}
```

**Additional resources:**

- [C# coding conventions (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
- [File-scoped namespaces (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-10.0/file-scoped-namespaces)
- [Access modifiers (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/access-modifiers)
- [Properties (Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties)

<div id="end-of-document"></div>

## Wrap Up

If you think the cheatsheet can be improved, please open a PR with any updates and submit any issues. Also, I will continue to improve this, so you should star this repository, too.

## Contribution

- Open a pull request with improvements
- Discuss ideas in issues
- Spread the word

## License

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Author

[Dr. Milan Milanović](https://milan.milanovic.org) -  CTO at [3MD](https://3mdinc.com) and Microsoft MVP for Developer Technologies.