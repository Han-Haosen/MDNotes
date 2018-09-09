## Java notes 

Covers data strctures in Java programming 



# Data Structure 

1.ArrayList

2.LinkedList

3.Vector

4.Stack

5.Queue

Good: 

ArrayList and Vector are fast, memory coherent provide initial size

can be time consuming to add elements in the middle 

Use internal arrays for storage meaning random access is fast 

Bad: 

May waste space/need to be resized/slower when deleting

## Linkedlist:

Insert/Delete quick

Bad: Read sequentially not stored sequentially so random access is not efficient 

## Collections Interface 

Set/List/Queue

Set-- TreeSet/SortedSet/HashSet

List-- Vector(Stack)/ArrayList/Linkedlist

Queue-- PQ/Deque


## Collections Class& Interface

method throws Nullpointerexception if object full

Queue First in first out 

List -- Ordered 

Set-- not duplicate

toArray() returns an array

Arrays.toList()

## Iterable interface 

hide detail of how data is stored 

iterator() and foreach()

iterator() returns an iterator object

hasNext(), next(), remove()

ListIterator-- adds functionality to traverse list backward


Iterator iterator = collection.iterator();

## ArrayList 

implements List interface 

can contain null

can have duplicate 

not inherently thread safe

trimTo()

## LinkedList 

added in Java 7

included in the API

access is linear

doubly linked list to manage

last item points to null 

addfirst()

getLast()

ListIterator iterator = states.listIterator(states.size());

iterator.hasPrevious()

## Vector 

similar to ArrayList -- automatic synchronization/bad performance

most use ArrayList

## stack 

Last in first out 

use push() to add

use pop() to remove

use peek() to make a copy of first item 

foreach i in s
    stack.push(i);

while not empty:
    print(stack.pop());

to reverse a list 

## Queue

Linear list where itmes are adde to one and deleted from the other

waiting in line -- FIFO

add()/peek()/remove()/poll()

remove top error if empty

poll remove from top, return null if empty 

Queue<integer> queue = new LinkedList<>();

int removed = queue.remove();

addAll() for arraylist 






# Generics 

define generic classes etc 


package java.lang

```
public interface Comparable<T>{
    public int compareTo(T o)
}
```

Case Study 1 

Sorting Array of Objects

generic method for an array of Comparable objects 

