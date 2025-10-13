#java

[[java]]
[[access modifier]]

[[static]]
`void`: no return value

![[Pasted image 20250715172043.png]]

```java
static <T> Stream<T> of(T... values)
```

`<T>` is a [[type parameter]].
`T... values` signifies a **varargs** (variable arguments) parameter. It means you can pass zero or more arguments of type `T` to this method.

