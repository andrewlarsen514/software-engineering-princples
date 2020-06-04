# software-engineering-princples
Repository containing examples and walkthroughs of Concord's Core Engineering Principles. These principles are as follows:

1. Clean Code
2. Fast Feedback
3. Simplicity
4. Repeatability
5. Operationally Ready
6. Secure

The remainder of the document contains an introduction to each principle along with practices to help implement each principle respectively.

## Clean Code

Clean code is the idea that software should be easy to understand what’s it’s doing, it’s easy to maintain, and it’s obvious what it’s doing.

So what are some practices that we can do to write “clean code”

### Meaningful names

Naming is hard in software - however it goes a long way into making code easy to understand and maintain.  When creating classes, methods, variables, etc it’s important that the name makes it clear what it is for.   For example listOfUsers is much more helpful than list.  To take that a step further, listOfUsersToRemove is even more explicit and tells exactly that that list is going to be used for.  

This can also be useful for determining if a class or method is doing too much (and thus violating the Single Responsibility Principle).  If you cannot think of a clear and concise name to describe what a method is doing, that is probably a sign it’s doing too much!

Naming consistency is also very important when writing clean code.  Picking a consistent name for an entity throughout a code base can go a long way in helping others (and yourself) improve the readability of a code base.

### Comments

The phrase “self documenting code” often makes some engineer’s skin crawl - but there is merit to this principle.  Use of comments should be used only to explain why we’re doing something in the code.  For example, a weird workaround to deal with some quirky external dependency.  Comments should never describe what code is doing.  This is a clear sign that it is overly complex, the naming is unclear, or both.


### Functions

There are a number of practices to keep in mind when writing clean functions including:

Keep methods small
Do one thing
Small number of arguments
Easy to test

***Keep Methods Small***

“The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that.”

Functions should be small, do one thing, and be easy to test.

A function, generally, should be no more than a handful of lines.  There is no magic number here, I can’t tell you how small a function should be but I know a function is too large when i see it.  Some common ways to tell if a function is too long:

1. Lots of if/else statements
2. It’s hard to tell what the function does “at a glance”
3. You find yourself writing comments to explain what something is doing

If a method hits any of the above cases that often means you may want to consider factoring out pieces of the function into other smaller functions that the method in question calls.

***Do one thing***

A function should do one thing, and do it well.  Said another way, a method should have only one reason to change.  This means that a function should only be concerned with a specific area or part of a domain, which given a new or changed requirement, would require said function to be modified.  

Side effects are a common code small that can tell us a function is not doing one thing only.  Side effects are when a method does something that is not overtly obvious.  For example, take the following method that returns the next the integer after the provided integer:

```java
private Integer getNextNumber(final Integer number){
    final Integer nextNumber = ++number;
    return nextNumber;
}
```

In the above function we return a new number that directly follows the provided number.  While this may be a contrived example, it as an interesting side effect.  This will not only return the next number, but will also increment the number passed in!  To avoid side effects the method could be re-written as:

```java
private Integer getNextNumber(final Integer number){
    final Integer nextNumber = number + 1;
    return nextNumber;
}
```

***Arguments***

A long list of arguments is often a code smell that should be avoided.  If a method has more than, say, 3 arguments it’s probably a sign that either.

1. The method is doing too much
2. There is a new Class that should be introduced to represent the data.

Another code smell relating to arguments is the idea of “flag arguments”.  These are arguments that change the behavior of the method based on a boolean value.  These can make the methods less obvious as to what they’re doing.  

***Easy to test***

Above all, functions (and of course their containing classes) should be easy to test.  Simply put - if it’s painful to setup your unit tests for a given method under test, that is a sign that the method is doing too much and should be refactored.  This pain can include setting up mocks, test data, etc.  If our classes and methods are small and “do one thing” our unit tests should not require a large amount of setup.

TODO - Example of how to refactor a class with many components into smaller components
