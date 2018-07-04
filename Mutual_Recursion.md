## Mutual Recursion

To use mutually recursive functions to express certain algorithms, such as walking tree-like data structures, recursive descent parsing, and state machine manipulations.
 - Some of the more complex problems require solutions where functions can call each other recursively.
 - Mutual recursion does the trick called a **trampoline**. Instead of making mutually recursive calls directly, we return a function that would make the desired call, and we let the compiler or runtime take care of the rest.
 - Related patterns: [Iterator](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Iterator.md), [Filter-Map-reduce]() 

### Scala Example
 ```scala
 def isOdd(n: Long): Boolean = if (n == 0) false else isEven(n - 1)
 def isEven(n: Long): Boolean = if (n == 0) true else isOdd(n - 1)
 
 isEven(1000)   // true
 isOdd(100001)  // java.lang.StackOverflowError
 ```
 - Support for trampolining in Scala lives in `scala.util.control.TailCalls`, and it comes in two parts. The first is a `done` function, which is used to return the final result from the recursive calls. The second is a `tailcall` function, which is used to make the recursive calls.
 ```scala
 def isOddTrampoline(n: Long): TailRec[Boolean] =
   if (n == 0) done(false) else tailcall(isEvenTrampoline(n - 1))
 def isEvenTrampoline(n: Long): TailRec[Boolean] =
   if (n == 0) done(true) else tailcall(isOddTrampoline(n - 1))
   
 isOddTrampoline(100001).result // true
 ```
