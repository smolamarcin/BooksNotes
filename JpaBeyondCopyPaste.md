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

@Entity
class Customer{
@OneToOne
Address address;
}

@Entity
class Address{
@OneToOne
Customer customer;
}

Above example is wrong. Because this relationship does not have 'owner', so Hibernate will create two foreign keys.
We need to use mappedBy on one of the side, eg.

@Entity
class Address{
  @OneToOne(mappedBy="customer")
  Customer customer;
}

6. @OneToMany and @ManyToMany
Issues: 
> Intermediate table -> Hibernate will create it.
> 2 Intermediate tables for @ManyToMany
    
Solution:
> mappedBy
7. Lazy loading - element is loaded only when required.
Hibernate provides custom implementations for collections in mappings:
* Set -> PersistentSet
No order, no duplicates. The best performance in application, because we need just check if object exists. One update.
* List -> PersistentBag - worst than a Set. Allows duplicates, No order (in PersistentBag, impelemntation of 'Java list' in Hibernate).
* PersistentList - on field we need to use @OrderColumn annotation. Additional column with order informations. Update entity -> Inser + update order informations column. 

8. N+1 selects 
We have lazdy loaded List of Addresses in Person Entity.

@Entity
class Person{
  @OneToMany
  Set<Address> addresses;
}
  
Then, we need to print all addresses of every person, so we need to get all persons:

> List<Person> personList = session.createQuery("FROM Person p").list(); 
  
Then, get addresses for every person and print them.
for (Person person : personList) {
  sout(person);
  System.out.println("----- UMOWY -----");
  for (Address address : person.getAddresses()) {
   sout(address);
  }
 }
 
 We have one query for getting list of person (addresses are not loaded, because of lazy loading).
 Then, for every person we have one query, so for N person, we have N queries.
 
 Summary we have N+1 queries.

9. N+1 solutions:

9.1 @BatchSize(size = 10) -> work around, but it generally works ('(n/10) + 1'. Hibernate will load next 10 addresses (In order. So, eg. for filtering it's not good).

9.2 Using joins
> SELECT DISTINCT p from Person p JOIN fetch p.addresses

10. Saving in hibernate: merge vs persist
> void persist(Object object) - save entity. Works for new entities. Does not have to check if entiy exists. After return from this method, entity is managed (so, after calling setter on this entity, hibernate will auto-update entity in database using dirty checking mechanism)

> T merge(T object); - save entity, and also save some old entity(deserialized? I'm not sure about it.). Need to check if entity exists. After returning, entity (object) is 'no entity'. SO when  entity (object) is passed to merge method, it will be copied, save and copy will be returned. So copy is entity, not the passed object.
So, better choice is persist (because performance, does not need to check if entity exists (another select))
Merge only when entity is deatached (eg it's returned from another layer) and we need to save it. 
