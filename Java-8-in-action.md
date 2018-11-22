Hello!

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
