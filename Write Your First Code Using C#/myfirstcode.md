# LEARNING C#

## Write your first code using C#

The C# programming language allows you to build many types of applications, like:

- Business applications to capture, analyze, and process data
- Dynamic web applications that can be accessed from a web browser
- Games, both 2D and 3D
- Financial and scientific applications
- Cloud-based applications
- Mobile applications

### Case Sensitivity in C#
C# is a case-sensitive language, meaning that the C# compiler considers the words `console` and `Console` as different, just like `cat` and `dog`.

### Writing Code in .NET Editor
`.NET Editor` is used to write code for C#.

### Writing "Hello World"
```csharp
Console.WriteLine("Hello World!");
```

### Comments in C#
`//` is used for writing comments.

### Console Output
```csharp
Console.Write("Congratulations!");
Console.Write(" ");
Console.Write("You wrote your first lines of code.");
```
**Output:**
```
Congratulations! You wrote your first lines of code.
```

- `Console.WriteLine()` prints a message to the output console and adds a new line.
- `Console.Write()` prints the message without adding a new line.

## Understanding C# Syntax
- A programming language allows humans to express their intent in a human-readable way to a computer.
- The instructions written in a programming language are called "source code".
- The rules for writing C# code are called **syntax**.

### Elements of C# Syntax
- **Literal String**: A phrase surrounded by double-quotation marks (`" "`).
- **Class (`Console`)**: Methods belong to a class.
- **Member Access Operator (`.`)**: Used to navigate from the class to a method.
- **Method Invocation Operator (`()` )**: Used to call a method.
- **End of Statement Operator (`;`)**: Marks the end of a statement.

## Data Types in C#
### Character and Numeric Types
```csharp
Console.WriteLine('b'); // char literal
Console.WriteLine(123); // int literal
Console.WriteLine(123.44564F); // float literal
Console.WriteLine(123.5689837543243224M); // decimal literal
```

### Boolean Data Type
```csharp
Console.WriteLine(true); // Boolean (bool) literal
```

### Floating-Point Precision
| Type | Precision |
|------|------------|
| float | ~6-9 digits |
| double | ~15-17 digits |
| decimal | 28-29 digits |

### Variables in C#
```csharp
string firstName;
firstName = "Bob";
Console.WriteLine(firstName);
```

#### Rules for Variable Names:
- Can contain alphanumeric characters and underscores.
- Must begin with an alphabetic character or an underscore.
- Case-sensitive.
- Cannot use C# keywords as names.

#### Coding Conventions:
- Use **camelCase**: `string thisIsCamelCase;`
- Variable names should be meaningful and descriptive.

### Implicitly Typed Variables
```csharp
var value = "Hello world";
```

#### Why Use `var`?
- Saves keystrokes
- Improves readability
- Compiler infers the type

### Escape Sequences in Strings
```csharp
Console.WriteLine("Hello \"World\"!"); // Output: Hello "World"!
Console.WriteLine("c:\\source\\repos"); // Correct way to display backslash
```

### Verbatim String Literals
```csharp
Console.WriteLine(@"c:\source\repos");
```

### Unicode Characters in Strings
```csharp
Console.WriteLine("\u3053\u3093\u306B\u3061\u306F World!"); // こんにちは World!
```

## String Interpolation
```csharp
string firstName = "Bob";
int widgetsSold = 7;
Console.WriteLine($"{firstName} sold {widgetsSold + widgetsSold} widgets.");
```

### Mathematical Operators in C#
| Operator | Description |
|----------|-------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |

#### Example:
```csharp
var value = (int) dividend / (int) divisor;
```
This casts operands to the `int` data type.

### Order of Operations (PEMDAS)
1. Parentheses
2. Exponents
3. Multiplication and Division (Left to Right)
4. Addition and Subtraction (Left to Right)

In C#, **exponents** are handled using:
```csharp
System.Math.Pow(base, exponent);
```

This is a structured overview of basic C# concepts. 🚀

**Reference:** This content is taken from Microsoft Learn.
