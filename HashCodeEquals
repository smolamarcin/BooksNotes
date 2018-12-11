### When you are writing equals() method, which other method or methods you need to override?

Hashcode. When you overriding equals, you should override hashcode too, otherwise you break the contract between hashcode and equals.

### Can two objects which are not equal have the same hashCode?

Yes

### Where have you written equals() and hashCode in your project?

Value objects. Domain objects. Hibernate enties.

### Suppose your Class has an Id field, should you include in equals()? Why?

Including this field is not a good idea in, because this method should check equality based upon content and business rules. Also including id, which is mostly a database identifier and not available to transient object until they are saved into the database.

### What happens if equals() is not consistent with compareTo() method?

 If compareTo() is not consistent means doesn't return zero, if equals() method returns true, it may break Set contract, which is not to avoid any duplicates.
 For example, when putting object in the treeMap can work wrong.





