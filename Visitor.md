## Visitor

Pattern allows to add new operations to an existing data type. Visitor allows to fairly easily add new operations to an existing data type, but it makes adding new implementations of the data type difficult.
 - If we want to add a new operation, we just need to create a new visitor and write code such that it knows how to visit each existing concrete element.
 - It’s hard to add new implementations. To do so, we’d need to modify all of the existing visitors to know how to visit the new data implementation. If those Visitor classes are outside of our control, it may be impossible!
 - Relared patterns: [Decorator](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Decorator.md)
 
### Java Example
 ```java
 public interface ItemElement {
   public int accept(ShoppingVisitor visitor);
 }
 
 public class Book implements ItemElement {
   private int price;
   private String isbnNumber;
   ...
   @Override
   public int accept(ShoppingVisitor visitor) {
     return visitor.visit(this);
   }
 }
 
 public class Fruit implements ItemElement {
   private int price;
   private String name;
	  ...
   @Override
   public int accept(ShoppingCartVisitor visitor) {
     return visitor.visit(this);
   }
 }
 
 public interface ShoppingVisitor {
   int visit(ItemElement element);
 }
 
 public class ShoppingVisitorImpl implements ShoppingVisitor {
   @Override
   public int visit(ItemElement element) {
     element.getPrice()
   }
 }
 
 public class ShoppingClient {
   public static void main(String[] args) {
     ItemElement[] items = new ItemElement[]{new Book(20, "1234"),new Book(100, "5678"),
         new Fruit(10, "Banana"), new Fruit(5, "Apple")};

     int total = 0;
     ShoppingVisitor visitor = new ShoppingVisitorImpl();
     for(ItemElement item : items){
       total += item.accept(visitor);
     }

     System.out.println("Total Cost = " + total);
   }
 }
 ```

### Scala Replacement
- Extending the operations in an existing library that uses Scala’s implicit conversion system. This allows us to add new operations to existing libraries.
 ```scala
 trait ItemElement {
   def name: String
   def price: Float
 }
 
 class Book(val name: String, val price: Float) extends ItemElement
 class Fruit(val name: String, val price: Float) extends ItemElement
 
 val items: Array[ItemElement] = Array(new Book("firstBook", 20),
     new Book("SecondBoook", 45), new Fruit("Banana", 10), new Fruit("Apple", 5))
 
 implicit class ExtendedItem(item: ItemElement) {
   def getDiscountPrice = item.price * 0.9
 }
 
 items.foldLeft(0.0) {(sum, item) => sum + item.price}
 
 // using new operation
 items.foldLeft(0.0) {(sum, item) => sum + item.getDiscountPrice}
 ```
 - Solution takes advantage of Scala’s mix-in inheritance and traits, which allows us to easily add both new operations and new implementations to a data type.
 ```scala
 trait PerimeterShapes {  // we can use Scala’s traits as modules here
   trait Shape {
     def perimeter: Double
   }
 
   class Circle(radius: Double) extends Shape {
     def perimeter = 2 * Math.PI * radius
   }
 
   class Rectangle(width: Double, height: Double) extends Shape {
     def perimeter = 2 * width + 2 * height
   }
 }
 ```
 ```scala
 object FirstShapeExample extends PerimeterShapes {
   val aCircle = new Circle(4);
   val aRectangle = new Rectangle(2, 2);	
 }
 
 import com.mblinn.mbfpp.oo.visitor.FirstShapeExample._
 aCircle.perimeter      // 25.132
 aRectangle.perimeter   // 8.0
 ```
 
 
 ```scala
 // Extending our Shape with new operations
 trait AreaShapes extends PerimeterShapes {
   trait Shape extends super.Shape {
     def area: Double
   }

   class Circle(radius: Double) extends super.Circle(radius) with Shape {
     def area = Math.PI * radius * radius
   }

   class Rectangle(width: Double, height: Double) extends super.Rectangle(width, height) with Shape {
     def area = width * height
   }	
 }
 ```
 ```scala
 object SecondShapeExample extends AreaShapes {
   val someShapes = Vector(new Circle(4), new Rectangle(2, 2));
 }

 import com.mblinn.mbfpp.oo.visitor.SecondShapeExample._
 for(shape <- someShapes) yield shape.perimeter  // Vector(25.132741228718345, 8.0)
 for(shape <- someShapes) yield shape.area       // Vector(50.26548245743669, 4.0)
 ```
 
 
 ```scala
 trait MorePerimeterShapes extends PerimeterShapes {
   class Square(side: Double) extends Shape {
     def perimeter = 4 * side;
   }
 }

 trait MoreAreaShapes extends AreaShapes with MorePerimeterShapes {
   class Square(side: Double) extends super.Square(side) with Shape {
     def area = side * side
  }
 }
 ```
 ```scala
 object ThirdShapeExample extends MoreAreaShapes {
   val someMoreShapes = Vector(new Circle(4), new Rectangle(2, 2), new Square(4));
 }
 
 import com.mblinn.mbfpp.oo.visitor.ThirdShapeExample._
 for(shape <- someMoreShapes) yield shape.perimeter   // Vector(25.132741228718345, 8.0, 16.0)
 for(shape <- someMoreShapes) yield shape.area        //Vector(50.26548245743669, 4.0, 16.0)
 ```
