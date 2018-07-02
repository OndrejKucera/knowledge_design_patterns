## Strategy

To define an algorithm in abstract terms so it can be implemented in several different ways, and to allow it to be used across several different clients.
 - It as 3 parts: One interface represents algorithm, another interface that represent strategy classes. And the client tha uses the strategy. 
 - Related patterns: [Functional Interface](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Functional_Interface.md), [Template method](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Template_Method.md)
 
### Java Example
 - One common use of Strategy is to create different algorithms that can be used to validate the same set of data
 ```java
 
 ```

### Scala Replacement
 - use higher-order functions that implement the needed algorithms -> no need for interfaces for different strategy implementations
 - pass our strategy functions aroun
 ```scala
 
 ```
