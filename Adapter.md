## Adapter

Pattern converts interface of a class into expected interface, allowing classes with incompatible interfaces to work together. Adapter is useful for integrating existing component as a wrapper.

### Java Example
  ```java
  public interface Log {
    void warning(String message);
    void error(String message);
  }

  public final class Logger {
    void log(Level level, String message) { /* ... */ }
  }

  public class LoggerToLogAdapter implements Log {
    private final Logger logger;

    public LoggerToLogAdapter(Logger logger) { this.logger = logger; }

    public void warning(String message) {
        logger.log(WARNING, message);
    }

    public void error(String message) {
        logger.log(ERROR, message);
    }
  }

  Log log = new LoggerToLogAdapter(new Logger());
  ```

### Scala Replacement
 - When expected type of expression is Log, yet a Logger instance is used, Scala compiler will automatically wrap that instance in the adapter class.
 ```scala
 trait Log {
  def warning(message: String)
  def error(message: String)
 }

 final class Logger {
  def log(level: Level, message: String) { /* ... */ }
 }

 implicit class LoggerToLogAdapter(logger: Logger) extends Log {
  def warning(message: String) { logger.log(WARNING, message) }
  def error(message: String) { logger.log(ERROR, message) }
 }

 val log: Log = new Logger()
 ```
