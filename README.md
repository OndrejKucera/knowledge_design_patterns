Knowledge - Scala Design Patterns
====================

Note: Here are not exhausted knowledge about patterns.

## Replacing Object-Oriented Patterns with Functional Approach
 - [Functional Interface](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Functional_Interface.md)
 - [State-Carrying Functional Interface](https://github.com/OndrejKucera/knowledge_patterns/blob/master/State-Carrying_Functional_Interface.md)

#### 1. Creational (gof)
  - Patterns create objects for you, rather than having you instantiate objects directly. This makes program more flexibility in deciding which objects need to be created for a given case.
    - [Builder](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Builder.md)
    - [Factory method](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Factory_Method.md)
    - [Singleton](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Singleton.md)

#### 2. Behavioral (gof)
 - Patterns are specifically concerned with communication between objects.
   - [Command](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Command.md)
   - [Iterator](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Iterator.md)
   - [Template Method](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Template_Method.md)
   - [Strategy](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Strategy.md)
   - [Visitor](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Visitor.md)
   - [Chain of responsibility](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Chain_Of_Responsibility.md)
   - [Dependency Injection](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Dependency_Injection.md) (not gof)
   - [Null Object](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Null_Object.md) (not gof)
   - Value Object (not gof)

#### 3. Structural (gof)
 - Patterns show class and object composition. They use inheritance to compose interfaces and define ways to compose objects to obtain new functionality.
   - [Decorator](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Decorator.md)
   - [Adapter](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Adapter.md)

## Functional Patterns
Functional programming has its own set of patterns that have evolved out of the functional style.
1. [Tail Recursion](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Tail_Recursion.md)
2. [Mutual Recursion](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Mutual_Recursion.md)
3. [Filter-Map-Reduce](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Filter-Map-Reduce.md)
4. Memoization - To cache the results of a pure function call to avoid performing the same computation more than once
5. Lazy sequence - To create a sequence whose members are computed only when needed—this allows us to easily stream results from a computation and to work with infinitely long sequences
6. Focused Mutability - To use mutable data structures in small, performance-sensitive parts of a program hidden inside of a function while still using immutable data throughout the majority
7. Customized Control Flow
8. Domain-Specific Language

---
The main resources were book [Functional Programming Patterns in Scala and Clojure](https://www.goodreads.com/book/show/17610214-functional-programming-patterns-in-scala-and-clojure), the blog post from [pavelfatin.com](https://pavelfatin.com/design-patterns-in-scala/), and wikipedia page [Design_Patterns](https://en.wikipedia.org/wiki/Design_Patterns#Patterns_by_Type)
