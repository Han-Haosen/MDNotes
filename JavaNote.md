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

# Multithreading


single-processor shares CPU time

multithreading in multiple core allows you to do taskes simultaneously


It is done with task class that implmenet **Runnable interface**

all it contains is the run method

implement the **run method**  to tell how your threa is gonna run

for exampmle:
```
public class TaskClass implements Runnable{
    public TaskClass(){

    }

    public void run(){

    }
}
```
java.lang.Runnable
```
public class Client{
    public void someMethod(){
        TaskClass task = new TaskCalss();
        Thread thread = new Thread(task);
        thread.start();
    }
}
```

JVM execute the task by invoking task's run() method

A real example below:
```
public class TaskThreadDemo{

    public static void main(String[] args){
        Runnable printA = new PrintChar('a',100);
        Runnable printB = new PrintChar('b',100);
    }

    Thread thread1 = new Thread(printA);
    Thread thread2 = new Thread(printB);

    thread1.start();
    thread2.start();
}

class PrintChar implements Runnable{
    private char charToPrint;
    private int times;

    public PrintChar(char c, int t){
        charToPrint = c;
        times = t;
    }

    @Override
    public void run(){
        for (int i = 0;i< times;i++){
            System.out.print(charToPrint);
        }
    }
}
```

methods :

Thread()

Thread(task:Runnable)

start()

isAlive()

 setPriority(int) //set p ranging from 1 to 10

join() //waits for it to finish

sleep(milisecond:long): void

yield() // stop and allow other threads to execute

interrupt()


InterruptedException ex -- checked when interrupt() is called

join() method:

thread4.join();

print100 will stop since //if(i==50)thread4.join()

it will wait until it is finished

There is also

MIN/MAX/NORM_PRIORITY, 1,10,5

main thread is max

picks currently runnable thread with highest priority

round-robin scheduling

Lambda version of the demonstration:

```
new Thread(()->{
    try{
        while(true)[
            if(lblText.getText().trim().length==0)text="welcome";
            else text = ""
        ]
        Platform.runLater(()-> lblText.setText(text));
        Thread.sleep(200);
    }
    catch(interruptedE){

    }
}).start();
```

Using threadpools

Executor interface for executing tasks in a thread pool and the ExecutorService interface for managing and controlling tasks.

java.util.concurrent.Executor

+execute(Runnable object) executes the task

ExecutorService

shutdown()/shutdownnow() returns List<Runnable>

isShutdown():boolean/isTerminated():booloean


newFixedThreadPoll(int) creates a fixed number of threads in a pool

if completes, reused to execute another task

if terminates new thread will be created



eg.

```
import java.util.concurrent.*;

public class ExecutorDemo{
    public static void main(String[] args){
        ExecutorServicec executor = Executors.newFixedThreadPool(3);

        executor.execute(new PrintChar(a,100));
        executor.execute(new PrintChar(b,100));

        executor.shutdown();//no new tasks and existed will continue to execute
    }
}

```

## thread synchronization

avoid race conditions

prevent more than one thread from simultanenously entering a part of the program

**synchronized** keyword to synchronize the method so only one thread can access it at a time

e.g

`public synchronized void deposit(double amount);`

such methods acquare lock before executes

instance method, lock is on object

static method, lock is on class
```
synchronized(account){
    account.deposit(1);
}
```

lock is an instance of the Lock interface, which


java.util.concurrent.locks.Lock
```
+lock(): void //acquire
+unlock(): void //release
+newCondition(): Condition// return new Condition instance that is bound to lock instance
```

ReentrantLock is a concrete implementation of Lock for creating mutually exclusive
locks.

in static main:

```
ExecutorService executor = Executors.newCachedThreadPool();

for(100){
  executor.execute(new AddAPennyTask());
}

executor.shutdown();

while(!executor.isTerminated()){
}

System.out.println(account.getBalance)


public static class AddAPennyTask implements Runnable{
  public void run(){
    account.deposit(1);
  }
}

public static class Account{
  private static Lock lock = new ReentrantLock();
  private int balance = 0;

  public int getBalance() {
    return balance;
  }

  public void deposit(int amount){
    lock.lock();
    try{
      int newBalance = balance + amount;
      Thread.sleep(5);
      balance = newBalance;
    }
    catch(InterruptedException e){}
    finally{
      lock.unlock();
    }
  }
}
```


## Cooperation between threads

Conditions are objects created by invoking the
newCondition() method on a Lock object.

Once a condition is created, you can use its
await(), signal(), and signalAll() methods for thread communications

The await() method causes the current thread to wait until the condition is
signaled.

The signal() method wakes up one waiting thread, and the signalAll() method
wakes all waiting threads.
