# Extension Methods

## Example - short

The following is an extension method for the class `Rock`:

```csharp
internal static class RockExtensions
{
    public static void PaintRed(this Rock rock)
    {
        if (rock == null)
            return;
        
        rock.SetColor("red");
    }
}
```

### Important aspects:

- **Static method** - The extension method must be static.
- **Static class** - The extension method must be placed in a static class.
  - The name of the static class is not important.
- **`this` parameter** - The first parameter must be marked with `this` keyword. It is the object that is extended.
- **Syntactic sugar** - They are a syntactic sugar for calling static methods that have a special first parameter.
  - They can still be called like a normal static methods.

## Example - long

### The `Rock` class

Let's have a class with a `private` field and a `public` method:

```csharp
internal class Rock
{
    private string color;
    
    public void SetColor(string newColor)
    {
        color = newColor;
    }
}
```

Now, let's set the color of that rock:

```csharp
internal static void Main()
{
    Rock rock = new Rock();
    rock.SetColor("red");
}
```

### The `PaintRed` method

If we paint the rock in red very often, we may want, at this point, to create a method specific for painting the rock in red. Something like this:

```csharp
internal class Rock
{
    private string color;
    
    public void SetColor(string newColor)
	{
    	color = newColor;
	}
    
    public void PaintRed()
	{
    	color = "red";
	}
}
```
Now, the call in our `Main` method will look like this:

```csharp
internal static void Main()
{
    Rock rock = new Rock();
    rock.PaintRed();
}
```

### Static `PaintRed` method

There are situations when we do not have access to the source code of the `Rock` class. What can we do then?

I know, I know, let's make the `PaintRed` method static and move it in a different class, so that it can be accessed from different parts of the application:

```csharp
internal class RockHelpers
{
    public static void PaintRed(Rock rock)
    {
        if (rock == null)
            return;
        
        rock.SetColor("red");
    }
}
```

Now, the call in our `Main` method will look like this:

```csharp
internal static void Main()
{
    Rock rock = new Rock();
    RockHelpers.PaintRed(rock);
}
```

### Extension method

The story would have stopped here if it was not for the .NET development team that went further and created a syntactic sugar for calling this type of static methods. They named them extension methods and can be called like normal methods of an instance:

```csharp
internal static void Main()
{
    Rock rock = new Rock();
    rock.PaintRed();
}
```

But, for this to work, we must make two important changes to the static method:

- Put it in a static class;
- Mark the first parameter with `this` keyword.

```csharp
internal static class RockExtensions
{
    public static void PaintRed(this Rock rock)
    {
        if (rock == null)
            return;
        
        rock.SetColor("red");
    }
}
```

> **Note:** I also changed the name of the static class into `RockExtensions` to be more explicit.