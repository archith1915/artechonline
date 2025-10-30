---
{"dg-publish":true,"permalink":"/content-folders/dsa/javafordsa/collections/","title":"Collections in Java","tags":["dsa","java"]}
---

# Methods on collections

| Method                    | Description                                                                                | Return type |
| ------------------------- | ------------------------------------------------------------------------------------------ | ----------- |
| add(E e)                  | Add an element to the collection                                                           | boolean     |
| addAll(E e)               | Add all elements from one collection to another                                            | boolean     |
| remove(Object element)    | Remove an element from the collection                                                      | boolean     |
| removeAll(Collection C)   | Remove all the elements of the specified collection from the invoking collection           | boolean     |
| retainAll(Collection C)   | Delete all the elements of the invoking collection except that in the specified collection | boolean     |
| size()                    | Find the size of the collection (total number of elements)                                 | int         |
| clear()                   | Clear the collection                                                                       | void        |
| contains(Object element)  | To check if the collection contains the specified element                                  | boolean     |
| containsAll(Collection C) | To check if the invoking function contains all the elements in the specified collection    | boolean     |
| isEmpty()                 | To check if the collection is empty                                                        | boolean     |
| equals()                  | To match two collections                                                                   | boolean     |
| toArray()                 | Convert a collection into an array                                                         | Object\[]   |
# List Interface

A collection that stores a sequence of elements.

```java
List<DataType> var_name = new ListType <>();
```
## Types:

1. ArrayList
2. LinkedList
3. Vector

## Methods on List interface

| Method                    | Description                                                                             | Return type |
| ------------------------- | --------------------------------------------------------------------------------------- | ----------- |
| add(E e)                  | Add an element to the collection                                                        | boolean     |
| addAll(Collection C)      | Add all elements from one collection to another                                         | boolean     |
| remove(Object element)    | Remove an element from the collection                                                   | boolean     |
| size()                    | Find the size of the collection (total number of elements)                              | int         |
| clear()                   | Clear the collection                                                                    | void        |
| contains(Object element)  | To check if the collection contains the specified element                               | boolean     |
| containsAll(Collection C) | To check if the invoking function contains all the elements in the specified collection | boolean     |
| isEmpty()                 | To check if the collection is empty                                                     | boolean     |
| equals()                  | To match two collections                                                                | boolean     |
**Additional Methods:**

| Method                              | Description                                                             | Return type                                 |
| ----------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------- |
| get(int index)                      | Returns the element at the specified index                              | Object                                      |
| set(int index, E element)           | Add the element at the specified index                                  | E - previous element at the specified index |
| indexOf(Object o)                   | Get the index of the first occurrence specified element                 | int *or* -1 if not found                    |
| lastIndexOf(Object o)               | Get the index of the last occurrence of the specified element           | int *or* -1 if not found                    |
| subList(int fromIndex, int toIndex) | Returns a view of the portion of the list between the specified indices | List                                        |
# ArrayList

```java
ArrayList <DataType> al = new ArrayList <> ();
```
## Methods on ArrayList

| Method                          | Description                                                                                | Return type              |
| ------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------ |
| add(int index, Object element)  | Add an element to the collection at the specified index                                    | boolean                  |
| addAll(Collection C)            | Add all elements from one collection to another                                            | boolean                  |
| addAll(int index, Collection C) | Add all elements from one collection to another at the specified index                     | boolean                  |
| remove(Object element)          | Remove an element from the collection                                                      | boolean                  |
| size()                          | Find the size of the collection (total number of elements)                                 | int                      |
| clear()                         | Clear the collection                                                                       | void                     |
| clone()                         | Return a shallow copy of the ArrayList                                                     | List                     |
| retainAll(Collection C)         | Delete all the elements of the invoking collection except that in the specified collection | boolean                  |
| get(int index)                  | Return the element at the specified index                                                  | Object o                 |
| indexOf(Object o)               | Get the index of the first occurrence specified element                                    | int *or* -1 if not found |
| lastIndexOf(Object o)           | Get the index of the last occurrence of the specified element                              | int *or* -1 if not found |
| remove(int index)               | Remove the element at the specified index                                                  | boolean                  |
# LinkedList

```java
LinkedList <DataType> ll = new LinkedList <> ();
```
## Methods on LinkedList

| Method                         | Description                                                     | Return type                                |
| ------------------------------ | --------------------------------------------------------------- | ------------------------------------------ |
| add(int index, Object element) | Add an element to the collection at the specified index         | boolean                                    |
| add(Object element)            | Append the specified element to the list                        | boolean                                    |
| addAll(Collection C)           | Add all elements from one collection to another                 | boolean                                    |
| addFirst() *or* offerFirst()   | Add elements to the start of the list                           | boolean                                    |
| addLast() *or* offerLast()     | Add elements at the end of the list                             | boolean                                    |
| getFirst() *or* peekFirst()    | Obtain the first element in the list                            | Object                                     |
| getLast() *or* peekLast()      | Obtain the last element in the list                             | Object                                     |
| pollFirst() *or* removeFirst() | Remove the first element in the list                            | boolean                                    |
| pollLast() *or* removeLast()   | Remove the last element in the list                             | boolean                                    |
| removeFirstOccurence(Object o) | Remove the first occurrence of the specified object in the list | boolean                                    |
| removeLastOccurrence(Object o) | Remove the last occurrence of the specified object in the list  | boolean                                    |
| set(int index, E element)      | Set the element E at the specified index                        | Object - previously at the index specified |
| size()                         | To get the total number of elements in the list                 | int                                        |
| toArray()                      | To convert the list into an array                               | Object \[]                                 |
# Set interface

```java
Set <DataType> set1 = new Set <> ();
```

# HashSet

```java
HashSet <DataType> hashset1 = new HashSet (capacity, loadFactor);
```

> - Capacity: Number of elements the set will store.
> - Represents a value between 0.0 and 1.00 that determines when data will be moved to a new set (double size).

## LinkedHashSet

**Constructors of java LinkedHashSet**

1. HashSet() - Default
2. HashSet (Collection c) - Initialize hash set by using the elements of the collection c.
3. LinkedHashSet (int capacity) - Initialize the capacity of the linked set to the given integer value.
4. LinkedHashSet (int capacity, float fillRato) - Initialize both the capacity and the load factor.

**Methods on LinkedHashSet**

| Method                                  | Description                                                                          | Return Type          |
| --------------------------------------- | ------------------------------------------------------------------------------------ | -------------------- |
| add(E e)                                | Adds the specified element to the set if it’s not already present.                   | boolean              |
| addAll(Collection&lt;? extends E&gt; c) | Adds all elements from the specified collection to the set.                          | boolean              |
| clear()                                 | Removes all elements from the set.                                                   | void                 |
| contains(Object o)                      | Returns true if the set contains the specified element.                              | boolean              |
| containsAll(Collection&lt;?&gt; c)      | Returns true if the set contains all elements of the given collection.               | boolean              |
| isEmpty()                               | Returns true if the set contains no elements.                                        | boolean              |
| remove(Object o)                        | Removes the specified element from the set if it is present.                         | boolean              |
| removeAll(Collection c)                 | Removes all elements in the set that are contained in the specified collection.      | boolean              |
| retainAll(Collection c)                 | Keeps only elements in the set that are contained in the specified collection.       | boolean              |
| size()                                  | Returns the number of elements in the set.                                           | int                  |
| iterator()                              | Returns an iterator over the elements in the set.                                    | Iterator&lt;E&gt;    |
| toArray()                               | Returns an array containing all elements in the set.                                 | Object[]             |
| toArray(T[] a)                          | Returns an array containing all elements in the set, using the specified array type. | T[]                  |
| spliterator()                           | Creates a Spliterator for the set (used in parallel streams).                        | Spliterator&lt;E&gt; |
| equals(Object o)                        | Compares the set to another object for equality.                                     | boolean              |
| hashCode()                              | Returns the hash code for the set.                                                   | int                  |
# TreeSet

**Constructors of TreeSet**

1. TreeSet() - Default
2. TreeSet (Collection c) - Build a tree set that contains the elements of collection c.
3. TreeSet (SortedSet s) - Build a tree set that contains the elements of the sorted collection c.
# Map interface

## Types

1. HashMap
```java
HashMap <keyDataType, valueDataType> hm = new HashMap <> ();
```

2. LinkedHashMap
```java
LinkedHashMap <keyDataType, valueDataType> lhm = new LinkedHashMap <> ();
```

3. TreeMap
```java
TreeMap <keyDataType, valueDataType> tm = new TreeMap <> ();
```


**Methods on Maps**

| Method                  | Description                                                                 | Return Type         |
| ----------------------- | --------------------------------------------------------------------------- | ------------------- |
| put(key, value)         | Adds a key-value pair to the map or updates the value if the key exists     | V                   |
| get(key)                | Retrieves the value associated with the specified key                       | V                   |
| remove(key)             | Removes the mapping for the specified key                                   | V                   |
| containsKey(key)        | Checks if the map contains the specified key                                | boolean             |
| containsValue(value)    | Checks if the map contains the specified value                              | boolean             |
| keySet()                | Returns a set of all keys in the map                                        | Set                 |
| values()                | Returns a collection of all values in the map                               | Collection          |
| entrySet()              | Returns a set of key-value mappings                                         | Set<Map.Entry<K,V>> |
| size()                  | Returns the number of key-value mappings                                    | int                 |
| clear()                 | Removes all mappings from the map                                           | void                |
| putIfAbsent(key, value) | Adds a mapping only if the key is not already present                       | V                   |
| replace(key, value)     | Replaces the value for a given key if it exists                             | V                   |
| firstKey()              | Returns the first (lowest) key (TreeMap only)                               | K                   |
| lastKey()               | Returns the last (highest) key (TreeMap only)                               | K                   |
