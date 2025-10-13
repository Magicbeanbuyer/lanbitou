#java 

[[Java]] Classes within the same package are automatically visible to each other without any explicit `import` statements. Therefore, you do **not** need to import classes within the same package in Java.

A Java class file is a file (with the .class filename extension) containing Java bytecode that can be executed on the Java Virtual Machine (JVM). A Java class file is usually produced by a Java compiler from Java programming language source files (.java files) containing Java classes (alternatively, other JVM languages can also be used to create class files). If a source file has more than one class, each class is compiled into a separate class file. Thus, it is called a .class file because it contains the bytecode for a single class.

### classpath
The `classpath` is simply a list of directories, JAR files, and ZIP archives to search for class files.

The default value for the `classpath` is the current directory. 

[Tutorial on how Java classpath works | Javarevisited](https://medium.com/javarevisited/back-to-the-basics-of-java-part-1-classpath-47cf3f834ff)
### instance variable

If a class variable (also known as a field or member variable) in Java has neither `public` nor `private` [[access modifier]], it has package-private (or default) access.

### methods
[[method signature]]

constructor 
The constructor's name is always the same as the class name.

If the programmer does not define a constructor for a class, Java automatically creates a default one for it. A default constructor is a constructor that doesn't do anything apart from creating the object. The object's variables remain uninitialized

It is the convention in Java to name a method that returns an instance variable  `getVariableName`. Such methods are often referred to as "getters".

if the method's only purpose is to set a value to an instance variable, then it's named as `setVariableName`. Value-setting methods are often called "setters".

Simply defining public getters and setters for a private field in a class is equivalent to making the field public without getters and setters. So, it’s always advisable to decide thoughtfully whether to define accessor methods for all the fields or not.

The method returning the string representation is always `toString` in Java.
```
Person foo = new Person();
System.out.println(foo);
// is the same as System.out.println(foo.toString());
```


**all executable code must reside within a class.** This means you cannot define a standalone function (sometimes called a "top-level function") directly in a Java source file without enclosing it within a class. However one could create [[static]] methods within a class
