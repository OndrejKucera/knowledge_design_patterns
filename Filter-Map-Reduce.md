## Filter-Map-Reduce

To manipulate a sequence (list, vector, and so on) declaratively using filter, map, and reduce to produce a new one
 - `filter` function to select the elements we care about
 - `map` to transform each element
 - `reduce`, sometimes known as fold, to combine the results.
 - Sometimes, it could be hard to write algorithm with filter-map-reduce style, then we should look at the related paterns.
 - Related patterns: [Replacing Iterator](), [Tail Recursion](), [Mutual Recursion]()

### Scala Example
 ```scala
 Vector(20.0, 4.5, 50.0, 15.75, 30.0, 3.5)
   .filter(price => price >= 20)
   .map(price => price * 0.10)
   .reduce((total, price) => total + price) // 10.0
 ```
