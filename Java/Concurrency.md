# Thread class
> java.lang.Thread

A thread is a line of execution with properties such as: priority, id and daemon. The JVM is responsible of creating an identifier and map all alive threads.

```java
Thread thread = Thread.currentThread(); // the current thread
```

# Runnable interface
> java.lang.Runnable

Extend thread class is inconvenient because Java has a single inheritance limit.

## Implementing a thread
You can implement a thread by either extending the Thread class or implementing the Runnable interface. In both cases you need to override its `run` method.

```java
class HelloRunnable implements Runnable {
	
    @Override
    public void run() {
        String threadName = Thread.currentThread().getName();
        String helloMsg = String.format("Hello, I'm %s", threadName);
        System.out.println(helloMsg);
    }
}
```

## Daemon mode
`daemon` property indicates that the current thread is a non essential part of the program, or either it is a very small part that does not require a lot of resources.

JVM will not terminate a program if it still has any `non-daemon` thread running.

## Shared data

### volatile keyword
This declaration makes the operations of a certain variable atomic. This state allows multiple threads to work with the same reference without overlapping or losing data. `volatile` is used for visibility between threads.

This keyword is commonly used in `long` and `double` references. (As a rule, data types of more than 64 bits).