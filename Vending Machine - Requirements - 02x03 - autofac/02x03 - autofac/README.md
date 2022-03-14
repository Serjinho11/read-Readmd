# Dependency Injection (Autofac)

Use Autofac to generate the needed dependencies in the VendingMachine application instead of manually creating them with `new` operator.

## Hints

### The `Bootstrapper`

The `Bootstrapper` class is the one that will have the most changes. The `Bootstrapper` is creating al the concrete instances of repositories, payment algorithms, views, use cases, etc. Instead of manually creating all this instances, Autofac can do it for you.

Autofac becomes very useful when the instance that needs to be created has some constructor dependencies. Autofac will automatically create them, too, and provide them to the constructor. And if those dependencies have dependencies of their own, Autofac will go further and create them, too. And so on. It will create the entire tree of dependencies, in order to provide the initial instance, you requested.

### Autofac configuration

Before using Autofac to generate instances, it must be configured. Read about the `ContainerBuilder` class and all the Register methods it provides.

In Vending Machine, `RegisterAssemblyTypes()` may be useful for registering all the use cases at once. Have a look on this method.

### Inject collection of objects

There are situations when a class needs on its constructor a collection of objects of a specific type (for example `IUseCase`).

This articles may help:

- https://stackoverflow.com/questions/15346415/is-it-possible-to-inject-a-list-of-resolved-objects-into-a-constructor-using-aut
- https://autofaccn.readthedocs.io/en/latest/resolve/relationships.html#enumeration-ienumerable-b-ilist-b-icollection-b

