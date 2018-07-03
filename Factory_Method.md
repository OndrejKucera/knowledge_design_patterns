## Factory method

Interface for creating an object that encapsulates the actual class instantiation in a method, and lets subclasses decide which class to instantiate.
 - The pattern hide the construction of object and select which class to instantiate.
 - It can cache the objects and coordinate access to shared resources.

### Java Example
 ```java
 public interface Animal {}

 private class Dog implements Animal {}

 private class Cat implements Animal {}

 public class AnimalFactory {
    public static Animal createAnimal(String kind) {
        if ("cat".equals(kind)) return new Cat();
        if ("dog".equals(kind)) return new Dog();
        throw new IllegalArgumentException();
    }
 }

 AnimalFactory.createAnimal("dog");
 ```

### Scala Replacement
 - The factory method is defined in “companion object” – a special singleton object 
 ```
 trait Animal
 private class Dog extends Animal
 private class Cat extends Animal

 object Animal {
   def apply(kind: String) = kind match {
     case "dog" => new Dog()
     case "cat" => new Cat()
   }
 }

 val dog = Animal("dog")
 ```
