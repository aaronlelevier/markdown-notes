# Design Patterns

### Compositor and Composition
Pattern to break up physical relationships of objects and the individual objects behavior

**composition** - for managing the phsyical structure of object relationships, member of one composition group for example

**compositor** - individual object's class that can encapsulate it's own behavior, for example formatting themselves

### Strategy Pattern
Formatting algorithms can use this. If they have the same interface, but a different formatting pattern, then they'd be said to use a strategy pattern because their internal strategy for formatting is different

### Transparent Enclosure
This pattern uses a **decorator pattern** to forward all requests to the object that it wraps, using **delegation**. It decorates the object because it can extend behavior in addtion to what the object does. It has the name 

**transparent** - because it's interface is the same, so the client can't tell that it's calling a different type

**enclosure** - because of the decorator pattern it uses

The **transparent enclosure** should implement the same interface as the class it wraps, and take the class instance it wraps as an argument in it's constructor, so it has a referent, in order to forward all requests 

### Abstract Factory
This pattern uses a *factory creational oblject pattern* to create groups of related objects

A *concrete* Factory can be made at runtime to specify that factory **products** will be of a specific kind

Since each *concrete factory* follows the *abstract factory's* interface, the client doesn't have to be aware of the concrete type, and can call the factory create logic in the same way

