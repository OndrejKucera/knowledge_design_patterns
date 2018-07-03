## Null Object

To avoid scattering null checks throughout our code by encapsulating the action
 - Lack of a value in Java is represented by a null reference
 - the problem is that this handeling is often repeating in the code
  if(null == someObject){
   // default null handling behavior
 } else {
   someObject.someMethod()
 }
 - Solution to this is to create a singleton null object that has the same interface as our real objects but implements our default behavior. We can then use this object in place of null references.
 - trade-offs: the program won't fail fast
 
### Java Example
 - Minimizing the surface area of our code where we need to deal with null,
 ```java
 class NullPerson extend Person {
   ...
 }
 
 public Person buildPerson(String firstName, String lastName) {
   if(null != firstName && null != lastName)
     return new RealPerson(firstName, lastName);
   else
     return new NullPerson();
 }
 ```

### Scala Replacement
 - replace null references and Null Object
 - `Option` indicates that we may not have a value in a type-safe manner.
   - subtypes: `Some` carries a value, singleton object `None` which does not.
   - if you use option others can imidiately know how to deal with deal with missing value
   ```scala
   def aSome = Some("foo")

   aSome.getOrElse("default value")
   aSome.map((s) => s.toUpperCase)
   ```
 - `Either` provides a value when we’ve got one and a default or error value when we don’t.
 
 - In Scala, there is no need to create Null Object type. We can use `Option`
 ```scala
 def buildPerson(firstNameOption: Option[String], lastNameOption: Option[String]) =
   (for(
     firstName <- firstNameOption;
     lastName <- lastNameOption)
   yield Person(firstName, lastName)).getOrElse(Person("Default First Name", "Default Second Name"))
 
 buildPerson(Some("Mike"), Some("Linn"))
 buildPerson(Some("Mike"), None)
 ```
