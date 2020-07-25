---
title: "multi-threading"
tags: ""
---
process

> a program running on the compter  
> programs have memory isolation as such, they do not share data with each other.

thread

> a lightweight process. an isolated sub-task  
> which is a side sequential flow of execution beside a program.

-   multi-threading is a means to implement cocurrency. program performs tasks simultaneously.  
    this can be real concurrency or simulated concurrency by splitting time between threads.

-   processes don't share memory with each other.  
    data fields withing a thread can be accessed by their inner-threads. inner-threads share data with each other.  

-   every program has a **main thread** for its main method. OS distributes time between threads.

applications of multi-threading

-   I/O: loading a large file in background
-   networking: waiting for another machine to connect
-   parallelized algorithms: like merge-sort
-   event-handling loops: handled by java

* * *

### states of a thread

-   new: thread object creation, with constructor.
-   running: executing commands
-   waiting: halts execution until it is notified to continue by another thread
-   timed waiting: halts execution for a specified time
-   terminated: task completed
-   blocked: entering a **synchronized** statement / busy doing a long task ( File I/O request )

![](thread-life-cycle.JPG)

### Thread creation

```java
public class ExtThread extends thread //thread itself implements the runnable class
public class ImplThread implements runnable
{
	public []Thread(){//constructor
    
    }	
    public []Thread(String name){//constructor
    	super(name)
    }    
	@Override
   	public void run(){//thread commands
	}
}

ExtThread thread = new ExtThread();
Thread thread = new thread( new ImplThread(), String name); //argument must implement the runnable class
```

### runnable and other methods during execution

```java
thread.start();	// add thread to OS, executes along main thread.
thred.run();	// main thread executes the code, do not use this.

**"in upper thread"
	innerThread.join(); //wait for this thread to finish and then continue
	innerThread.join(t);//wait for a maximum of t for the thread to finish	
    innerThread.interrupt();//interrupt the thread
	//if interrupt is called during sleep, the exception is thrown
	
	
**"inside the thread itself"
	Thread.sleep(t) throws InterruptedException// put the thread to sleep for t ms
	if(Thread.interrupted()); //check whether current thread is interrupted or not
    
**"typically used in other class methods"
	Thread.getCurrentThread();	//get the thread that is executing this code
	thread.getName();			//get the name of the thread 
```

### waiting

```java
wait(t);	// release the objects lock and wait until notified

notify();	// a single waiting thread chosen at random
notifyAll();// all threads waiting on this object are notified, compete for lock if required

"wrong proposal": synchronized method for updating, unsynchronized methods for just accessing.
    		lock object when updating takes place. imagine it like a database.
			'wrong': because fields can be changed during accessing		
    
"note": the wait, sleep, notify and notify all methods are methods of the Object class.
		it may be best to call them using this.wait(), this.notifyAll(), ... .

these methods are used in Producer/Consumer Relationship architecture patters.
see concurrent collections below
```

### timed waiting

```java
thread.wait(t);	// release the objects lock and wait for t ms (minimum?)
thread.sleep(t);// put to sleep for t ms, keeps lock of objects so other threads cannot access it

thread returns to runnable when
1. interval expires
2. the notify or notifyAll methods are called

"note": methods sleep and wait, check and throw an InterruptedException
		which is nothing more than a boolean field in the Thread class.
        thus, "self-interruption" is also possible - like maybe in catch.

```

### terminated

-   thread finished executing the run method

### blocked

-   enter locked state when:  
    -   issue I/O request
    -   enter locked synchronized statement

-   return to runnable when:
    -   I/O completes
    -   previous thread finished and frees the lock, this thread acquires the lock now and beings statements
    -   interrupted

* * *

### ThreadPool and executorService

-   an **ExecutorService** object executes runnables  
    by managing a group of threads called a thread pool

-   manual creation and execution of threads can be detrimental.  
    an ExecutorService optmizes processor and resource use  
    and eliminates overhead of creating new threads by reusing existing threads.

```java
import java.util.concurrent

ExecutorService executorService = Executors.newCachedThreadPool

executorService.'execute(runnable)' //put the thread in line to execute
executorService.'shutdown()' //don't accept more threads, close service once all threads terminate
//if this method is not called, the service will be open for 60 seconds, waiting for new threads
//the main thread directly continues after this line

boolean tasksEnded = executorService.'awaitTermination(t)';
//wait for a maximum of t ms for the threads to finish, calling thread is blocked.
//return whether all tasks were finished or if timeout was reached
```

* * *

### Thread synchronization

-   a means to prevent threads from simultaneously using the same data  

-   every object has a lock.  
    for a thread to access the **synchronized methods** of an object it must acquire it's lock.  

-   once the object is locked, all other synchronized methods become locked and cannot be accessed.  
    the thread waits for the lock to be released and then executes the code.  

-   non-synchronized methods can be accessed at any time

-   this solution ensures mutual exclusion on working threads.  
    problems like simultaneous update and simultaneous read & update are solved.

-   static synchronized methods do not block synchronized instance methods

```java
// synchronized method: uses "this" object's lock
public synchronized type methodName (){
	statement(s)
}

// synchronized static method: uses the given class 's lock
public static synchronized type methodName (){
	statement(s)
}

// synchronized block: uses the "given object's" lock
synchronized (object){
	statement(s)
}

"note": //for different objects, synchronized non-static methods can be accessed
"note": //the last one can be used when only part of a method needs to be synchronized,
		//also an object is passed, "that" object and its methods become locked
"note": instead of sleep(), use wait() in synchronized blocks so other threads can execute.
```

* * *

### Producer Consumer Relationship

three elements:  

1.  Producer: generates data and stores it in a shared object
2.  Consumer: reads data from the shared object and operates on it
3.  SharedObject: a means to make threads wait depending on certain conditions.  
    allows data product entry/exit when available,  
    blocks threads and puts them on hiatus when it is not available

shared objects are usually one of the concurrent collections below: 
![](concurrent-collections1.JPG)
![](concurrent-collections2.JPG)

* * *

### SwingWorker: MultiThreading with GUI's

best to extend this class for multi-threading in GUI's

```java
public class BackgroundWorker extends SwingWorker<T1, T2 >{
	//T1 is the return type
    //T2 is the intermediate results type    
	@Override
    public T1 doInBackground() {
        //Defines a long computation and is called in a worker thread.
    }
    @Override
	protected void done() {
		//Executes on the event dispatch thread when doInBackground returns.
    }    
    @Override
    protected void process(List<T2> publishedVals)
   {
		//Receives intermediate results from the publish method and processes
		//these results on the event dispatch thread.
   } 
    
    typically not overriden methods
    these methods are usually used in other methods
    
    get: Waits for the computation to complete, then returns the result of the computati
    execute: Schedules the SwingWorker object to be executed in a worker thread.
    setProgress: Sets the "progress property" and notify any "propertyChange Listeners" on the
				 event dispatch thread of progress bar updates.
    publish: Sends intermediate results from the doInBackground method to the "process method"
        	 for processing on the event dispatch thread.
     
}

overriden methods can alter GUI views
```

other methods used in methods of extending class

```java
isCancelled()	//check the cancelled property
catching exceptions
```

methods used in calling thread

```java
SwingWorker.'execute()'//begin the background task
SwingWorker.'addPropertyChangeListener()'//called after setProgress is executed in background thread
SwingWorker.cancel(true);//set cancel propert to true
```

* * *

JAVA.Security.SecureRandom

-   exactly like the Random Class
