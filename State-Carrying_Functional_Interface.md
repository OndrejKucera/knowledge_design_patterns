## State-Carrying Functional Interface

For encapsulating state along with program logic ([functional interface](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Functional_Interface.md)) and passing around.

 - Functional Interface implementations that need state using **closure**
 - Related patterns: [Command](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Command.md), [Template method](), [Strategy](), [Builder](https://github.com/OndrejKucera/knowledge_patterns/blob/master/Builder.md)
 
 ### Java example
  - To carry state around by creating fields on the class and by providing setters.
  ```scala
  public class ComposedComparator<T> implements Comparator<T> {
    private Comparator<T>[] comparators;
    
    public ComposedComparator(Comparator<T>... comparators) {
      this.comparators = comparators;
    }
    
    @Override
    public int compare(T o1, T o2) {
      //Iterate through comparators and call each in turn.​
    }
  }
  ```
 
 ### Scala Replacement
  - A closure wraps up a function along with the state available to it when it was created. 
  - No need to do anything special to create a closure; the compiler and runtime take care of it.
  ```scala
  def makeComposedComparison(comparisons: (Person, Person) => Int*) = 	
    (p1: Person, p2: Person) => comparisons.map(cmp => cmp(p1, p2)).find(_ != 0).getOrElse(0)
  ```
