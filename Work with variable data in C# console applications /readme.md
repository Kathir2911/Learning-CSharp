# C# Variable Types Guide

## Value Types vs Reference Types

Variables of reference types store references to their data (objects), that is they point to data values stored somewhere else. In comparison, variables of value types directly contain their data. Simple value types are a set of predefined types provided by C# as keywords. These keywords are aliases (a nickname) for predefined types defined in the .NET Class Library. For example, the C# keyword `int` is an alias of a value type defined in the .NET Class Library as `System.Int32`.

```csharp
Console.WriteLine("Signed integral types:");
Console.WriteLine($"sbyte  : {sbyte.MinValue} to {sbyte.MaxValue}");
Console.WriteLine($"short  : {short.MinValue} to {short.MaxValue}");
Console.WriteLine($"int    : {int.MinValue} to {int.MaxValue}");
Console.WriteLine($"long   : {long.MinValue} to {long.MaxValue}");
```

Output:
```
Signed integral types:
sbyte : -128 to 127
short : -32768 to 32767
int : -2147483648 to 2147483647
long : -9223372036854775808 to 9223372036854775807
```

```csharp
Console.WriteLine("");
Console.WriteLine("Unsigned integral types:");
Console.WriteLine($"byte : {byte.MinValue} to {byte.MaxValue}");
Console.WriteLine($"ushort : {ushort.MinValue} to {ushort.MaxValue}");
Console.WriteLine($"uint : {uint.MinValue} to {uint.MaxValue}");
Console.WriteLine($"ulong : {ulong.MinValue} to {ulong.MaxValue}");
```

Output:
```
Unsigned integral types:
byte : 0 to 255
ushort : 0 to 65535
uint : 0 to 4294967295
ulong : 0 to 18446744073709551615
```

Floating point types:
- `float`: -3.402823E+38 to 3.402823E+38 (with ~6-9 digits of precision)
- `double`: -1.79769313486232E+308 to 1.79769313486232E+308 (with ~15-17 digits of precision)
- `decimal`: -79228162514264337593543950335 to 79228162514264337593543950335 (with 28-29 digits of precision)

Reference types include arrays, classes, and strings. Reference types are treated differently from value types regarding the way values are stored when the application is executing. A value type variable stores its values directly in an area of storage called the stack. The stack is memory allocated to the code that is currently running on the CPU (also known as the stack frame, or activation frame). When the stack frame has finished executing, the values in the stack are removed. The nature of stack frame is use and throw memory allocation.

## Value Types and Reference Types Explained

### Value Types: Like Keeping Things in Your Pocket

- Imagine you have a small item, like a coin or a note with a phone number on it.
- When you store it, you put it directly into your pocket.
- That's like a value type. The actual value (the coin, the number) is stored directly in the memory space allocated to your current task (the stack).
- When you're done with that task (the function finishes), the pocket (stack frame) and everything in it are gone.

### Reference Types: Like Having an Address to a Storage Unit

- Now, imagine you have a large item, like a piece of furniture or a box of belongings.
- You can't fit it in your pocket, so you rent a storage unit.
- You write down the address of the storage unit on a piece of paper and keep that paper in your pocket.
- That's like a reference type. The piece of paper with the address is what's stored in your pocket (the stack), but the actual furniture or belongings are stored elsewhere (the heap).
- The .NET Runtime is like the storage unit manager. It finds an available unit (memory address) for your belongings and gives you the address.
- When you need the furniture, you look up the address on your paper and go to the storage unit to get it.
- Even when the paper in your pocket is gone, the storage unit, and its contents, could still exist. The .Net garbage collector will clean up the storage unit when it detects that nothing is using the address anymore.

### In simpler terms:

- **Value types:** You store the actual thing directly where you're working. Fast and simple, but only for small, temporary things.
- **Reference types:** You store an "address" to the thing, not the thing itself. More flexible for larger, longer-lasting things, but requires an extra step to get the actual value.

The string data type is also a reference type. You might be wondering why a new operator wasn't used when declaring a string. This is purely a convenience afforded by the designers of C#. Because the string data type is used so frequently, you can use this format:

```csharp
string shortenedString = "Hello World!";
Console.WriteLine(shortenedString);
```

Behind the scenes, however, a new instance of System.String is created and initialized to "Hello World!".

## Example: Value Types vs Reference Types

### Value Types Example:
```csharp
int val_A = 2;
int val_B = val_A;
val_B = 5;

Console.WriteLine("--Value Types--");
Console.WriteLine($"val_A: {val_A}");
Console.WriteLine($"val_B: {val_B}");
```

When value B is changed, value A remains unchanged.

### Reference Datatype Example:
```csharp
int[] ref_A = new int[1];
ref_A[0] = 2;
int[] ref_B = ref_A;
ref_B[0] = 5;

Console.WriteLine("--Reference Types--");
Console.WriteLine($"ref_A[0]: {ref_A[0]}");
Console.WriteLine($"ref_B[0]: {ref_B[0]}");
```

When `ref_B = ref_A` is executed, ref_B points to the same memory location as ref_A. So, when ref_B[0] is changed, ref_A[0] also changes because they both point to the same memory location. This is a key difference between value types and reference types.

- Value types can hold smaller values and are stored in the stack. Reference types can hold large values, and a new instance of a reference type is created using the new operator. Reference type variables hold a reference (the memory address) to the actual value stored in the heap.
- Reference types include arrays, strings, and classes.

## Choosing Datatypes:

- `int` for most whole numbers
- `decimal` for numbers representing money
- `bool` for true or false values
- `string` for alphanumeric value
- `byte`: working with encoded data that comes from other computer systems or using different character sets.
- `double`: working with geometric or scientific purposes. double is used frequently when building games involving motion.
- `System.DateTime` for a specific date and time value.
- `System.TimeSpan` for a span of years / months / days / hours / minutes / seconds / milliseconds.

## Type Conversion

The term **narrowing conversion** means that you're attempting to convert a value from a data type that can hold *more* information to a data type that can hold less information. In this case, you may lose information such as precision (that is, the number of values after the decimal point).

For data conversions, there are three techniques you can use:
- Use a helper method on the variable
- Use a helper method on the data type
- Use the Convert class' methods

### Use ToString() to convert a number to a string

Every data type variable has a ToString() method. What the ToString() method does depends on how it's implemented on a given type. However, on most primitives, it performs a widening conversion. While this isn't strictly necessary (since you can rely on implicit conversion in most cases) it can communicate to other developers that you understand what you're doing and it's intentional.

### Convert a string to an int using the Parse() helper method

Most of the numeric data types have a Parse() method, which converts a string into given data type. In this case you use Parse() method to convert two strings into int values, then add them together.

```csharp
string first = "5";
string second = "7";
int sum = int.Parse(first) + int.Parse(second);
Console.WriteLine(sum);
```

### Using the Convert class

The Convert class has many helper methods to convert a value from one type into another.

```csharp
string value1 = "5";
string value2 = "7";
int result = Convert.ToInt32(value1) * Convert.ToInt32(value2);
Console.WriteLine(result);
```

Why is the method name ToInt32()? Why not ToInt()? System.Int32 is the name of the underlying data type in the .NET Class Library that the C# programming language maps to the keyword int. Because the Convert class is also part of the .NET Class Library, it is called by its full name, not its C# name. By defining data types as part of the .NET Class Library, multiple .NET languages like Visual Basic, F#, IronPython, and others can share the same data types and the same classes in the .NET Class Library.

The Convert class is best for converting fractional numbers into whole numbers (int) because it rounds up the way you would expect.

### Using TryParse()

The TryParse() method does several things simultaneously:
- It attempts to parse a string into the given numeric data type.
- If successful, it stores the converted value in an **out parameter**.
- It returns a bool to indicate whether the action succeeded or failed.

#### Out parameter

Methods can return a value or return "void" -- meaning they return no values through out parameters, which are defined just like an input parameter, but include the out keyword.

- Use TryParse() when converting a string into a numeric data type.
- TryParse() returns true if the conversion is successful, false if it's unsuccessful.
- Out parameters provide a secondary means of a method returning a value. In this case, the out parameter returns the converted value.
- Use the keyword out when passing in an argument to a method that has defined an out parameter.

```csharp
string[] values = { "12.3", "45", "ABC", "11", "DEF" };
decimal total = 0m;
string message = "";

foreach (var value in values)
{
    decimal number; // stores the TryParse "out" value
    if (decimal.TryParse(value, out number))
    {
        total += number;
    } 
    else
    {
        message += value;
    }
}

Console.WriteLine($"Message: {message}");
Console.WriteLine($"Total: {total}");
```

**Note: Changing a float into an int is a narrowing conversion, because float can store more precision data compared to int.**

## Array Methods

- **Array.Sort()** method sorts all types of array even strings.
- **Array.Reverse()** method reverses the orders of items inside array class.
- The Array class has methods that can manipulate the size and contents of an array.
- Use the Sort() method to manipulate the order based on the given data type of the array. It is an array method.
- Use the Reverse() method to flip the order of the elements in the array.
- The Array.Clear() method enables you to eliminate the contents of specific elements in your array, replacing them with the array's default value. For instance, if you clear an element in a string array, the cleared value is replaced with null. Similarly, when you clear an element in an int array, the replacement is 0(zero).
- The Array.Resize() method, on the other hand, allows you to add or remove elements from your array.

```csharp
string[] pallets = [ "B14", "A11", "B12", "A13" ];
Console.WriteLine("");
Array.Clear(pallets, 0, 2);
Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```

Output:
```
Clearing 2 ... count: 4
-- 
-- 
-- B12
-- A13
```

`Array.Clear(pallets, 0, 2);` Here you're using the Array.Clear() method to clear the values stored in the elements of the pallets array starting at index 0 and clearing 2 elements.

- Use the Clear() method to empty the values out of elements in the array.
- Use the Resize() method to change the number of elements in the array, removing or adding elements from the end of the array.
- New array elements and cleared elements are null, meaning they don't point to a value in memory.

## String Manipulation

### Use of ToCharArray() to reverse a string

```csharp
string value = "abc123";
char[] valueArray = value.ToCharArray();
```

ToCharArray() method is used to create an array of char, where each element of the array represent one character of the original string.

### Reverse a String:

```csharp
string str = "abc123";
char[] array = str.ToCharArray();
Array.Reverse(array);
string newstring = new string(array);
Console.WriteLine(newstring);
```

In some cases, you might need to separate each element of the character array using a comma, which is a common practice when working with data represented as ASCII text.

```csharp
string value = "abc123";
char[] valueArray = value.ToCharArray();
Array.Reverse(valueArray);
string result = String.Join(",", valueArray);
Console.WriteLine(result);
```

Output: `3,2,1,c,b,a`

### Split() the comma separated value string into an array of strings

```csharp
string value = "abc123";
char[] valueArray = value.ToCharArray();
Array.Reverse(valueArray);
// string result = new string(valueArray);
string result = String.Join(",", valueArray);
Console.WriteLine(result);

string[] items = result.Split(',');
foreach (string item in items)
{
    Console.WriteLine(item);
}
```

- To create an array, use methods like ToCharArray() and Split()
- To turn the array back into a single string, use methods like Join(), or create a new string passing in an array of char

What is null? A value that indicates a variable points to nothing in memory. **Null isn't the same as an empty string or the value zero.**

## String Formatting

**Composite formatting** uses numbered place holders within a string. At run time, everything the braces is resolved to a value that is also passed in based on their position. The example of composite formatting uses a built-in method Format() on the string data type keyword.

```csharp
string first = "Hello";
string second = "World";
string result = string.Format("{0} {1}!", first, second);
Console.WriteLine(result);
```

Datatypes and variables of a given data type have built-in "helper methods" to make certain tasks easy. The literal string "{0} {1}!" forms a template, parts of which are replaced at run time. The token {0} is replaced by the first argument after the string template, in other words, the value of the variable first. The token {1} is replaced by the second argument after the string template, in other words, the value of the variable second. You many think it's odd to start with the number 0. Actually this is very common in software development. Whenever there's a sequence of items that can be identified using a number, the numbering will usually start at 0.

```csharp
string first = "Hello";
string second = "World";
Console.WriteLine("{1} {0}!", first, second);
Console.WriteLine("{0} {0} {0}!", first, second);
```

Output:
```
World Hello!
Hello Hello Hello!
```

- For the second Console.WriteLine() statement, observe that the tokens can be reused with three instances of {0}. Also, the second variable argument, second, isn't used. Yet, the code still runs without error.

### String interpolation

String interpolation is a technique that simplifies composite formatting. Instead of using a numbered token and including the literal value or variable name in a list of arguments to String.Format() or Console.WriteLine(), you can just use the variable name inside of the curly braces.

In order for a string to be interpolated, you must prefix it with the $ directive.

```csharp
string first = "Hello";
string second = "World";
Console.WriteLine($"{first} {second}!");
Console.WriteLine($"{second} {first}!");
Console.WriteLine($"{first} {first} {first}!");
```

### Formatting currency

Composite formatting and string interpolation can be used to format values for display given a specific language and culture. In the following example, the :C currency format specifier is used to present the price and discount variables as currency.

```csharp
decimal price = 123.45m;
int discount = 50;
Console.WriteLine($"Price: {price:C} (Save {discount:C})");
```

If you executed this code on a computer that has its Windows display language set to "English(United States)", you observe the following output.

Output:
```
Price: $123.45 (Save $50.00)
```

Notice how adding the :C to the tokens inside of the curly braces formats the numbers as currency regardless of whether you use int or decimal.

What happens if your country/region and language isn't known? If you run the previous code in the "in-browser" .NET Editor, such as at [TrydotNet](https://dotnet.microsoft.com/platform/try-dotnet) you'll see the following output: **Price: ¤123.45 (Save ¤50.00)**. The symbol **¤** is used instead of the symbol for your country/region's money. This is a generic symbol used to denote "currency" regardless of the *type* of currency. You see this symbol in the .NET Editor because it ignores your current location.

### Formatting numbers

When working with numeric data, you might want to format the number for readability by including commas to delineate thousand, millions, billions and so on.

The N number format specifier makes number more readable.

```csharp
decimal measurement = 123456.78912m;
Console.WriteLine($"Measurement: {measurement:N} units");
```

Output:
```
Measurement: 123,456.7891 units
```

If you want to display more precision, you can do that by adding a number after the specifier. The following code will display four digits after the decimal point using the N4 specifier.

```csharp
decimal measurement = 123456.78912m;
Console.WriteLine($"Measurement: {measurement:N4} units");
```

### Formatting percentages

Use the P format specifier to format percentages and rounds to 2 decimal places. Add a number afterwards to control the number of values displayed after the decimal point

```csharp
decimal tax = .36785m;
Console.WriteLine($"Tax rate: {tax:P2}");
```

Output: `Tax rate: 36.79%`

- You can use composite formatting or string interpolation to format strings.
- With **composite formatting**, you use a string template containing one or more replacement tokens in the form {0}. You also supply a list of arguments that are matched with the replacement tokens based on their order. Composite formatting works when using string.Format() or Console.WriteLine().
- With **string interpolation**, you use a string template containing the variable names you want replaced surrounded by curly braces. Use the $ directive before the string template to indicate you want the string to be interpolated.
- Format currency using a :C specifier.
- Format numbers using a :N specifier. Control the precision (number of values after the decimal point) using a number after the :N like {myNumber:N3}.
- Format percentages using the :P format specifier.
- Formatting currency and numbers depend on the end user's culture, a five character code that includes the user's country/region and language (per the settings on their computer).

Example:
```csharp
int invoiceNumber = 1201;
decimal productShares = 25.4568m;
decimal subtotal = 2750.00m;
decimal taxPercentage = .15825m;
decimal total = 3185.19m;

Console.WriteLine($"Invoice Number: {invoiceNumber}");
Console.WriteLine($" Shares: {productShares:N3} Product");
Console.WriteLine($" Sub Total: {subtotal:C}");
Console.WriteLine($" Tax: {taxPercentage:P2}");
Console.WriteLine($" Total Billed: {total:C}");
```

Output:
```
Invoice Number: 1201
Shares: 25.457 Product
Sub Total: $2,750.00
Tax: 15.83%
Total Billed: $3,185.19
```

## String Methods

- Methods that add blank spaces for formatting purposes (PadLeft(), PadRight())
- Methods that compare two strings or facilitate comparison (Trim(), TrimStart(), TrimEnd(), GetHashcode(), the Length property)
- Methods that help you determine what's inside of a string, or even retrieve just a part of the string (Contains(), StartsWith(), EndsWith(), Substring())
- Methods that change the content of the string by replacing, inserting, or removing parts (Replace(), Insert(), Remove())
- Methods that turn a string into an array of strings or characters (Split(), ToCharArray())

### PadLeft, PadRight():

```csharp
string name = "Kathir";
Console.WriteLine(name.PadLeft(12));
Console.WriteLine(name.PadLeft(12, '*'));
Console.WriteLine(name.PadRight(12));
Console.WriteLine(name.PadRight(12, '*'));
```

Output:
```
       Kathir
*******Kathir
Kathir       
Kathir*******
```

In C#, an overloaded method is another version of a method with different or extra arguments that modify the functionality of the method slightly, as it the case with the overloaded version of the PadLeft method.

```csharp
string paymentId = "769C";
string payeeName = "Mr. Stephen Ortega";
var formattedLine = paymentId.PadRight(6);
formattedLine += payeeName.PadRight(24);
Console.WriteLine(formattedLine);
```

Here paymentId create 2 gaps and the payeeName will be after the paymentId thus it looks like:
```
769C  Mr. Stephen Ortega
```

- The string data type, literal strings, and variables of type string each implement many helper methods to format, modify, and perform other operations on strings.
- The PadLeft() and PadRight() methods add white space (or optionally, another character) to the total length of a string.
- Use PadLeft() to right-align a string.
- Some methods are overloaded, meaning they have multiple versions of the method with different arguments that affect their functionality.
- The += operator concatenates a new string on the right to the existing string on the left.

### IndexOf()

IndexOf() is used to find the index of particular character in a string or a string itself (for string it gives the first character position of string). If it doesn't present in the string the output is -1. If the character appears many time the first appear index will be displayed.

```csharp
string message = "Find what is (inside the parentheses)";
int openingPosition = message.IndexOf('(');
int closingPosition = message.IndexOf(')');
// Console.WriteLine(openingPosition);
// Console.WriteLine(closingPosition);
int length = closingPosition - openingPosition;
Console.WriteLine(message.Substring(openingPosition, length));
```

Output: `(inside the parentheses`

The Substring() method needs the starting position and the number of characters, or length, to retrieve.

- IndexOf() gives you the first position of a character or string inside of another string.
- IndexOf() returns -1 if it can't find a match.
- Substring() returns just the specified portion of a string, using a starting position and optional length.
- There's often more than one way to solve a problem. You used two separate techniques to find all instances of a given character or string.
- Avoid hardcoded **magic values**. Instead, define a const variable. A constant variable's value can't be changed after initialization.

The .IndexOf() method returns the index of the first occurrence of a specified character or substring within a given string. The method .LastIndexOf() returns the index position of the last occurrence of a character or string within a given string. Both the Indexof() and LastIndexOf() methods return **-1** if the character or string is **not found**.

```csharp
string message = "(What if) there are (more than) one (set of parentheses)?";
while (true)
{
    int openingPosition = message.IndexOf('(');
    if (openingPosition == -1) break;
    openingPosition += 1;
    int closingPosition = message.IndexOf(')');
    int length = closingPosition - openingPosition;
    Console.WriteLine(message.Substring(openingPosition, length));
    // Note the overload of the Substring to return only the remaining
    // unprocessed message:
    message = message.Substring(closingPosition + 1);
}
```

Here the remaining message after the first ")" will be equal to message.

### IndexOfAny()

.IndexOfAny() reports the index of the first occurrence of any character in a supplied array of characters. The method returns -1 if all characters in the array of characters are not found.

```csharp
string message = "Hello, world!";
char[] charsToFind = { 'a', 'e', 'i' };
int index = message.IndexOfAny(charsToFind);
Console.WriteLine($"Found '{message[index]}' in '{message}' at index: {index}.");
```

Output:
```
Found 'e' in 'Hello, world!' at index: 1.
```

- LastIndexOf() returns the last position of a character or string inside of another string.
- IndexOfAny() returns the first position of an array of char that occurs inside of another string

### Use of Remove() method:

You would typically use Remove() when there's a standard and consistent position of the characters you want to remove from the string.

```csharp
string data = "12345John Smith 5000 3 ";
string updatedData = data.Remove(5, 20);
Console.WriteLine(updatedData);
```

Output: `123455000 3`

### Use the Replace() method

The Replace() method is used when you need to replace one or more characters with a different character (or no character). The Replace method is different from the other methods used so far, it replaces every instance of the given characters, not just the first or last instance.

```csharp
string message = "This--is--ex-amp-le--da-ta";
message = message.Replace("--", " ");
message = message.Replace("-", "");
Console.WriteLine(message);
```

Output: `This is example data`

- The Remove() method works like the Substring() method, except that it deletes the specified characters in the string.
- The Replace() method swaps all instances of a string with a new string.

### Multiple Replace in a single input:

```csharp
string output = input.Replace("<div>", "")
    .Replace("</div>", "")
    .Replace("trade", "reg");
```

**A constant variable can never be changed, once initialized**

Reference from Microsoft Learn, chatgpt and other llm's
