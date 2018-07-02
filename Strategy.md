## Strategy

To define an algorithm in abstract terms so it can be implemented in several different ways, and to allow it to be used across several different clients.
 - It has 3 parts: The first interface represents algorithm, implementations that represent strategy classes. And the client that uses the strategy.
 - Strategy and Template Method serve similar ends. Both are ways to inject some bit of custom code into a larger framework or algorithm. Strategy does so using composition, and Template Method does so using inheritance.
 - Related patterns: [Functional Interface](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Functional_Interface.md), [Template method](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Template_Method.md)
 
### Java Example
 - One common use of Strategy is to create different algorithms that can be used to validate the same set of data
 ```java
 public interface PaymentStrategy {
   public void pay(int amount);
 }
 
 public class CreditCardStrategy implements PaymentStrategy {
   ...
 }
 
 public class PaypalStrategy implements PaymentStrategy {
   ...
 }
 
 public class ShoppingCart {
   ...

   public void pay(int amount, PaymentStrategy paymentMethod){
     paymentMethod.pay(amount);
   }
 }
 ```

### Scala Replacement
 - use higher-order functions that implement the needed algorithms -> no need for interfaces for different strategy implementations
 - pass our strategy functions aroun
 ```scala
 def byCreditCard(amount: Double) = ...
 
 def byPaypal(amount: Double) = ...
 
 def pay(amount: Double, paymentStrategy: Double => Unit) {
   paymentStrategy(amount)
 }
 
 pay(20.5, byCreditCard)
 ```
