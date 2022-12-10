# Interface Segregation Principle (ISP)

The Interface Segregation Principle (ISP) is a principle of object-oriented design that states that no client should be forced to depend on methods it does not use. This means that classes should have small, specific interfaces that only include the methods that are actually needed by the client classes. This allows for better code organization and maintainability, as well as flexibility to accommodate future changes in requirements. To implement the ISP, developers can use techniques such as [abstraction](../glossary/abstraction.md) and [composition](../glossary/composition.md).

> #### Explain Interface Segregation Principle (ISP) like I'm five
>
> The Interface Segregation Principle is like a toolbox. In a toolbox, there are different tools for different jobs. For example, there might be a hammer for pounding nails, and a screwdriver for turning screws. And even though the hammer and the screwdriver are both tools, they are not used for the same thing. So if you want to use the hammer, you don't have to look through the whole toolbox to find it. You can just go to the part of the toolbox where the hammers are, and take out the one you need. In object-oriented programming, the tools are like methods, and the toolbox is like an interface. The Interface Segregation Principle says that interfaces should be organized into small, specific parts, so that you can easily find the methods you need without having to look through lots of other methods that you don't need.

| [Previous](03\_liskov\_substitution\_principle.md) | [Index](../) | [Next](05\_dependency\_inversion\_principle.md) |
| -------------------------------------------------- | ------------ | ----------------------------------------------- |
