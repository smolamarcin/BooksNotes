### Collections hierarchy

Source: www.falkhausen.de

![alt text][logo]

[logo]: http://www.falkhausen.de/Java-8/java.util/Collection-Hierarchy.png "Logo Title Text 2"

### BigO in basic Collections
# List:
# ArrayList:
* add - O(1), just add at last array index
* add(index, element) - O(n), first move items to the right, then add item to specific index
* get - always O(1)
* remove - O(n) - we need to iterate to specific index
* remove (index) - O(n) - we need to delete object at index, and then copy the rest of array
* indexOf - O(n)
* contains - O(n)

# LinkedList
* add - O(1) - just change the indices, this operation does not include iterating, just adding
* get - O(n)
* remove - O(1) - just change the references to the nodes, does not include iterating, just removing
* contains - O(n)

# CopyOnWriteArrayList
* add - O(n)
* get - O(1)
* contains - O(n)


# Set
HashSet: Adding: O(1) | Deleting O(1) | Searching O(n)
TreeSet: Adding: O(logn) | Deleting: O(1) | Searching O(logn)
LinkedHashSet
EnumSet
ConcurentSkipListSet
CopyOnWriteArraySet


#Queue
PriorityQueue
DelayQueue
ArrayDequeue

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

### HashSet vs TreeSet

1. Ordering : HashSet stores the object in random order . There is no guarantee that the element we  inserted first in the HashSet  will be printed first in the output . 

Elements are sorted according to the natural ordering of its elements in TreeSet. If the objects can not
be sorted in natural order than use compareTo() method to sort the elements of TreeSet object.

2. Null value :   HashSet can store null object while TreeSet does not allow null object. If one try to store null object in TreeSet object , it will throw Null Pointer Exception.

3. Performance : HashSet take constant time performance for the basic operations like add, remove contains and  size.While TreeSet guarantees log(n) time cost for the basic operations (add,remove,contains).

4. Speed : HashSet is much faster than TreeSet,as performance time of HashSet is constant against the log time of TreeSet for most operations (add,remove ,contains and size) . Iteration performance of HashSet mainly depends on the load factor and initial capacity parameters.

5. Internal implementation :  As we have already discussed How hashset internally works in java thus, in one line HashSet are internally backed by hashmap. While TreeSet is backed by a  Navigable  TreeMap. 

### How Hashmap works?
https://javarevisited.blogspot.com/2011/02/how-hashmap-works-in-java.html


### Contranct equals hashcode
If two objects are equal according to the equals(Object) method, then calling the hashCode method on each of the two objects must produce the same integer result.


### HashMap vs TreeMap vs LinkedHashMap


    HashMap:
        Order not maintains
        Allow one null key and multiplie null values
        One value per one key

    LinkedHashMap:
        LinkedHashMap insertion order will be maintained
        Slower than HashMap and faster than TreeMap
        If you want to maintain an insertion order use this.

    TreeMap:
        TreeMap is a tree-based mapping
        TreeMap will follow the natural ordering of key (compareTo or provided Comparator)
        Use TreeMap when you need to maintain natural(default) ordering

