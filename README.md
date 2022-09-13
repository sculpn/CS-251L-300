# CS-251L-300
CS-251L-300 Intermediate Programming

CS 251
Intermediate Programming in Java
Programming Assignment 1
due by end-of-day Tuesday, September 13, 2022
In class we studied how an ArrayList<E> is implemented by creating an underlying
array (e.g., [ ] ) and storing the data in that array. The set, get, add, remove, etc. methods
were implemented by manipulating the data in the underlying array. Note that the
ArrayList<E> is a generic class. The type of data stored in the array can be any kind of
Object. The type-parameter E is a placeholder for the actual type of data to be stored in
the data structure (e.g., String, or Car, or BankAccount).
For this assignment you must implement a generic FIFO Queue. This data structure
(aka Collection) represents a “waiting line”, such as a line at the grocery store. People
join the line at the end (no cutting in line!) and the person at the front of the line is the
one to leave the line and get service. A FIFO Queue is “first in, first out”. This data
structure is much more limited than a general List, such as ArrayList or LinkedList.
For this assignment you must write a class called FloatingQueue<T>. You must
implement the following operations specified in the given LucasQueue<T> interface.
This is a subset of the operations specified in the Queue<T> interface in the Java API,
which is part of the Java Collections Framework.
FloatingQueue() Constructor method that will allocate memory for an array of size 5.
FloatingQueue(n) Constructor method that will allocate memory for an array of size
maximum(5,n)
offer (newData) Add the parameter value to the end of the Queue. If the array does
not have any more capacity, then create a new array with twice as
much room. It is illegal for the added value to be the null pointer
poll() Remove the data from the head (or front) of the Queue, and return
that object. Return null, if the Queue is empty. If the size of the
Queue falls below 25% of capacity, then reallocate an array that is
half the size of the current array (so memory is not wasted), but do
not allow the array to have fewer than 5 slots.
peek() Return the data from the head (or front) of the Queue. Return null, if
the Queue is empty
size() Return the number of items currently in the Queue
isEmpty() Return true if-and-only-if the Queue has no elements in it.
clear() The Queue should be empty after this operation is performed, and
the allocated memory for the Queue should be the minimum value
(.e., 5)
toString() Return a String representing the current contents of the Queue, listed
from left-to-right in the same order as the front-to-rear of the Queue.
For example, the String might be: “[alice,bob,chad]”
You must implement these methods directly, without using any built-in Collection
classes.
Your FloatingQueue class will be generic. So, your class definition will be similar to
that shown below.
public class FloatingQueue<T> implements LucasQueue<T>
{
private T[] theData; // The underlying data array
public FloatingQueue( int initialCapacity ) {
.....
theData = (T[]) new Object[ initialCapacity ];
....
}
}
The FloatingQueue class contains an array to hold the data in the queue. You must not
use an ArrayList, or any other class to store these elements. The point of this exercise is
to directly manipulate the array.
The constructor methods for the FloatingQueue class allocate memory for the underlying
array, and use casting. The following, seemingly more direct, code will not compile:
theData = new T[ initialCapacity ];
Your FloatingQueue class must also have a default (aka “no parameter”) constructor that
initializes the size of the underlying array to be five (5).
As with any data structure, there are many different ways you can go about storing
the data and implementing the operations. One possibility is to use a “left justified”
array. The following example illustrates how the contents of the array change as data is
inserted and deleted, assuming that the array is initially empty and has length five. Every
poll() operation causes all the data in the array to shift one position to the left. This is a
costly, O(n) time operation.
