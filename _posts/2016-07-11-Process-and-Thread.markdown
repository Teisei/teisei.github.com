---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Process and Thread
categories: Java
---

## Process and Thread

### References

[1] [http://stackoverflow.com/questions/200469/what-is-the-difference-between-a-process-and-a-thread][ln1]

[2] [http://www.programmerinterview.com/index.php/operating-systems/thread-vs-process/][ln2]

[3] [https://en.wikipedia.org/wiki/Inter-process_communication][ln3]

[4] [https://en.wikipedia.org/wiki/Process_state][ln4]

[5] [http://web.stanford.edu/class/cs140/cgi-bin/lecture.php?topic=process][ln5]

[ln1]:	http://stackoverflow.com/questions/200469/what-is-the-difference-between-a-process-and-a-thread
	
[ln2]:	http://www.programmerinterview.com/index.php/operating-systems/thread-vs-process/

[ln3]:	https://en.wikipedia.org/wiki/Inter-process_communication

[ln4]:	https://en.wikipedia.org/wiki/Process_state

[ln5]:	http://web.stanford.edu/class/cs140/cgi-bin/lecture.php?topic=process

### Process

Each process provides the resources needed to execute a program. It consists of resource grouping and execution.

#### What is inside a process?

OS uses a process control block to keep track of each process:
Execution state for each thread (saved registers, etc.)
Scheduling information
Memory used by this process
Information about open files
Accounting and other miscellaneous information

#### Inter process communication

Signal: signal processor
Semaphore: P、V operation
Message queue:
Shared Memory:
Pipe:
Socket:
File
Names pipe
Message passing
Memory mapped file
 
#### Process state

1. Created: When a process is first created, it occupied the “created” or “new” state;
2. Waiting (Swapped out and blocked): A run queue is used in computer scheduling;
3. Running: A process is chosen for execution and instructions are executed one core of the CPU; a process can be kernel mode or user mode;
4. Blocked (Swapped out and blocked): A process blocked on some event (such as I/O operation completion or a signal), may be blocked due to various reasons, such as exhausting tis CPU time allocation or waiting for an event to occur;
5. Terminated: The underlying program is no longer executing and remains in the process table until its parent process calls ‘wait’ system call.

#### Dispatching/Scheduling

How does dispatcher decide which process to run next?
Search process table from front, run first ready thread
Link together the ready threads into a queue. Dispatcher grabs first thread from the queue. When threads become ready, insert at back of queue.
Give each thread a priority, organize the queue according to priority. Or, perhaps have multiple queues, one for each priority class.

 
### Thread

A thread is the entity within a process that can be scheduled for execution.
All threads of a process share its virtual address and system resources.

#### Why support threads?

Concurrent execution on multiprocessors
Manage I/O more efficiently: some threads wait for I/O while others compute
Most common usage for threads: large server applications

#### What is inside a thread?

1. Program counter, which keeps track of which instructions to execute next;
2. Registers, which hold its current working variables;
3. A stack, which contains the execution history
4. exception handlers,
5. a scheduling priority,
6. thread local storage,
7. a unique thread identifier,
8. a set of structures the system will use to save the thread context until it is scheduled

#### What is the differences between Process and Thread?

Processes are used to group resources together.
Threads are the entities scheduled for execution on the CPU.

1. Threads are easier to create than processes since they don’t require a separate address space;
2. Multithreading requires careful programming since threads share data structures that should only be modified by one thread at a time. Unlike threads, processes don’t share the same address space;
3. Threads are considered lightweight because they use far less resources than processes;
4. Processes are independent of each other. Threads since they share the same address space are interdependent, so caution must be taken so that different threads don’t step on each other. This is really another way of starting #2 above;
5. A process can consist of multiple threads.
 
 
Further down he provides the following table:

Per process items             | Per thread items
----------------------------- | -----------------
Address space                 | Program counter
Global variables              | Registers
Open files                    | Stack
Child processes               | State
Pending alarms                | 
Signals and signal handlers   | 
Accounting information        | 

 
#### Multithreads Programming

1. Context switching between threads is generally less expensive than in processes.
2. Critical section: Sections of code that modify data structures shared by multiple threads are called critical sections.
3. Synchronization: When a critical section is running in one thread it’s extremely important that no other thread be allowed into that critical section.



<br>
<br>
<br>

---

{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}<font size='4'>Tree and Graphs</font>













---

[Back to Content](#content)

