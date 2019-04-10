# Jpa by Jakub Kubryński (https://www.youtube.com/watch?v=UPWkpl5PL_w)

1. It's not neccessary to call save method, when object is updated. Hibernate has dirty checking mechanism, so it will update Enttity state in database.
Hibernate manages this entity ( entity is in persistence context ).

2. Annotations on fields vs annotations on getters.
It should be consistent. Joining anootations on fields and getters is not turned on by default ( we need to enable it ).

3. @Access - allowing to putting annotations of fields and getters. We can join them.

4. Entity name - Order - conflict, because this is a keyword. When we change entity name (@Entity(name="orders"). We neet to change HQL query:

From: 
> em.createQuery("Select o from Order o")

To:
> em.createQuery("Select o from orders o")

Better way is to use @Table annotation.

So, instead of:
> @Entity(name="orders")
class Order {}

Better way:
> @Entity
@Table(name="orders") --> define table name
class Order {}

5. @OneToOne

