## Decorator

It allows to change the behavior of an existing class.
 - To add behavior to an individual object rather than to an entire class of objects.
 - There is class that we need to add some behavior to but we can’t change the existing class. But we can’t change every other part of the system where the class is used. Or the class may be part of a library that we can’t, or don’t want to, modify.
 - Also know as Wrapper
 - Related patterns: [Strategy](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Strategy.md), [Builder](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Builder.md)
 
### Java Examples
 - We have 2 parts, interface and implemantation in class which we don't want to change
 - Then we implement the interface with an abstract decorator class as a solution
 ```java
 public interface Troll {
   void attack();
   void fleeBattle();
 }

 public class SimpleTroll implements Troll { ... }

 public class DecoratedTroll implements Troll {
   private Troll troll;

   public ClubbedTroll(Troll t) {
     this.troll = t;
   }
  
   @Override
   public boolean attack() {
     troll.attack();
     // some other decorated funcionality
   }

   @Override
   public void fleeBattle() {
     decorated.fleeBattle();
     // some other decorated funcionality
   }
 }
 
 decoratedTroll = new DecoratedTroll(troll);
 decoratedTroll.attack();
 decoratedTroll.fleeBattle();
 ```

### Scala Replacement
 -  Create new higher-order function that takes in original-function and returns a new function that runs the original-function and some new functionality.
 ```scala
 def attack() = ...
 def fleeBattle() = ...
 
 def decorateMove(originalFn: () => Unit) =
   () => {
     calcFn()
     // new functionality
   }
   
 val decoratedAttack = decorateMove(attack)
 val decoratedfleeBattle = decorateMove(fleeBattle)
 ```
