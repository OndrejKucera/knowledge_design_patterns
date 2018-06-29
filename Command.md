## Command

Contains command interface, its implementations, client (that creates the Command) and invoker (responsible to run Command)

- Use case: to keep a history, callback functionality, the undo functionality
- A simple example is a logging Command
- Related patterns: [Functional Interface](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Functional_Interface.md)

### Java example 
 - http://java-design-patterns.com/patterns/command/

### Scala Replacement
- Instead of creating a Command interface and implementation, we’ll simply use higher-order functions
- Instead of creating a separate class to act as an invoker, we’ll just create an execution function
 ```scala
 class CashRegister(var total: Int) {
   def addCash(toAdd: Int) {
     total += toAdd
   }
 }
 
 def makePurchase(register: CashRegister, amount: Int) = {
   () => {
     println("Purchase in amount: " + amount)
     register.addCash(amount)
   }
 }
 
 var purchases: Vector[() => Unit] = Vector()	
 def executePurchase(purchase: () => Unit) = {
   purchases = purchases :+ purchase
   purchase()
 }
 ```
 
 ```scala
 val register = new CashRegister(0)
 val purchaseOne = makePurchase(register, 100)
 val purchaseTwo = makePurchase(register, 50)
 
 executePurchase(purchaseOne)
 executePurchase(purchaseTwo)
 register.total
 ```



