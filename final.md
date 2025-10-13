#java 

In [[java]], final is a non-[[access modifier]] that can be applied to [[class]]es, methods, and variables. Its primary purpose is to make an entity immutable or to prevent it from being overridden or inherited.

A `final` variable can only be initialized once. 

**Reference `final` variables:** The reference itself cannot be changed to point to a different object. However, the _state_ of the object that the reference points to _can_ be modified if the object itself is mutable.

A `final` variable that is not initialized at the time of declaration is called a blank `final` variable. It can be initialized only once,

A `final` method cannot be overridden by subclasses.

A `final` class cannot be inherited.