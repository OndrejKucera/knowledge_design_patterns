## Template Method

To specify the outline of an algorithm, letting callers plug in some of the specifics

 - Create a skeleton for some algorithm and let callers plug in the details.
 - Consists of an abstract class that defines some operation
 - Related patterns: [Functional Interface](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Functional_Interface.md), [Strategy](), [Builder](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Builder.md)
 
### Java Example
 -
 ```java
 public abstract class TemplateExample{
   public void anOperation(){
     subOperationOne();
     subOperationTwo();
   }

   protected abstract void subOperationOne();
   protected abstract void subOperationTwo();
}
 ```

### Scala Replacement
 - Instead of classes to implement suboperations, we’ll use higher-order functions.
 - Instead of relying on subclassing, we’ll rely on function composition.
 ```scala
 
 ```
