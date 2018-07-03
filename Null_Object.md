## Null Object

To avoid scattering null checks throughout our code by encapsulating the action
 - Lack of a value in Java is represented by a null reference
 - the problem is that this handeling is often repeating in the code
 - Solution to this is to create a singleton null object that has the same interface as our real objects but implements our default behavior. We can then use this object in place of null references.
 - trade-offs: the program won't fail fast
 
### Java Example
 ```java
 if(null == someObject){
   // default null handling behavior
 } else {
   someObject.someMethod()
 }
 ```

### Scala Replacement
 - replace null references and Null Object
 - `Option` indicates that we may not have a value in a type-safe manner.
   - subtypes: `Some` carries a value, singleton object `None` which does not.
 - `Either` provides a value when we’ve got one and a default or error value when we don’t.
 ```scala
 aSome.getOrElse("default value")
 ```
