# Lambda Expressions

## The Short Story

Lambda Expressions are a syntactic sugar for writing anonymous methods.

The following example declares a delegate and instantiate it passing a lambda expression on its constructor:

```csharp
internal delegate bool IsZeroDelegate(int number);

IsZeroDelegate isZeroDelegate = number => number == 0;
```

## The Long Story

### Declare a Delegate

Do you remember delegates? Here it is an example:

```csharp
internal delegate bool IsZeroDelegate(int number);
```

### Instantiate the delegate - Using a Named Method

And the delegate can be instantiated like this:

```csharp
private void DoSomething()
{
    IsZeroDelegate isZeroDelegate = new IsZeroDelegate(IsZero);
}

private bool IsZero(int number)
{
    return number == 0;
}
```

On its constructor, the delegate receives, as parameter, a reference to the actual method.

### Instantiate the delegate - Using an Anonymous Method

If we do not want to create the `CountLetters` method in our class we can write it inline, directly in the delegate's constructor using the `delegate` keyword. This is called an anonymous method and it looks like this:

```csharp
private void DoSomething()
{
    IsZeroDelegate isZeroDelegate = new IsZeroDelegate(delegate (int number)
    {
        return number == 0;
    });
}
```

> **Note:** This is similar to anonymous functions that are often used in JavaScript.

### Instantiate the delegate - Using a lambda statement

As a syntactic sugar, we can write the same thing using a lambda statement:

```csharp
private void DoSomething()
{
    IsZeroDelegate isZeroDelegate = new IsZeroDelegate(number =>
    {
        return number == 0;
    });
}
```

The body of the anonymous method remains unchanged, but we drop the `delegate` keyword and the type of the parameter. The type is inferred by the compiler.

### Instantiate the delegate - Using a lambda expression

If the body of the lambda statement is just a single statement, we can drop also the curly brackets `{}` and the `return` keyword and transform it in a lambda expression that is more concise:

```csharp
private void DoSomething()
{
    IsZeroDelegate isZeroDelegate = new IsZeroDelegate(number => number == 0);
}
```

### Instantiate the delegate - Implicit Creation

For all the above examples, we can also drop the explicit creation of the delegate. That `new CountLettersDelegate` part.

Since the variable is a delegate, we can directly assign to it the named method, anonymous method, lambda statement or lambda expression:

```csharp
private void DoSomething()
{
    // Named Method
    IsZeroDelegate isZeroDelegate1 = IsZero;
    
    // Anonynous Method
    IsZeroDelegate isZeroDelegate2 = delegate (int number)
    {
        return number == 0;
    };

    // Lambda Statement
    IsZeroDelegate isZeroDelegate3 = number =>
    {
        return number == 0;
    };
    
    // Lambda Expression
    IsZeroDelegate isZeroDelegate4 = number => number == 0;
}

private bool IsZero(int number)
{
    return number == 0;
}
```

