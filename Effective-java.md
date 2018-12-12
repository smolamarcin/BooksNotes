## Chapter 4

### Minimize the access of classes and members. A well designed component hides all implementations details. 

We should make class as inaccessible as possible, trying to not expose whole implementations details.
Only api should be public. Try to return defensive copies on accessors methods, not the reference itself (to final fields too).
Public static fields should be final and immutable. Classes should not have public fields.

If you can't avoid public fields, acces them through setters/getters and make fields private.

* Do not provide methods that modify the object's state (mutators)
* Ensure the class can't be extended.
* Make all fields final.
* Make all fields private
* Ensure exclusive access to any mutable components - ensure that clients of the class cannot obtain references do that objects -> Make defensive copises (in constructors, accessors).

### Favor composition over inheritance.

Inheritance violates encapsulation. It it appropriate only when a genuine subtype relationship exists between the subclass and the superclass (is every A is B?. Class B should extends class A only if an "is-a" relationship exists between the two classes). Even then, inheritance may lead to fragility.



