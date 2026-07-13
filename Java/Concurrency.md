# Thread class
> java.lang.Thread

A thread is a line of execution with properties such as: priority, id and daemon.

```java
Thread thread = Thread.currentThread(); // the current thread
```

The JVM is responsible of creating an identifier and map all alive threads.

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