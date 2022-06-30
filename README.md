# What is a Thread?

## Learning Goals

- Explain the differences between a program, process, and thread.
- Understand information sharing between processes and threads.

## Introduction

In order to understand concurrency and multithreading we have to first
understand some basic terms. We’ll look at the following terms:

- Program
- Process
- Thread

A program is a collection of instructions and data to perform specialized tasks.
For example, Firefox is a program for browsing the internet. Programs run in
their own environments called processes.

A process is an environment that allocates the necessary system resources to run
the instructions in the program. A process can run multiple threads to carry out
the instructions.

A thread is the simplest unit of execution that runs instructions. It runs the
instruction in the given order.

## Information Access

As mentioned earlier, a process creates an environment with allocated system
resources. Multiple processes can run in a system but they don’t share resources
among them.

Threads within the same process can share resources among them since they all
have access to the process/global variables. Threads also have local memory for
storing temporary data when running instructions.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a079aa4-c5dd-4ca0-9490-c82701b99e7a/Untitled.png)

## Thread Example

Let’s briefly look at how we can use a thread in Java. We’ll explain the syntax
in detail in later lessons and expand on this example.

```java
class Counter {
    private int count = 0;

    public void increment() {
        count++;
    }

    public int getValue() {
        return count;
    }
}

class Example {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();

        Thread thread = new Thread(new Runnable() {
            @Override
            public void run() {
                for (int i = 0; i < 100; i++) {
                    counter.increment();
                }
            }
        });

        thread.start();
        thread.join();

        System.out.println(counter.getValue());
    }
}
```

## Conclusion

You’ve learned about programs, processes, and threads. Once we take a deeper
dive into threads, you’ll be able to handle multiple threads in your program!
