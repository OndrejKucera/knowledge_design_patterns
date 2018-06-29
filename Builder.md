## Builder

To create an **immutable object** using a friendly syntax for setting attributes.

 - Examples in `StringBuilder` and `StringBuffer`
 - To create immutable object in Java, only with Constructor. This ways has two cons. 
 - Related patterns: [Focused Mutability]()

### Java example
 - lot of code for such a basic task :(
 ```java
 public class ImmutablePerson {
   private final String firstName;
   // more attributes
  
   public String getFirstName() {
     return firstName;
   }
   // more getters

   private ImmutablePerson(Builder builder) {
     firstName = builder.firstName;
     // set more attributes
   }

   public static class Builder {
     private String firstName;
     // more attributes
    
     public Builder firstName(String firstName) {
       this.firstName = firstName;
       return this;
     }
     // more setters

     public ImmutablePerson build() {
       return new ImmutablePerson(this);
     } 	
   }
  
   public static Builder newBuilder() {
     return new Builder();
   }
 }
 ```

### Scala Replacement
 - Three different techniques to create immutable object
 - Immutable classes: plain classes that only contain immutable attributes, neccesary to code hash codes for equality, or a nice representation when printed
 ```scala
 class Person(
   val firstName: String,
   val middleName: String = "",
   val lastName: String
 )
 ```
 - Case classes: special kind of class intended to work with Scala’s pattern matching
 ```
 case class PersonCaseClass(
   firstName: String,
   middleName: String = "",
   lastName: String
 )
 ```
 - Tuples: immutable data structures that let us group data together
 ```
 def p = ("John", "Adams")
 ```
 
