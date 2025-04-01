# Software Testing, Debugging, and Exception Handling in C#

## Introduction

Every software developer needs to complete some level of testing and debugging when they develop their code. Code debugging is clearly related to both code development and testing. After all, you make corrections to your code logic as you develop your application, and you also run your code periodically to verify that your code syntax and logic are correct. 

The errors that occur during the application runtime are referred to as **exceptions**, and "exception handling" is the process that a developer uses to manage those runtime exceptions within their code. Errors that occur during the build process are referred to as errors, and aren't part of the exception handling process.

## Software Testing Categories

Software testing categories can be organized under the types of testing, the approaches to testing, or a combination of both. One way to categorize the types of testing is to split testing into Functional and NonFunctional testing.

### Functional testing
- Unit testing
- Integration testing
- System testing
- Acceptance testing

### Nonfunctional testing
- Security testing
- Performance testing
- Usability testing
- Compatibility testing

Although most developers probably don't consider themselves to be testers, some level of testing is expected before a developer hands off their work. When developers are assigned a formal role in the testing process, it's often at the level of unit testing.

## Debugging

Code debugging is a process that developers use to isolate an issue and identify one or more ways to fix it. The issue could be related to either code logic or an exception. Either way, you work on debugging your code when it isn't working the way you want it to.

As you read earlier, errors that occur during the application runtime are referred to as exceptions. If an application generates an exception, and that exception isn't managed in code, it can result in the application being shut down.

### Key Points
- Testing, debugging, and exception handling are all important tasks for software developers.
- Testing can be categorized into functional and nonfunctional testing, and developers are expected to perform some level of testing.
- Code debugging is the process of isolating issues and identifying ways to fix them, and it's a developer responsibility.
- Exception handling is the process of managing errors that occur during runtime, and developers are responsible for handling exceptions by using "try" and "catch" statements in their code.
- **If an exception isn't managed in code, the runtime will display an error message and the application may be terminated.**

## Debuggers

A debugger is a software tool used to observe and control the execution flow of your program with an analytical approach. Debuggers help you isolate the cause of a bug and help you resolve it. A debugger connects to your code using one of two approaches:

- By hosting your program in its own execution process.
- By running as a separate process that's attached to your running program.

Debuggers come in different flavors. Some work directly from the command line while others come with a graphical user interface. Visual Studio Code integrates debugger tools in the user interface.

### Debugger Features

Every debugger has its own set of features. The two most important features that come with almost all debuggers are:

- **Control of your program execution**: You can pause your program and run it step by step, which allows you to see what code is executed and how it affects your program's state.
- **Observation of your program's state**: For example, you can look at the value of your variables and function parameters at any point during your code execution.

### Important Notes on Debugging
- Code debugging is a crucial skill in the software development process that every developer learns.
- The best approach to debugging your applications is to use a debugger, not rereading your code five times or adding console.WriteLine() statements throughout your code.
- Debuggers enable you to pause your application, step through your code line-by-line, and observe the state of variables and function parameters.

## Exceptions in C#

In C#, errors in the program at runtime are propagated through the program by using a mechanism called exceptions. Exceptions are thrown by code that encounters an error and caught by code that can correct the error. Exceptions can be thrown by the .NET runtime or by code in a program. Exceptions are represented by classes derived from Exception. Each class identifies the type of exception and contains properties that have details about the exception.

Exceptions are thrown by code that encounters an error and caught by code that can correct the error. The first part of this sentence tells you that exceptions are created by the .NET runtime when an error occurs in your code. The second part of the sentence tells you that you can write code to catch an exception that's been thrown. In addition, the code that catches the exception can be used to complete a corrective action, hopefully mitigating the situation caused by the code that resulted in the error. In other words, you can write code that protects your application when an error occurs.

### Key Points on Exceptions
- Exceptions are used in C# to propagate errors at runtime, and are represented by classes derived from the Exception class.
- Exceptions are thrown by code that encounters an error and caught by code that can correct the error.
- When an exception is caught, code can access its contents and take corrective action to mitigate the error.
- The .NET runtime generates exceptions when it detects an error and the exception contains information about the type of error that occurred.
- **The .NET runtime throws an exception when a C# application generates a system error.**

## Debugging in Visual Studio Code

**The CALL STACK section** is used to keep track of the current point of execution within the running application, starting with the initial point of entry into the application. 

**The VARIABLES section** is used to view and manage variable state during a debug session.

**The "More" dropdown** on the right side of the Debug toolbar enables a developer to disconnect the debugger from the current process. 

**The Run and Debug controls panel** is used to configure and start a debug session from the RUN AND DEBUG view in Visual Studio Code.

The Visual Studio Code debugger for C# uses the .NET Core runtime to launch and interact with an application. When you start the debugger, it creates a new instance of the runtime and runs the application within that instance. The runtime includes an application programming interface (API), which the debugger uses to attach to the running process (your application). Breakpoints are used to specify where code execution pauses.

### Launch.json Configuration
- **The name attribute** specifies the display name for the configuration. The value assigned to name appears in the controls panel at the top of the RUN AND DEBUG view.
- **The preLaunchTask attribute** specifies a task to run before debugging the program. The task itself can be found in the tasks.json file, which is in the .vscode folder along with the launch.json file. Specifying a prelaunch task of build runs a dotnet build command before launching the application.
- **The console attribute** specifies the type of console that's used when the application is launched. The options are internalConsole, integratedTerminal, and externalTerminal. The default setting is internalConsole.

### Types of Breakpoints
- Use a standard breakpoint to pause an application each time a breakpoint is encountered.
- Use a conditional breakpoint to pause an application when a Boolean expression evaluates to true.

The CALL STACK section is useful when you're trying to find the source location for an exception or WATCH expression. The BREAKPOINTS section displays the current breakpoint settings and can be used to enable or disable specific breakpoints during a debug session.

## Common Scenarios Requiring Exception Handling

1. **User input**: Exceptions can occur when code processes user input. For example, exceptions occur when the input value is in the wrong format or out of range.

2. **Data processing and computations**: Exceptions can occur when code performs data calculations or conversions. For example, exceptions occur when code attempts to divide by zero, cast to an unsupported type, or assign a value that's out of range.

3. **File input/output operations**: Exceptions can occur when code reads from or writes to a file. For example, exceptions occur when the file doesn't exist, the program doesn't have permission to access the file, or the file is in use by another process.

4. **Database operations**: Exceptions can occur when code interacts with a database. For example, exceptions occur when the database connection is lost, a syntax error occurs in a SQL statement, or a constraint violation occurs.

5. **Network communication**: Exceptions can occur when code communicates over a network. For example, exceptions occur when the network connection is lost, a timeout occurs, or the remote server returns an error.

6. **Other external resources**: Exceptions can occur when code communicates with other external resources. Web Services, REST APIs, or third-party libraries, can throw exceptions for various reasons. For example, exceptions occur due to network connections issues, malformed data, etc.

## Exception Handling Syntax

```csharp
try
{
    // try code block - code that may generate an exception
}
catch
{
    // catch code block - code to handle an exception
}
finally
{
    // finally code block - code to clean up resources
}
```

- The **try code block** contains the guarded code that may cause an exception. If the code within a try block causes an exception, the exception is handled by a corresponding catch block.

- The **catch code block** contains the code that's executed when an exception is caught. The catch block can handle the exception, log it, or ignore it. A catch block can be configured to execute when any exception type occurs, or only when a specific type of exception occurs.

- The **finally code block** contains code that executes whether an exception occurs or not. The finally block is often used to clean up any resources that are allocated in a try block. For example, ensuring that a variable has the correct or required value assigned to it.

### Exception Handling Patterns

- The **try-catch pattern** consists of a try block followed by one or more catch clauses. Each catch block is used to specify handlers for different exceptions.

- The **try-finally pattern** consists of a try block followed by a finally block. Typically, the statements of a finally block run when control leaves a try statement.

- The **try-catch-finally pattern** implements all three types of exception handling blocks. A common scenario for the try-catch-finally pattern is when resources are obtained and used in a try block, exceptional circumstances are managed in a catch block, and the resources are released or otherwise managed in the finally block.

- If no catch clause is found to handle the exception, the runtime terminates the application and displays an error message to the user.

### The Call Stack

You can think of the call stack like a tower of blocks. When you build a tower, you start with just one block. Each time you add a block to the tower, you place it on top of the existing blocks. When your application starts running in the debugger, the entry point to your application is the first layer added to the call stack (the first block of the tower). Each time a method calls another method, the new method is added to the top of the stack. When your code exits out of a method, the method is removed from the call stack.

## Key Exception Handling Concepts

- Common scenarios that may require exception handling include user input, data processing, file I/O operations, database operations, and network communication.

- Exception handling in C# is implemented using try, catch, and finally keywords. Each keyword has an associated code block that serves a specific purpose.

- Exceptions are represented as types and derived from the System.Exception class in .NET. Exceptions contain information that identifies the type of exception, and properties that provide additional details.

- When an exception occurs, the .NET runtime searches for the nearest catch clause that can handle it. The search starts with the method where the exception was thrown, and moves down the call stack if necessary.

- **The try, catch, finally, and throw keywords are used for exception handling in C#.**

## Common Runtime Exceptions

The .NET runtime throws exceptions when basic operations fail. Here's a short list of runtime exceptions and their error conditions:

- **ArrayTypeMismatchException**: Thrown when an array can't store a given element because the actual type of the element is incompatible with the actual type of the array.

- **DivideByZeroException**: Thrown when an attempt is made to divide an integral value by zero.

- **FormatException**: Thrown when the format of an argument is invalid.

- **IndexOutOfRangeException**: Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.

- **InvalidCastException**: Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.

- **NullReferenceException**: Thrown when an attempt is made to reference an object whose value is null.

- **OverflowException**: Thrown when an arithmetic operation in a checked context overflows.

## Exception Class Properties

Most of the exception classes that inherit from Exception don't add any additional functionality; they simply inherit from Exception. Therefore, examining the properties of the Exception class enables you to understand most exceptions, and how you might use an exception in your code.

Here are the properties of the Exception class:

- **Data**: The Data property holds arbitrary data in key-value pairs.

- **HelpLink**: The HelpLink property can be used to hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.

- **HResult**: The HResult property can be used to access to a coded numerical value that's assigned to a specific exception.

- **InnerException**: The InnerException property can be used to create and preserve a series of exceptions during exception handling.

- **Message**: The Message property provides details about the cause of an exception.

- **Source**: The Source property can be used to access the name of the application or the object that causes the error.

- **StackTrace**: The StackTrace property contains a stack trace that can be used to determine where an error occurred.

- **TargetSite**: The TargetSite property can be used to get the method that throws the current exception.

## Examples of Exception Handling

### Example 1: Basic Exception Handling

```csharp
static void Process1()
{
    try
    {
        WriteMessage();
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Exception caught in Process1: {ex.Message}");
    }
}
```

This ex.Message gives the type of exception to the user:

```
Exception caught in Process1: Attempted to divide by zero.
Exit program
```

Note: When float1/float2 (i.e., 3000.0/0.0) is executed, it doesn't throw an exception. Instead, it follows the IEEE 754 standard for floating-point arithmetic, resulting in infinity being printed.

### Example 2: Multiple Catch Blocks

```csharp
// inputValues is used to store numeric values entered by a user
string[] inputValues = new string[]{"three", "9999999999", "0", "2" };

foreach (string inputValue in inputValues)
{
    int numValue = 0;
    try
    {
        numValue = int.Parse(inputValue);
    }
    catch (FormatException)
    {
        Console.WriteLine("Invalid readResult. Please enter a valid number.");
    }
    catch (OverflowException)
    {
        Console.WriteLine("The number you entered is too large or too small.");
    }
    catch(Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}
```

## Important Notes on Exception Handling

- **System.Exception is the base class that all derived exception types inherit from.**
- **The recommended approach is to catch only the exceptions that your code knows how to recover from.**
- **The StackTrace property contains a stack trace that can be used to determine where an error occurred.**

## Throwing Exceptions

Exceptions can be thrown by your code when an issue or error condition is encountered. Exception objects that describe an error are created and then thrown with the throw keyword. When an exception is thrown by your code, the runtime searches for the nearest catch clause that can handle the exception.

The ability to generate an exception in response to a specific condition, issue, or error helps you to ensure the stability of your application.

The process for throwing an exception object involves creating an instance of an exception derived class, optionally configuring properties of the exception, and then throwing the object using the throw keyword.

### Method 1: Create and Throw

```csharp
ArgumentException invalidArgumentException = new ArgumentException("ArgumentException: The 'GraphData' method received data outside the expected range.");
throw invalidArgumentException;
```

### Method 2: Inline Creation and Throw

```csharp
throw new FormatException("FormatException: Calculations in process XYZ have been cancelled due to invalid data format.");
```

### Important Considerations When Throwing Exceptions

- The **Message property** should explain the reason for the exception. However, information that's sensitive, or that represents a security concern shouldn't be put in the message text.

- The **StackTrace property** is often used to track the origin of the exception. This string property contains the name of the methods on the current call stack, together with the file name and line number in each method that's associated with the exception. A StackTrace object is created automatically by the common language runtime (CLR) from the point of the throw statement. Exceptions must be thrown from the point where the stack trace should begin.

## Creating a 2-D Array Example

```csharp
string[][] userEnteredValues = new string[][]
{
    new string[] { "1", "2", "3"},
    new string[] { "1", "two", "3"},
    new string[] { "0", "1", "2"}
};
```
Reference from Microsoft Learn and Chatgpt
