# Understanding C# Methods

Methods are essential building blocks in C# programming that allow you to organize code into reusable components. This guide explains how methods work, their structure, and best practices for using them effectively.

## Method Basics

### Anatomy of a Method

A method consists of:
- **Method signature**: Declares the method's return type, name, and input parameters
- **Method body**: Contains the code that executes when the method is called

```csharp
// Basic method structure
returnType MethodName(parameterType parameterName)
{
    // Method body - code that executes when called
}
```

### Creating a Simple Method

```csharp
void SayHello()
{
    Console.WriteLine("Hello World!");
}
```

In this example:
- `void` is the return type (returns no data)
- `SayHello` is the method name
- The empty parentheses `()` indicate no parameters
- The code between the braces `{}` is the method body

## Calling Methods

Methods can be called before or after their definition:

```csharp
// Calling before definition
SayHello();

// Method definition
void SayHello()
{
    Console.WriteLine("Hello World!");
}
```

This flexibility lets you organize your code as needed. It's common to define all methods at the end of a program.

## Method Parameters

Parameters allow you to pass information to methods:

```csharp
void DisplayMessage(string message)
{
    Console.WriteLine(message);
}

// Calling the method with an argument
DisplayMessage("Hello from C#!");
```

### Passing Arrays to Methods

```csharp
string[] students = {"Jenna", "Ayesha", "Carlos", "Viktor"};
DisplayStudents(students);

// You can also pass arrays directly
DisplayStudents(new string[] {"Robert", "Vanya"});

void DisplayStudents(string[] students)
{
    foreach (string student in students)
    {
        Console.Write($"{student}, ");
    }
    Console.WriteLine();
}
```

### Named Arguments

Named arguments allow you to specify which parameter each argument is for:

```csharp
void PrintDetails(string name, int age, string city)
{
    Console.WriteLine($"Name: {name}, Age: {age}, City: {city}");
}

// Using named arguments (order can be different)
PrintDetails(age: 30, city: "Los Angeles", name: "Bob");

// Mixing positional and named arguments
PrintDetails("Charlie", city: "Chicago", age: 28);
```

### Optional Parameters

Optional parameters have default values and can be omitted when calling the method:

```csharp
void PrintDetails(string name, int age, string city = "Unknown")
{
    Console.WriteLine($"Name: {name}, Age: {age}, City: {city}");
}

// All arguments provided
PrintDetails("Alice", 25, "New York");

// Omitting the optional argument (city defaults to "Unknown")
PrintDetails("Bob", 30);
```

## Variable Scope in Methods

- Variables declared inside a method are only accessible within that method
- Variables declared in top-level statements are accessible throughout the program
- Methods don't have access to variables defined in different methods
- Methods can call other methods

## Value Types vs. Reference Types

### Value Types
- Directly contain values (int, double, bool, etc.)
- Methods using value type arguments create their own copy of the values
- Changes to the parameter inside the method don't affect the original variable

### Reference Types
- Store the address of the value (arrays, objects, etc.)
- Methods that modify an array parameter affect the original input array
- Strings are immutable reference types - methods modifying a string don't affect the original

## Multidimensional Arrays

```csharp
// Two-dimensional array (notice the comma inside the square brackets)
string[,] corporate =
{
    {"Robert", "Bavin"}, {"Simon", "Bright"},
    {"Kim", "Sinclair"}, {"Aashrita", "Kamath"},
    {"Sarah", "Delucchi"}, {"Sinan", "Ali"}
};
```

## Method Naming Best Practices

- Use Pascal case (capitalize first letter of each word)
- Choose concise names that clearly reflect the method's purpose
- Avoid starting names with digits
- Parameter names should describe what kind of information they represent

## Key Concepts

- **Method signature**: The combination of return type, method name, and parameters
- **Optional parameters**: Simplify method calls by providing default values
- **Pseudo-code**: A design template that helps bridge the gap between concept and code

Methods are powerful tools for organizing and reusing code, making programs more maintainable and readable.
Reference from Microsoft Learn and Chatgpt
