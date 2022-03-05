# Linq (Language Integrated Query)

## Overview

Linq is a way to interrogate collections of data in .NET.

It is composed from a number of extension methods over the `IEnumerable` interface:

## Example

Having the following collection of persons:

```csharp
internal class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int Age { get; set; }
}

List<Person> persons = new List<Person>
{
    new Person { FirstName = "Drusilla", LastName = "Dornez", Age = 24 },
    new Person { FirstName = "Maddy", LastName = "Raith", Age = 42 },
    new Person { FirstName = "Louisa", LastName = "Todd", Age = 67 },
    new Person { FirstName = "Crimson", LastName = "Talbot", Age = 35 },
    new Person { FirstName = "Stephen", LastName = "Skyle", Age = 18 },
    new Person { FirstName = "Kyle", LastName = "Montgomery", Age = 73 },
};
```

Let's find all the first names of the persons that are older than 40 years ordered alphabetically.

```csharp
List<string> firstNames = persons
    .Where(x => x.Age > 40)
    .Select(x => x.FirstName)
    .OrderBy(x => x)
    .ToList();
```

### Dissecting the Query

- The `Where` method is filtering the persons based on the specified predicate and is allowing to pass further only the persons older than 40.
  - It changes the number of items in the collection.
  - It does NOT change the items themselves.

- The `Select` method is passing further to the next method only the `FirstName` value instead of the whole object.
  - It does NOT change the number of items in the collection.
  - It changes the items themselves.

- The `OrderBy` method is acting on the new items that are now strings (the `FirstName` returned by `Select`) and sorts them.
  - The `string` class implements the `IComparable` and `IComparable<T>` interfaces, and, by default they compare the strings alphabetically.

- The `ToList` method is the one that executes the query and creates the resulted `List<string>`
  - All the other methods are not executed immediately, They just describe the query. Only in the end, when the `ToList` method is called, the query is executed.
  - Other similar methods: `ToArray`, `ToDictionary`, etc...

In the end, the `firstNames` variable will contain, `Kyle, Louisa, Maddy`, in this order.

## Query Expression vs Method Chain

The above example is using the Method Chain form. The Linq methods are called one after the other. I will write it again here:

```csharp
List<string> firstNames = persons
    .Where(x => x.Age > 40)
    .Select(x => x.FirstName)
    .OrderBy(x => x)
    .ToList();
```

The same query can be written as a query expression:

```csharp
List<string> firstNames = (from person in persons
                            where person.Age > 40
                            orderby person.FirstName
                            select person.FirstName).ToList();
```

> **Note:** Usually, we prefer to use the Method Chain form. It is more ordered.