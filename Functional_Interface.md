## Functional Interface

It consists of an interface with a single method with a name like run, execute, perform, apply, or some other generic verb. Functional Interface lets us call an object as if it were a function, which lets us pass verbs around our program rather than nouns.

 - also called Functor, Function object
 - same as interfaces: `Runnable`, `Callable`, `Comparator` with their methods
 - You can use it as anonymous or named class
 - Related patterns: [Command](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Command.md), [Template method](), [Strategy](), [Builder](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Builder.md)

### Java example
 ```java
 Comparator personComparator = new Comparator<Person>() {
   public int compare(Person p1, Person p2) {
     return p1.getFirstName().compareTo(p2.getFirstName());
   }
 }
 
 Collections.sort(people, personComparator);
 ```

### Scala Replacement
 - function as high order
 ```scala
 case class Person(firstName: String, lastName: String)
 val comparator: (Person, Person) => Boolean = (p1, p2) => p1.lastName < p2.lastName
 people.sortWith(comparator)
 ```
 

  
