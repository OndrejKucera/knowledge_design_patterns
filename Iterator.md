## Iterator

To iterate through the elements of a sequence in order, without having to index into it. It keeps track of where in the sequence the iterator is currently.

 - Iterator is fundamentally imperative because it relies on mutable state
 - Related patterns: [Tail Recursion](), [Mutual Recursion](), [Filter-Map-Reduce]()

### Java Example
 ```java
 public static List<String> prependHello(List<String> names) {
   List<String> prepended = new ArrayList​<​String​>();
   for (String name : names) {
     prepended.add("Hello, " + name);
   }
   
   return prepended;
 }
 ```

### Scala Replacement
 - It combination of higher-order functions and sequence comprehensions
 - solution is no iterating, no mutation, just a simple higher-order function

 ```scala
 def prependHello(names : Seq[String]) = names.map((name) => "Hello, " + name)
 
 prependHello(Vector("Mike", "John", "Joe"))
 // Vector(Hello, Mike, Hello, John, Hello, Joe)
 ```
 - A sequence comprehension is technique that take one sequence and transform it into another in some sophisticated ways. (bit like map function)
 ```scala
 case class Person(name: String, address: Address)
 case class Address(zip: Int)

 def generateGreetings(people: Seq[Person]) =
   for (Person(name, address) <- people if isCloseZip(address.zip))
   yield "Hello, %s, and welcome to the Lambda Bar And Grille!".format(name)

 def isCloseZip(zipCode: Int) =
   zipCode == 19123 || zipCode == 19103
 ```
