# C# Conditional Logic and Variable Scope

## The Conditional (Ternary) Operator

The conditional operator `?:` (also known as the ternary operator) is a compact way to evaluate a Boolean expression and return one of two values based on whether the expression is true or false.

### Syntax
```csharp
condition ? consequent : alternative
```

### Example with Discount Calculation
```csharp
int saleAmount = 1001;
int discount = saleAmount > 1000 ? 100 : 50;
Console.WriteLine($"Discount: {discount}");
```

In this example:
- If `saleAmount` is greater than 1000, the discount is 100
- Otherwise, the discount is 50
- The output will be: `Discount: 100`

## Random Selection with the Conditional Operator

The conditional operator is useful for randomly selecting values.

### Example with Coin Flip
```csharp
Random random = new Random();
string coin = random.Next(0, 2) == 0 ? "Heads" : "Tails";
Console.WriteLine(coin);
```

This code:
1. Creates a new `Random` object
2. Generates a random number (either 0 or 1)
3. Uses the conditional operator to assign "Heads" or "Tails" to the `coin` variable
4. Outputs the result

## Variable Scope in C#

Variables in C# have a defined scope - they're only accessible within the block where they're declared.

### Common Scope Error

The following code generates an error:

```csharp
bool flag = true;

if (flag)
{
    int value = 10;
    Console.WriteLine($"Inside the code block: {value}");
}

// Error: 'value' doesn't exist in this context
Console.WriteLine($"Outside the code block: {value}");
```

### Why This Happens
- The variable `value` is declared inside the `if` block
- It only exists within that block's scope (between the curly braces `{}`)
- Attempting to access it outside that scope results in a compilation error

### Fixing the Scope Issue
To fix this, declare the variable before the conditional block:

```csharp
bool flag = true;
int value; // Declare outside the block

if (flag)
{
    value = 10; // Assign inside the block
    Console.WriteLine($"Inside the code block: {value}");
}

Console.WriteLine($"Outside the code block: {value}");
```
Reference from Microsoft Learn and chatgpt
