## Dependency Injection

To compose objects together
 - Not having an object instantiate its own dependencies allows to easily inject different dependency implementations into an object
 - Dependency Injection is to inject an object’s dependencies through a constructor or setter.
 - It can be also done by dependency-injection framework
 - Benefits: It makes it easy to change the implementation for a given dependency -> good for unit test.
 - Related patterns: [Builder](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Builder.md), [Domain-Specific Language]()
 
### Java Examples
 ```java
 public class MovieService {
   private MovieDao movieDao;
   private FavoritesService favoritesService;
   public MovieService(MovieDao movieDao, FavoritesService favoritesService){
     this.movieDao = movieDao;
     this.favoritesService = favoritesService;
   } 	
 }
 ```

### Scala Replacement
 - Classic Dependency Injection can be used in Scala. We can even use familiar Java frameworks like Spring or Guice
 - Scala pattern called the **Cake pattern** uses Scala traits and self-type annotations to accomplish the same sort of composition and structure that we get with Dependency Injection without the need for a container.
   - encapsulate the dependencies we want to inject inside of top-level traits
   - use annotation and mixin inheritance to specify wiring in a typesafe manner
 ```scala
 trait MovieDaoComponentTestImpl extends MovieDaoComponent {
   class MovieDaoTestImpl extends MovieDao {
     def getMovie(id: String): Movie = new Movie("43", "A Test Movie")
   }
 }
 
 trait FavoritesServiceComponentTestImpl extends FavoritesServiceComponent {
   class FavoritesServiceTestImpl extends FavoritesService {
     def getFavoriteVideos(id: String): Vector[Video] = Vector(new Video("2"))
   }
 }
 
 trait MovieServiceComponentImpl {
   this: MovieDaoComponent with FavoritesServiceComponent =>
   val favoritesService: FavoritesService
   val movieDao: MovieDao
   
   class MovieServiceImpl {
     def getFavoriteDecoratedMovies(userId: String): Vector[DecoratedMovie] =
       for (
         favoriteVideo <- favoritesService.getFavoriteVideos(userId);
         val movie = movieDao.getMovie(favoriteVideo.movieId)
       ) yield DecoratedMovie(movie, favoriteVideo)
   } 	
 }

 object TestComponentRegistery extends MovieServiceComponentImpl
   with FavoritesServiceComponentTestImpl with MovieDaoComponentTestImpl {
   
   val favoritesService = new FavoritesServiceTestImpl
   val movieDao = new MovieDaoTestImpl
   val movieService = new MovieServiceImpl 	
 }
 ```
