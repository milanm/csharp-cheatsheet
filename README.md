# C# Programming Cheat Sheet (2025 Edition)

## Introduction

This comprehensive C# cheat sheet serves as a quick reference guide for C# developers at all skill levels. It covers the core language features, modern patterns, and best practices as of 2025. The cheat sheet is organized from fundamental concepts to more advanced topics, making it useful for both learning and reference purposes.

C# has evolved significantly since its inception, with regular updates introducing powerful new features while maintaining backward compatibility. This guide incorporates the latest language enhancements through C# 13 and beyond, modern architectural patterns, performance optimizations, and development approaches that have become standard in the .NET ecosystem.

Whether you're building web applications, microservices, desktop software, mobile apps, or games, you'll find relevant syntax examples and patterns to accelerate your development process. Feel free to bookmark this page and refer to it whenever you need to refresh your knowledge of C# language features or modern development techniques.

## Support My Work

If you find this repository helpful, consider supporting me on Patreon:

[![Patreon](patreon.png)](https://www.patreon.com/techworld_with_milan)

## Disclaimer

> This roadmap aims to give you an idea about the landscape. The road map will guide you if you need clarification about what to learn next rather than encouraging you to pick what is hype and trendy. It would help if you grew some understanding of why one tool would be better suited for some cases than the other and remember that hype and trendy only sometimes mean best suited for the job.

## Give a Star! :star:

If you like or are using this project to learn or start your solution, please give it a star. Thanks!

## Table of Contents

- [Comments](#comments)
- [Strings](#strings)
- [Basic Types and Literals](#basic-types-and-literals)
- [Methods and Functions](#methods-and-functions)
  - [Basic Method Syntax](#basic-method-syntax)
  - [Expression-bodied Members](#expression-bodied-members-c-60)
  - [Method Parameters](#method-parameters)
  - [Local Functions](#local-functions-c-70)
  - [Extension Methods](#extension-methods)
  - [Lambda Expressions](#lambda-expressions)
  - [Method Overloading](#method-overloading)
- [Collections](#collections)
  - [Collection Expressions](#collection-expressions-c-12)
  - [Arrays](#arrays)
  - [Lists](#lists)
  - [Dictionary](#dictionary)
  - [HashSet](#hashset)
  - [Queue and Stack](#queue-and-stack)
  - [LINQ](#linq-language-integrated-query)
- [Data Types](#data-types)
  - [Classes](#classes)
  - [Structs](#structs)
  - [Records](#records-c-90)
  - [Record Structs](#record-structs-c-100)
  - [Interfaces](#interfaces)
  - [Enums](#enums)
  - [Tuples](#tuples)
  - [Nullable Types](#nullable-types)
- [Pattern Matching](#pattern-matching)
  - [Type Patterns](#type-patterns)
  - [Property Patterns](#property-patterns)
  - [Tuple Patterns](#tuple-patterns)
  - [Logical Patterns](#logical-patterns)
  - [List Patterns](#list-patterns-c-110)
  - [Discard Pattern](#discard-pattern)
- [Exceptions](#exceptions)
  - [Try-Catch-Finally](#try-catch-finally)
  - [Throwing Exceptions](#throwing-exceptions)
  - [Custom Exceptions](#custom-exceptions)
  - [Using Statement](#using-statement)
- [Classes and Inheritance](#classes-and-inheritance)
  - [Primary Constructors](#primary-constructors-c-12)
  - [Inheritance](#inheritance)
  - [Abstract Classes](#abstract-classes)
  - [Sealed Classes and Members](#sealed-classes-and-members)
  - [Constructors and Initialization](#constructors-and-initialization)
  - [Polymorphism](#polymorphism)
- [Interfaces and Default Implementation](#interfaces-and-default-implementation)
  - [Basic Interface Implementation](#basic-interface-implementation)
  - [Multiple Interface Implementation](#multiple-interface-implementation)
  - [Explicit Interface Implementation](#explicit-interface-implementation)
  - [Default Interface Methods](#default-interface-methods-c-80)
  - [Interface Properties](#interface-properties)
  - [Generic Interfaces](#generic-interfaces)
- [Modern C# Patterns and Performance](#modern-c-patterns-and-performance)
  - [Native AOT](#native-aot-ahead-of-time-compilation)
  - [Modern Dependency Injection](#modern-dependency-injection)
  - [Minimal APIs](#minimal-apis-aspnet-core)
  - [CQRS and MediatR Pattern](#cqrs-and-mediatr-pattern)
- [Asynchronous Programming](#asynchronous-programming)
  - [Async and Await Basics](#async-and-await-basics)
  - [Task-based Asynchronous Pattern](#task-based-asynchronous-pattern)
  - [Exception Handling in Async Code](#exception-handling-in-async-code)
  - [Cancellation in Async Operations](#cancellation-in-async-operations)
  - [ValueTask and Async Streams](#valuetask-and-async-streams-c-80)
- [Modern Testing Approaches](#modern-testing-approaches)
  - [Unit Testing with xUnit](#unit-testing-with-xunit)
  - [Mocking with Moq and NSubstitute](#mocking-with-moq-and-nsubstitute)
  - [Integration Testing](#integration-testing)
- [Performance Optimization](#performance-optimization)
  - [High-Performance Techniques](#high-performance-techniques)
  - [Memory Management](#memory-management)
- [Code Organization](#code-organization)
  - [Namespaces](#namespaces)
  - [Using Directives](#using-directives)
  - [File-scoped Types](#file-scoped-types-c-11)
  - [Partial Classes](#partial-classes)
  - [Access Modifiers](#access-modifiers)
  - [Extension Methods](#extension-methods)
  - [Properties and Indexers](#properties-and-indexers)

<div id="comments"></div>

# Comments

C# supports three types of comments: single-line, multi-line, and XML documentation comments.

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

<div id="strings"></div>

# Strings

In C#, strings are immutable sequences of Unicode characters represented by the `string` type, which is an alias for `System.String`.

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
string rawInterpolated = $$"""
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

For better performance with repeated string concatenation, use `StringBuilder`:

```csharp
using System.Text;

StringBuilder sb = new StringBuilder();
for (int i = 0; i < 100; i++)
{
    sb.Append($"Item {i}, ");
}
string result = sb.ToString();
```

<div id="basic-types-and-literals"></div>

# Basic Types and Literals

C# is a strongly-typed language with a rich type system. Here are the basic types and literals:

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

<div id="methods-and-functions"></div>

# Methods and Functions

Methods in C# are defined within classes or structs. C# supports various ways to define methods.

## Basic Method Syntax

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

## Expression-bodied Members (C# 6.0+)

```csharp
// Expression-bodied method (one-line methods)
public int Multiply(int a, int b) => a * b;

// Expression-bodied property
public string FullName => $"{FirstName} {LastName}";
```

## Method Parameters

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

## Local Functions (C# 7.0+)

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

## Extension Methods

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

## Lambda Expressions

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

## Method Overloading

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

<div id="collections"></div>

# Collections

C# provides a rich set of collection types for different scenarios.

## Collection Expressions (C# 12+)

Collection expressions are a concise way to initialize collections.

```csharp
// Creating collections with the new collection expressions syntax
int[] numbers = [1, 2, 3, 4, 5];            // Array
List<string> names = ["Alice", "Bob", "Charlie"]; // List
HashSet<char> letters = ['a', 'b', 'c'];    // HashSet
Dictionary<string, int> ages = [             // Dictionary
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

Arrays are fixed-size collections of elements of the same type.

```csharp
// Declaration and initialization
int[] numbers = new int[5];          // Array of 5 integers with default values (0)
int[] initialized = new int[] { 1, 2, 3, 4, 5 };  // Initialized array
int[] shorthand = { 1, 2, 3, 4, 5 }; // Shorthand initialization
string[] names = { "Alice", "Bob", "Charlie" };

// Accessing elements
int firstNumber = numbers[0];         // First element (zero-based indexing)
numbers[0] = 10;                      // Assign value to first element

// Multi-dimensional arrays
int[,] matrix = new int[3, 3];        // 3x3 2D array
matrix[0, 0] = 1;                     // Assign to specific position
int[,] initialized2D = {              // Initialize 2D array
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
int length = numbers.Length;          // Number of elements
Array.Sort(numbers);                  // Sort array in-place
Array.Reverse(numbers);               // Reverse array in-place
int index = Array.IndexOf(names, "Bob"); // Find index of element
bool exists = Array.Exists(numbers, n => n > 10); // Check if condition exists
```

## Lists

Lists are dynamic arrays that can grow or shrink in size.

```csharp
using System.Collections.Generic;

// Create a list
List<string> names = new List<string>();        // Empty list
List<int> numbers = new List<int> { 1, 2, 3 };  // Initialized list

// Add elements
names.Add("Alice");                   // Add single element
names.AddRange(new[] { "Bob", "Charlie" }); // Add multiple elements

// Access elements
string first = names[0];              // Access by index
names[0] = "Alicia";                  // Modify by index

// Remove elements
names.Remove("Bob");                  // Remove specific element
names.RemoveAt(0);                    // Remove element at index
names.RemoveAll(x => x.StartsWith("C")); // Remove all that match condition
names.Clear();                        // Remove all elements

// Search and query
bool contains = numbers.Contains(2);  // Check if contains value
int index = numbers.IndexOf(3);       // Find index of element
List<int> filtered = numbers.FindAll(n => n > 1); // Find all matching elements
int found = numbers.Find(n => n > 2); // Find first matching element

// Other operations
int count = numbers.Count;            // Number of elements
numbers.Sort();                       // Sort list in-place
numbers.Reverse();                    // Reverse list in-place
numbers.ForEach(n => Console.WriteLine(n)); // Perform action on each element
```

## Dictionary

Dictionaries store key-value pairs for fast lookups by key.

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

HashSets store unique elements with fast lookup, insertion, and deletion.

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

Queues (FIFO - first in, first out) and Stacks (LIFO - last in, first out).

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

LINQ provides powerful query capabilities for collections.

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

<div id="data-types"></div>

# Data Types

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

## Record Structs (C# 10.0+)

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

## Nullable Types

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

<div id="pattern-matching"></div>

# Pattern Matching

C# supports various pattern matching techniques for more expressive conditional logic.

## Type Patterns

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

## Property Patterns

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

## Tuple Patterns

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

## Logical Patterns

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

## List Patterns (C# 11.0+)

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

## Discard Pattern

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

Exception handling in C# allows you to gracefully handle runtime errors.

## Try-Catch-Finally

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
}
catch (FileNotFoundException ex) when (ex.FileName.Contains("nonexistent"))
{
    // Exception filter (C# 6.0+)
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
    throw; // Re-throw the exception
}
finally
{
    // Code that always executes, whether an exception occurred or not
    Console.WriteLine("This always runs");
}
```

## Throwing Exceptions

```csharp
// Throw exceptions
void ProcessData(string data)
{
    if (data == null)
    {
        throw new ArgumentNullException(nameof(data));
    }
    
    if (data.Length == 0)
    {
        throw new ArgumentException("Data cannot be empty", nameof(data));
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
    
    // This would reset the stack trace:
    // throw ex;
}
```

## Custom Exceptions

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

## Using Statement

The `using` statement ensures that disposable resources are properly cleaned up.

```csharp
// Traditional using statement
using (StreamReader reader = new StreamReader("file.txt"))
{
    string content = reader.ReadToEnd();
    // reader is automatically disposed here
}

// Using declaration (C# 8.0+)
using StreamWriter writer = new StreamWriter("output.txt");
writer.WriteLine("Hello, World!");
// writer is disposed at the end of the scope
```

<div id="classes-and-inheritance"></div>

# Classes and Inheritance

## Primary Constructors (C# 12+)

Primary constructors bring concise syntax for class initialization and property definition:

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

## Abstract Classes

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

## Sealed Classes and Members

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
    
    // Sealed method (can't be overridden further in inheritance chain)
    public virtual void Method2() { }
}

public class Derived : Base
{
    public override void Method1() { }
    
    public sealed override void Method2() { }
}

public class Further : Derived
{
    public override void Method1() { } // OK
    // public override void Method2() { } // Error: cannot override sealed method
}
```

## Constructors and Initialization

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

## Polymorphism

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

<div id="interfaces-and-default-implementation"></div>

# Interfaces and Default Implementation

## Basic Interface Implementation

```csharp
// Define an interface
public interface ILogger
{
    void Log(string message);
    void LogError(string message);
}

// Class implementing the interface
public class ConsoleLogger : ILogger
{
    public void Log(string message)
    {
        Console.WriteLine($"INFO: {message}");
    }
    
    public void LogError(string message)
    {
        Console.WriteLine($"ERROR: {message}");
    }
}

// Usage
ILogger logger = new ConsoleLogger();
logger.Log("Application started");
```

## Multiple Interface Implementation

```csharp
public interface IReadable
{
    string Read();
}

public interface IWritable
{
    void Write(string content);
}

// Implement multiple interfaces
public class TextFile : IReadable, IWritable
{
    private string content = "";
    
    public string Read()
    {
        return content;
    }
    
    public void Write(string newContent)
    {
        content = newContent;
    }
}

// Usage
TextFile file = new TextFile();
file.Write("Hello, World!");

IReadable reader = file;
Console.WriteLine(reader.Read());

IWritable writer = file;
writer.Write("New content");
```

## Explicit Interface Implementation

```csharp
public interface IControl
{
    void Paint();
}

public interface IWindow
{
    void Paint();
}

// Explicit implementation to resolve method name conflicts
public class Form : IControl, IWindow
{
    // Explicit implementation for IControl
    void IControl.Paint()
    {
        Console.WriteLine("Painting as a control");
    }
    
    // Explicit implementation for IWindow
    void IWindow.Paint()
    {
        Console.WriteLine("Painting as a window");
    }
    
    // Class's own implementation
    public void Paint()
    {
        Console.WriteLine("Form's paint method");
    }
}

// Usage
Form form = new Form();
form.Paint(); // Calls Form's method

IControl control = form;
control.Paint(); // Calls IControl's implementation

IWindow window = form;
window.Paint(); // Calls IWindow's implementation
```

## Default Interface Methods (C# 8.0+)

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

## Interface Properties

```csharp
public interface IIdentifiable
{
    string Id { get; }
    string Name { get; set; }
}

public class User : IIdentifiable
{
    // Implement as auto-property
    public string Id { get; } = Guid.NewGuid().ToString();
    
    // Implement with backing field
    private string _name;
    public string Name
    {
        get => _name;
        set => _name = value ?? throw new ArgumentNullException(nameof(value));
    }
}
```

## Generic Interfaces

```csharp
public interface IRepository<T>
{
    T GetById(int id);
    void Save(T entity);
    void Delete(int id);
    IEnumerable<T> GetAll();
}

public class CustomerRepository : IRepository<Customer>
{
    private readonly List<Customer> _customers = new List<Customer>();
    
    public Customer GetById(int id)
    {
        return _customers.FirstOrDefault(c => c.Id == id);
    }
    
    public void Save(Customer entity)
    {
        _customers.Add(entity);
    }
    
    public void Delete(int id)
    {
        _customers.RemoveAll(c => c.Id == id);
    }
    
    public IEnumerable<Customer> GetAll()
    {
        return _customers;
    }
}
```

<div id="async-programming"></div>

# Modern C# Patterns and Performance

## Native AOT (Ahead-of-Time) Compilation

Native AOT compiles C# code directly to native code for improved startup time and reduced memory usage.

```csharp
// Add to .csproj file
<PropertyGroup>
  <PublishAot>true</PublishAot>
</PropertyGroup>

// Assembly trimming hints
[assembly: System.Runtime.CompilerServices.DisableRuntimeMarshalling]

// Trimming annotations
[System.Diagnostics.CodeAnalysis.DynamicallyAccessedMembers(System.Diagnostics.CodeAnalysis.DynamicallyAccessedMemberTypes.All)]
public class MyType { }

// Optimizing code for AOT
// - Avoid reflection
// - Use static delegates instead of instance methods for callbacks
// - Prefer structs for small data structures
// - Use the SkipLocalsInit attribute for performance-critical methods
[System.Runtime.CompilerServices.SkipLocalsInit]
public static void PerformanceMethod() { }
```

## Modern Dependency Injection

```csharp
// Program.cs in ASP.NET Core or Worker Service
var builder = WebApplication.CreateBuilder(args);

// Service lifetimes
builder.Services.AddSingleton<IDataService, DataService>();     // Single instance for app lifetime
builder.Services.AddScoped<IUserService, UserService>();        // New instance per scope (e.g., per HTTP request)
builder.Services.AddTransient<IRandomService, RandomService>(); // New instance each time requested

// Generic open types
builder.Services.AddSingleton(typeof(IRepository<>), typeof(EntityRepository<>));

// Factory methods
builder.Services.AddSingleton<IApiClient>(provider => 
    new ApiClient(provider.GetRequiredService<IConfiguration>()["ApiKey"]));

// Configuration binding
builder.Services.Configure<ApiSettings>(builder.Configuration.GetSection("Api"));

// Keyed services (.NET 8+)
builder.Services.AddKeyedSingleton<IEmailSender, GmailSender>("gmail");
builder.Services.AddKeyedSingleton<IEmailSender, OutlookSender>("outlook");

var app = builder.Build();

// Retrieving keyed services
using (var scope = app.Services.CreateScope())
{
    var gmailSender = scope.ServiceProvider.GetRequiredKeyedService<IEmailSender>("gmail");
}
```

## Minimal APIs (ASP.NET Core)

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();
builder.Services.AddDbContext<AppDbContext>();

var app = builder.Build();

// Configure middleware
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

// Define API endpoints
app.MapGet("/api/users", async (AppDbContext db) => 
    await db.Users.ToListAsync());

app.MapGet("/api/users/{id}", async (int id, AppDbContext db) =>
    await db.Users.FindAsync(id) is User user
        ? Results.Ok(user)
        : Results.NotFound());

app.MapPost("/api/users", async (User user, AppDbContext db) =>
{
    db.Users.Add(user);
    await db.SaveChangesAsync();
    return Results.Created($"/api/users/{user.Id}", user);
});

app.MapDelete("/api/users/{id}", async (int id, AppDbContext db) =>
{
    var user = await db.Users.FindAsync(id);
    if (user is null) return Results.NotFound();
    
    db.Users.Remove(user);
    await db.SaveChangesAsync();
    return Results.NoContent();
});

// Authentication/Authorization filter
app.MapGet("/api/protected", () => "This is protected")
    .RequireAuthorization();

app.Run();
```

## CQRS and MediatR Pattern

```csharp
// Command - represents an action to modify state
public record CreateUserCommand(string Username, string Email) : IRequest<User>;

// Command handler - handles the command and produces a response
public class CreateUserHandler : IRequestHandler<CreateUserCommand, User>
{
    private readonly AppDbContext _db;

    public CreateUserHandler(AppDbContext db) => _db = db;

    public async Task<User> Handle(CreateUserCommand command, CancellationToken cancellationToken)
    {
        var user = new User { Username = command.Username, Email = command.Email };
        _db.Users.Add(user);
        await _db.SaveChangesAsync(cancellationToken);
        return user;
    }
}

// Query - represents a request for data
public record GetUserByIdQuery(int Id) : IRequest<User?>;

// Query handler - handles the query and returns data
public class GetUserByIdHandler : IRequestHandler<GetUserByIdQuery, User?>
{
    private readonly AppDbContext _db;

    public GetUserByIdHandler(AppDbContext db) => _db = db;

    public async Task<User?> Handle(GetUserByIdQuery query, CancellationToken cancellationToken)
    {
        return await _db.Users
            .AsNoTracking()
            .FirstOrDefaultAsync(u => u.Id == query.Id, cancellationToken);
    }
}

// Using MediatR in controller or minimal API
public class UsersController : ControllerBase
{
    private readonly IMediator _mediator;
    
    public UsersController(IMediator mediator) => _mediator = mediator;
    
    [HttpGet("{id}")]
    public async Task<ActionResult<User>> GetUser(int id)
    {
        var user = await _mediator.Send(new GetUserByIdQuery(id));
        return user is null ? NotFound() : Ok(user);
    }
    
    [HttpPost]
    public async Task<ActionResult<User>> CreateUser(CreateUserCommand command)
    {
        var user = await _mediator.Send(command);
        return CreatedAtAction(nameof(GetUser), new { id = user.Id }, user);
    }
}
```

# Asynchronous Programming

## Async and Await Basics

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

## Task-based Asynchronous Pattern

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

## Exception Handling in Async Code

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

## Cancellation in Async Operations

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

## ValueTask and Async Streams (C# 8.0+)

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

# Modern Testing Approaches

## Unit Testing with xUnit

```csharp
using Xunit;
using FluentAssertions; // Modern assertion library

public class CalculatorTests
{
    [Fact]
    public void Add_ShouldReturnSum_WhenGivenTwoNumbers()
    {
        // Arrange
        var calculator = new Calculator();
        
        // Act
        var result = calculator.Add(3, 4);
        
        // Assert
        result.Should().Be(7);
    }
    
    [Theory]
    [InlineData(1, 1, 2)]
    [InlineData(5, 10, 15)]
    [InlineData(-3, 3, 0)]
    public void Add_ShouldReturnCorrectSum_ForMultipleInputs(int a, int b, int expected)
    {
        var calculator = new Calculator();
        calculator.Add(a, b).Should().Be(expected);
    }
}
```

## Mocking with Moq and NSubstitute

```csharp
// NSubstitute example
[Fact]
public async Task ProcessOrder_ShouldCallRepository_WhenOrderIsValid()
{
    // Arrange
    var repository = Substitute.For<IOrderRepository>();
    var emailService = Substitute.For<IEmailService>();
    repository.SaveAsync(Arg.Any<Order>()).Returns(Task.FromResult(true));
    
    var service = new OrderService(repository, emailService);
    var order = new Order { Id = 1, CustomerId = 42, Items = new List<OrderItem>() };
    
    // Act
    await service.ProcessOrderAsync(order);
    
    // Assert
    await repository.Received(1).SaveAsync(Arg.Is<Order>(o => o.Id == 1));
    await emailService.Received(1).SendOrderConfirmationAsync(Arg.Any<Order>());
}

// Moq example
[Fact]
public async Task GetActiveUsers_ShouldFilterInactiveUsers()
{
    // Arrange
    var users = new List<User>
    {
        new User { Id = 1, IsActive = true },
        new User { Id = 2, IsActive = false },
        new User { Id = 3, IsActive = true }
    };
    
    var mockRepo = new Mock<IUserRepository>();
    mockRepo.Setup(repo => repo.GetAllUsersAsync())
        .ReturnsAsync(users);
    
    var service = new UserService(mockRepo.Object);
    
    // Act
    var activeUsers = await service.GetActiveUsersAsync();
    
    // Assert
    activeUsers.Should().HaveCount(2);
    activeUsers.Should().OnlyContain(u => u.IsActive);
}
```

## Integration Testing

```csharp
public class ApiIntegrationTests : IClassFixture<WebApplicationFactory<Program>>
{
    private readonly WebApplicationFactory<Program> _factory;
    
    public ApiIntegrationTests(WebApplicationFactory<Program> factory)
    {
        _factory = factory.WithWebHostBuilder(builder =>
        {
            builder.ConfigureServices(services =>
            {
                // Replace real services with test doubles
                var descriptor = services.SingleOrDefault(d => 
                    d.ServiceType == typeof(DbContextOptions<AppDbContext>));
                
                if (descriptor != null)
                {
                    services.Remove(descriptor);
                }
                
                services.AddDbContext<AppDbContext>(options =>
                {
                    options.UseInMemoryDatabase("TestDb");
                });
            });
        });
    }
    
    [Fact]
    public async Task GetUsers_ReturnsSuccessStatusCode()
    {
        // Arrange
        var client = _factory.CreateClient();
        
        // Act
        var response = await client.GetAsync("/api/users");
        
        // Assert
        response.EnsureSuccessStatusCode();
        var users = await response.Content.ReadFromJsonAsync<IEnumerable<User>>();
        users.Should().NotBeNull();
    }
}
```

# Performance Optimization

## High-Performance Techniques

```csharp
// Using Span<T> for memory-efficient operations
ReadOnlySpan<char> ParseName(string fullName)
{
    ReadOnlySpan<char> nameSpan = fullName.AsSpan();
    int spaceIndex = nameSpan.IndexOf(' ');
    return spaceIndex == -1 ? nameSpan : nameSpan[..spaceIndex];
}

// Span-based parsing
bool TryParseInt(ReadOnlySpan<char> text, out int result)
{
    return int.TryParse(text, out result);
}

// Avoiding allocations with stackalloc
Span<byte> buffer = stackalloc byte[128]; // Allocated on stack, not heap
FillBuffer(buffer);

// Using ArrayPool to reduce GC pressure
using System.Buffers;
byte[] tempBuffer = ArrayPool<byte>.Shared.Rent(4096);
try
{
    // Use the buffer
    ProcessLargeData(tempBuffer);
}
finally
{
    ArrayPool<byte>.Shared.Return(tempBuffer);
}

// String building with minimal allocations
var builder = new StringBuilder(estimatedCapacity: 1000);
for (int i = 0; i < 1000; i++)
{
    builder.Append(i).Append(',');
}
string result = builder.ToString();

// Fast text parsing with Utf8Parser
using System.Buffers.Text;
ReadOnlySpan<byte> utf8Data = [49, 50, 51]; // ASCII "123"
if (Utf8Parser.TryParse(utf8Data, out int value, out int bytesConsumed))
{
    Console.WriteLine($"Parsed: {value}");
}

// StreamReader and StreamWriter performance
using var streamReader = new StreamReader(
    filename,
    bufferSize: 4096,
    detectEncodingFromByteOrderMarks: true);

// Use streams efficiently
using var fileStream = new FileStream(
    path,
    FileMode.Open,
    FileAccess.Read,
    FileShare.Read,
    bufferSize: 4096,
    useAsync: true);
```

## Memory Management

```csharp
// Value types vs reference types
struct Point        // Stored on stack - better for small, frequently created objects
{
    public int X;
    public int Y;
}

// Ref structs - cannot be stored on the heap
ref struct LargeBuffer
{
    public Span<byte> Buffer;
    
    public LargeBuffer(int size)
    {
        Buffer = new byte[size];
    }
}

// Ref returns and ref locals
ref int FindValue(int[] array, int target)
{
    for (int i = 0; i < array.Length; i++)
    {
        if (array[i] == target)
        {
            return ref array[i]; // Return reference to the value, not a copy
        }
    }
    
    throw new ArgumentException("Target not found");
}

// Usage
int[] numbers = [1, 2, 3, 4];
ref int found = ref FindValue(numbers, 3);
found = 30; // Modifies the array element directly
// numbers is now [1, 2, 30, 4]

// Reducing allocations with record structs (C# 10+)
public readonly record struct UserId(Guid Value);
```

# Code Organization

## Namespaces

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

## Using Directives

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

## File-scoped Types (C# 11+)

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

## Partial Classes

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
```

## Access Modifiers

```csharp
// Access modifiers
public class AccessModifierDemo
{
    public int PublicField;           // Accessible from anywhere
    private int _privateField;        // Accessible only within the class
    protected int ProtectedField;     // Accessible within the class and derived classes
    internal int InternalField;       // Accessible within the same assembly
    protected internal int ProtectedInternalField; // Accessible within the same assembly or derived classes
    private protected int PrivateProtectedField;   // Accessible within the same assembly from derived classes
}
```

## Extension Methods

```csharp
// Extension methods must be defined in a static class
public static class StringExtensions
{
    // Extension method for String type
    public static bool IsNullOrEmpty(this string value)
    {
        return string.IsNullOrEmpty(value);
    }
    
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

## Properties and Indexers

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
            "last" => _data[^1],
            _ => throw new ArgumentException("Invalid key")
        };
    }
}
```
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