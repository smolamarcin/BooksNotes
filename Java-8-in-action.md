Hello!
## Method references
Methods references are easy lambda expressions for already existing methods (methods which already has a name).

| Tables        | Are           |
| ------------- |:-------------:|
| Reference to a static method     | ContainingClass::staticMethodName |
| Reference to an instance method of a particular object      | containingObject::instanceMethodName      |
| Reference to an instance method of an arbitrary object of a particular type | ContainingType::methodName    |
| Reference to a constructor | ClassName::new      |
## Streams
Stream - sequence of elements from a source that support data process operations.

### Streams vs Collections

A collection is an in-memory structure that holds all the values structure currently has ( every element of the collection is stored in memory).

Streams are fixed data structure (we can't add or remove items from the stream) whose elements are computed on demand.
Streams are lazily constructed collection: values are computed when they're solicited by user(just-in-time).
Streams can be traversed only once (after that streams are consumed). If we try to traverse it again, we're getting an exception.
Streams are using internal iteration - streams are do iteration for me.
Collections are eagerly constructed. 
Collections are using external iteration - eg using for-each.

### Streams operations

There are two categories of operations:
- intermediate operations - return another stream. This allows to connect operations. Intermediate operations are not executed until 
terminal operation is invoked on stream (lazy nature of streams). 
> map, filter, sorted, limit, distinct
- terminal operations - produces a results from a stream (any no stream value - even void)
> forEach, count, collect, 

### Reduce
Reduce takes 2 arguments
> initial value
> BinaryOperator<T> to combine two elements and return new value
  
There is overloaded version of reduce, without initial value. It returns an Optional.

Finding max integer using reduce: (without init value it returns optional).
Optional<Integer> reduce = integers.stream().reduce((a, b) -> Integer.max(a, b));
  
### Collectors

Implementations of Collector that implement various useful reduction operations, such as accumulating elements into collections, summarizing elements according to various criteria, etc. 

// Accumulate names into a List
     List<String> list = people.stream().map(Person::getName).collect(Collectors.toList());

     // Accumulate names into a TreeSet
     Set<String> set = people.stream().map(Person::getName).collect(Collectors.toCollection(TreeSet::new));

     // Convert elements to strings and concatenate them, separated by commas
     String joined = things.stream()
                           .map(Object::toString)
                           .collect(Collectors.joining(", "));

     // Compute sum of salaries of employee
     int total = employees.stream()
                          .collect(Collectors.summingInt(Employee::getSalary)));

     // Group employees by department
     Map<Department, List<Employee>> byDept
         = employees.stream()
                    .collect(Collectors.groupingBy(Employee::getDepartment));

     // Compute sum of salaries by department
     Map<Department, Integer> totalByDept
         = employees.stream()
                    .collect(Collectors.groupingBy(Employee::getDepartment,
                                                   Collectors.summingInt(Employee::getSalary)));

     // Partition students into passing and failing
     Map<Boolean, List<Student>> passingFailing =
         students.stream()
                 .collect(Collectors.partitioningBy(s -> s.getGrade() >= PASS_THRESHOLD));
