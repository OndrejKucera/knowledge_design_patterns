## Tail Recursion

To repeat a computation without using mutable state and without overflowing the stack
  - Iteration is an imperative technique that requires mutable state
  - Recursion problem: each recursive call will create frame on the program’s call stack.
  - Tail call optimization TCO use only single frame 
  - Advantage of tail recursion over iteration is simply that it eliminates a source of mutability in the language
  - Realted patterns: [Iterator](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Iterator.md), [Mutual Recursion](), [Filter-Map-reduce]()
  
In Scala’s case, the Scala compiler will attempt to translate tail recursive calls into iteration behind the scenes, and Scala provides an annotation, @tailrec, that can be placed on functions that are meant to be used in a tail recursive manner. If the function is called recursively without being in the tail position, the compiler will generate an error.
  
### Scala Example
 - stack consuming recursion
 ```scala
 public static int sumRecursive(int upTo) {
   if (upTo == 0)
     return 0;
   else
     returnupTo + sumRecursive(upTo - 1);
 }
 ```
 - tail recursion
 ```scala
 public static int sumTailRecursive(int upTo, int currentSum) {
   if (upTo == 0)
     return currentSum;
   else
     return sumTailRecursive(upTo - 1, currentSum + upTo);
}
 ```
