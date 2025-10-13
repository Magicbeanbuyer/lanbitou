#java

**Generic Classes:** A class definition that includes one or more [[type parameter]]s.

```java
class Box<T> { // T is a type parameter for the Box class
    private T content;

    public Box(T content) {
        this.content = content;
    }

    public T getContent() {
        return content;
    }
}

// When you use the class, you specify the concrete type:
Box<String> stringBox = new Box<>("Hello"); // T becomes String
String value = stringBox.getContent();

Box<Integer> integerBox = new Box<>(123); // T becomes Integer
Integer number = integerBox.getContent();
```