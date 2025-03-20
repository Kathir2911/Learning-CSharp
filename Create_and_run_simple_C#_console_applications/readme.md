# Create and Run Simple .NET Console Applications

## Introduction to .NET
.NET is a cross-platform, open-source developer platform used to develop different types of applications. It includes software languages and code libraries used to develop .NET applications. 

### Supported Languages
- C#
- F#
- Visual Basic

### .NET Platform Features
- Used to develop and run applications on Windows, macOS, and Linux.
- Provides a runtime environment for running applications.
- Includes the .NET Runtime (Common Language Runtime - CLR) for executing .NET applications.
- Visual Studio Code can be used with .NET SDK and C# extensions for writing, running, and debugging applications.

## Setting Up a .NET Console Application

### Creating a New Project
Run the following command to create a new C# console application:
```sh
dotnet new console -o ./CsharpProjects/TestProject
```
- This command creates a new folder `CsharpProjects/TestProject`.
- It generates `TestProject.csproj` and `Program.cs` files.

### Building the Application
```sh
dotnet build
```
- Builds the project and its dependencies into a set of binaries.
- The output includes Intermediate Language (IL) files with a `.dll` extension.

### Running the Application
```sh
dotnet run
```
- Executes the compiled application.
- The .NET SDK is required for running .NET CLI commands.

## .NET Class Library
The .NET Class Library is a collection of thousands of classes containing tens of thousands of methods.

### Example: Console Class
```csharp
/* Print Hello World to console */
Console.WriteLine("Hello World!");
```

### Example: System.Random Class
```csharp
/* Generate a random number between 1 and 6 */
Random dice = new Random();
int roll = dice.Next(1, 7);
Console.WriteLine(roll);
```

## Object-Oriented Programming in .NET
### Stateful vs. Stateless Methods
- **Stateless Methods**: Do not store or modify internal data (e.g., `Console.WriteLine()`).
- **Stateful Methods**: Store values in memory and can modify internal state (e.g., `Random.Next()`).

### Creating Objects
```csharp
/* Create an instance of Random class */
Random dice = new Random();
```
- The `new` operator creates an object in memory and returns its reference.

## Methods and Parameters
### Example: Overloaded Methods
```csharp
/* Example of overloaded methods */
Console.WriteLine(); // No parameters
Console.WriteLine("Kathir"); // String parameter
Console.WriteLine(101); // Integer parameter
```

### Example: Method Overloading in Random Class
```csharp
/* Different ways to use Random.Next() */
int num1 = dice.Next(); // No parameters
int num2 = dice.Next(101); // Upper boundary
int num3 = dice.Next(50, 101); // Min and max boundary
```

## Conditional Statements
### Example: If-Else Statement
```csharp
/* Example of if-else statement */
if (value > 10) {
    Console.WriteLine("Value is greater than 10");
} else {
    Console.WriteLine("Value is 10 or less");
}
```

## Arrays
### Example: Defining and Accessing an Array
```csharp
/* Example of defining and accessing an array */
string[] fraudulentOrderIDs = { "A123", "B456", "C789" };
Console.WriteLine($"First: {fraudulentOrderIDs[0]}");
```

### Iterating Using `foreach`
```csharp
/* Example of foreach loop */
string[] names = { "Rowena", "Robin", "Bao" };
foreach (string name in names) {
    Console.WriteLine(name);
}
```

## Variable Naming Rules
- Can contain alphanumeric characters and `_` (underscore).
- Cannot start with a number.
- Cannot use C# keywords.
- Are case-sensitive.

## Local Variables and Comments
A **local variable** is a variable that is scoped within the body of a method or within a console application using top-level statements.

A **code comment** is an instruction to the compiler to ignore everything after the comment symbols in the current line.

```csharp
// This is a single-line comment

/*
   This is a block comment spanning multiple lines.
*/
```

### Example: StartsWith Method
```csharp
/* Check for strings that start with 'B' */
string[] orderId = {"B123", "C234", "A345", "C15", "B177", "G3003", "C235", "B17"};
string[] fraudulentOrders = {};
foreach (string order in orderId) {
    if (order.StartsWith("B")) {
        Console.WriteLine($"The {order} starts with 'B'!");
    }
}
```

### Example: Convert Class - ToChar(), ToString()
```csharp
/* Generate random order IDs */
Random random = new Random();
string[] orderIDs = new string[5];
for (int i = 0; i < orderIDs.Length; i++) {
    int prefixValue = random.Next(65, 70);
    string prefix = Convert.ToChar(prefixValue).ToString();
    string suffix = random.Next(1, 1000).ToString("000");
    orderIDs[i] = prefix + suffix;
}
foreach (var orderID in orderIDs) {
    Console.WriteLine(orderID);
}
```
- `.ToString("000")` ensures numbers always have 3 digits.
- `random.Next(1, 1000)` generates numbers between 1 and 999.

## Whitespace in Code
The term **whitespace** refers to spaces, tabs, and new lines in code.

- Whitespace does not affect the compiler.
- Proper whitespace improves readability.

### Example: String Manipulation
```csharp
/* Reverse a string and count occurrences of 'o' */
string str = "The quick brown fox jumps over the lazy dog.";
char[] charMessage = str.ToCharArray();
Array.Reverse(charMessage);
int x = 0;
foreach (char i in charMessage) {
    if (i == 'o') { x++; }
}
string new_message = new string(charMessage);
Console.WriteLine(new_message);
Console.WriteLine($"'o' appears {x} times.");
```

## Conclusion
This guide covered:
- Setting up a .NET console application.
- Working with .NET Class Library.
- Object-oriented programming concepts.
- Conditional statements and loops.
- String manipulation and array handling.

For more details, refer to the official .NET documentation.

**Source: Microsoft Learn**

