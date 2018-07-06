## Chain of responsibility

The request is processed by the chain until some object handles it. Each object is given a chance to either handle the request (and interrupt the processing), or pass the request to the next handler in the chain. 
 - Pattern allows us to work cleanly with immutable data without storing lots of temporary results.
 - One of example where chain is used is the filter-map-reduce evaluation.
 - Related patterns: [Builder](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Builder.md), [Iterator](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Iterator.md), [Filter-Map-Reduce](https://github.com/OndrejKucera/knowledge_design_patterns/blob/master/Filter-Map-Reduce.md), Builder??

## Java example
 ```java
 public abstract class EventHandler {
    private EventHandler next;
    void setNext(EventHandler handler) { next = handler; }

    public void handle(Event event) {
        if (canHandle(event)) doHandle(event);
        else if (next != null) next.handle(event);
    }

    abstract protected boolean canHandle(Event event);
    abstract protected void doHandle(Event event);
}

public class KeyboardHandler extends EventHandler { // MouseHandler...
    protected boolean canHandle(Event event) {
        return "keyboard".equals(event.getSource());
    }

    protected void doHandle(Event event) { /* ... */ }
}

KeyboardHandler handler = new KeyboardHandler();
handler.setNext(new MouseHandler());
 ```


### Scala Replacement
 - partial function - defined only for subset of the possible values of its arguments.
 ```scala
 case class Event(source: String)

 type EventHandler = PartialFunction[Event, Unit]

 val defaultHandler: EventHandler = PartialFunction(_ => ())

 val keyboardHandler: EventHandler = {
   case Event("keyboard") => /* ... */
 }

 def mouseHandler(delay: Int): EventHandler = {
   case Event("mouse") => /* ... */
 }

 keyboardHandler.orElse(mouseHandler(100)).orElse(defaultHandler)
 ```
