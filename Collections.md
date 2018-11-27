### ArrayList vs LinkedList

Difference between ArrayList and LinkedList in Java

1. Implementation :  ArrayList is the resizable array implementation of list interface , while LinkedList is the Doubly-linked list implementation of the list interface.

2. Performance  :  Performance of ArrayList and LinkedList depends on the type of operation

a. get(int index) or search operation :  ArrayList get(int index) operation runs in constant time i.e O(1)  while LinkedList get(int index) operation run time is O(n) .

The reason behind ArrayList being faster than LinkedList is that ArrayList uses index based system for its elements as it internally uses array data structure , on the other hand ,
LinkedList does not provide index based access for its elements as it iterates either from the beginning or end (whichever is closer) to retrieve the node at the specified element index.

b. insert() or add(Object) operation :  Insertions in LinkedList are generally fast as compare to ArrayList.

In LinkedList adding or insertion is O(1) operation . While in ArrayList, if array is full i.e worst case,  there is extra cost of  resizing array and copying elements to the new array , which makes runtime of add operation in ArrayList O(n) , otherwise it is O(1) .

c. remove(int) operation :  Remove operation in LinkedList is generally same as ArrayList i.e. O(n).
In LinkedList , there are two overloaded remove methods. one is remove() without any parameter which removes the head of the list and runs in constant time O(1) .
The other overloaded remove method in LinkedList is remove(int) or remove(Object) which removes the Object or int passed as parameter . This method traverses the LinkedList until it found the Object and unlink it from the original list . Hence this method run time is O(n).

While in ArrayList remove(int) method involves copying elements from old array to new updated array , hence its run time is O(n).

3.  Reverse  Iterator :  LinkedList can be iterated in reverse direction using descendingIterator() while there is no descendingIterator() in ArrayList , so we need to write our own code to iterate over the ArrayList in reverse direction.

4. Initial Capacity :  If the constructor  is not overloaded , then ArrayList creates an empty list of initial capacity 10 , while LinkedList  only constructs the empty list without any initial capacity.

5. Memory Overhead :  Memory overhead in LinkedList is more as compared to ArrayList as node in LinkedList needs to maintain the addresses of next and previous node. While in ArrayList  each index only holds the actual object(data).
