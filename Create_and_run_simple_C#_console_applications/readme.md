# .NET and C# Basics

## Introduction to .NET
- .NET is a free, open-source developer platform for building various applications.
- It supports multiple languages, editors, and libraries.
- Commonly used languages include **C#, F#, and VB.NET**.

## Introduction to C#
- C# (pronounced C-Sharp) is a modern, object-oriented programming language developed by Microsoft.
- It is primarily used for developing Windows applications but can also be used for web and mobile applications.

## Classes and Objects
- **Class**: A blueprint for creating objects.
- **Object**: An instance of a class.

### Example:
```csharp
class Car {
    public string brand = "Toyota";
}

class Program {
    static void Main() {
        Car myCar = new Car();
        Console.WriteLine(myCar.brand);
    }
}
```

## Methods in C#
- A method is a block of code that performs a specific task.
- Methods can have parameters and return values.

### Example:
```csharp
class Program {
    static void Greet(string name) {
        Console.WriteLine("Hello, " + name);
    }
    static void Main() {
        Greet("Kathir");
    }
}
```

## Method Overloading
- **Method overloading** allows multiple methods with the same name but different parameters.

### Example:
```csharp
class Program {
    static void Print(int number) {
        Console.WriteLine("Number: " + number);
    }
    static void Print(string text) {
        Console.WriteLine("Text: " + text);
    }
    static void Main() {
        Print(10);
        Print("Hello");
    }
}
```

## Arrays in C#
- An array is a collection of variables of the same type.

### Example:
```csharp
class Program {
    static void Main() {
        int[] numbers = {1, 2, 3, 4, 5};
        foreach (int num in numbers) {
            Console.WriteLine(num);
        }
    }
}
