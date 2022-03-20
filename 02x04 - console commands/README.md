# Dependency Injection (Autofac)

## Overview

In the Vending Machine application, the current implementation of the use cases violates the Single Responsibility Principle. The use cases play two different roles:

- In Presentation Layer
  - The use cases have `Name`, `Description` and `CanExecute` properties that are used in Presentation Layer to describe and execute the command.
- In Business Layer
  - The `Execute` method, on the other hand, is part of the Business Layer. It implements the business rules.

So, the use cases have two different reasons to change, from two different directions:

- when the business rules changes
- when the interface changes.

## Requirement

Fix the violation of the Single Responsibility Principle.

## Suggestions

One way to respect the Single Responsibility Principle is to create Command classes in the Presentation Layer for each action that can be performed by the user. These Commands will provide the visual details and, when triggered, they will execute the needed Use Case.

These Commands are, in this Console Application, the equivalent of a Button from a GUI Application.

### Problem

By doing so we will encounter a problem. The Use Cases have, in general multiple dependencies. Some of them have dependencies of their own. This makes them harder to instantiate.

### Solution 1 - Duplicate all Use Case’s dependencies in the Command

One way to solve this is by allowing the Command classes to receive all the dependencies needed later to instantiate the Use Case.

**Cons**: This will generate allot of dependencies for the Command that are not really used by the Command and will make the code harder to read and work with.

Let’s see if we can avoid this.

### Solution 2 – Use Dependency Resolver

The Command should use the Dependency Resolver to obtain an instance of the needed Use Case.

**Pros**: Commands will not have fake dependencies.

**Cons**: Commands will depend upon the Dependency Resolver. So, this solution tightly couples each Command instance to the concrete Dependency Resolver. Let’s say it again: This solution tightly couples the presentation Layer to the concrete a detail of the Bootstrapper Module.

We are trying to avoid this type of coupling, to allow ourselves the freedom of easily changing the Dependency Injection framework later in the project’s development.

Let’s see if we can do better.

### Solution 3 – Use Factory Pattern

Actually, by using the Dependency Resolver we are already using the Factory Pattern. What we do not like is the tight coupling. We can solve this by creating an interface: `IUseCaseFactory` that will create the Use Case instance when the Command needs it. Now, the command will receive just an instance of this interface.

The concrete implementation of the `UseCaseFactory` will use, internally, the Dependency Resolver instance to actually create the Use Cases.

 ![Factory Pattern](README.resources\factory-pattern.drawio.png)

**Note:** Some of the Commands will also need an instance of `IAuthenticationService` to decide if they are visible or not. But this is fine, it is a real dependency. It is used by the Command itself.