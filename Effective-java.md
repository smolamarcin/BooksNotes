## Chapter 4

### Minimize the access of classes and members. A well designed component hides all implementations details. 

We should make class as inaccessible as possible, trying to not expose whole implementations details.
Only api should be public. Try to return defensive copies on accessors methods, not the reference itself (to final fields too).
Public static fields should be final and immutable. Classes should not have public fields.

If you can't avoid public fields, acces them through setters/getters and make fields private.
