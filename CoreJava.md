### Overloading rules

Two methods will be treated as overloaded if both follow the mandatory rules below:

* Both must have the same method name.
* Both must have different argument lists.

And if both methods follow the above mandatory rules, then they may or may not:

* Have different return types.
* Have different access modifiers.
* Throw different checked or unchecked exceptions.

### Overriding rules

With respect to the method it overrides, the overriding method must follow following mandatory rules:

* It must have the same method name.
* It must have the same arguments.
* It must have the same return type. From Java 5 onward, the return type can also be a subclass (subclasses are a covariant type to their parents).
* It must not have a more restrictive access modifier (if parent --> protected then child --> private is not allowed).
* It must not throw new or broader checked exceptions.

And if both overriding methods follow the above mandatory rules, then they:

* May have a less restrictive access modifier (if parent --> protected then child --> public is allowed).
* May throw fewer or narrower checked exceptions or any unchecked exception.

Apart from the above rules, there are also some facts to keep in mind:

* Only inherited methods can be overridden. That means methods can be overridden only in child classes.
* Constructors and private methods are not inherited, so they cannot be overridden.
* Abstract methods must be overridden by the first concrete (non-abstract) subclass.
* final methods cannot be overridden.
* A subclass can use super.overridden_method() to call the superclass version of an overridden method.

### Can static method be overloaded? What is hiding? What will happen if extending class will define the non-static method with the same name?

Static methods can be overloaded. 
Method hiding may happen in any hierarchy structure in java. When a child class defines a static method with the same signature as a static method in the parent class, then the child’s method hides the one in the parent class.
You can't create method in child class with the same name and same parameters in child class, when method in parrent class is static.
It's possible to do that, if parameters are different. 
