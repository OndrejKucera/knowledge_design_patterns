## Singleton

Pattern restricts the instantiation of a class to one object, and provides a global point of access to it.
  - Singleton is probably the most well-known design pattern in Java. It is a clear sign of the missing language feature.
  
### Java Example
  - While Java language includes `static` keyword, static members are not associated with any object, and static member classes cannot implement an interface. Thus, the concept of static methods in Java goes against the basic OOP premise that everything is an object. 
 ```java
 public final class LazySingleton {
   private static volatile LazySingleton instance = null;
    
   private LazySingleton() {}
 
   public static LazySingleton getInstance() {
     if (instance == null) {
       synchronized (LazySingleton.class) {
         instance = new LazySingleton();
       }
     }
     
     return instance;
   }
 }
 
 LazySingleton.getInstance()
 ```
 
 - the `Enum` is also used for singleton in Java because of thread-safety
 ```java
 public enum EnumSingleton {
   INSTANCE;
   public void someMethod() {
     // some class member
   }
 }
 
 EnumSingleton.INSTANCE.someMethod()
 ```

### Scala Replacement
  - Scala provides concise direct realization of the singleton pattern in the language with `object`
  - Objects can inherit methods from classes or interfaces.
  - It is thread-safe and it has on-demand initialization.
  ```scala
  object Cat extends Runnable {
    def run() {
      // do nothing
    }
  }

  Cat.run()
  ```
