### [프로세스와 스레드의 차이]

[Difference between Process and Thread]

프로세스는 실행 중인 프로그램을 가리킨다. 프로세스의 동작은 Process Control Block(이하 PCB)에 의해 제어되는데 PCB에는 priority, id, state 등의 정보가 저장되어 있어 

Question
> 쓰레드는 프로세스다?
>> 

```mermaid

```

https://www.youtube.com/watch?v=h_HwkHobfs0

```
* program is set of instructions written in programming langauge.
```

[what is kernel?]
* It can be thought of as the program which controls all other programs on the compute.
* When it starts it goes through some initialization (booting) functions, such as checking memory.
* It is responsible for assigning and unassigning memory space which allows software to run.

The kernel provides services so programs can request the use of the network card, the disk or other pieces of hardware.

[Threads vs. Process]
* A program starts out as a text file of programming code which is written by a programmer.
* The program is complied or interpreted into binary from which is a suitable form to be loaded into memory(RAM).
* We call a program as a process if the program is on the run.
* Processes are typically independent of each other, while one or more than one threads exist as the subset of a process.
* A thread is often called **a lightweight process** because it has the same property as a process, except the fact that threads share the same address space with the process and other threads within the same process, whereas processes are totally independent when it comes to the data they use.
* For the reason above, A thread can communicate with other threads more easier than how processes communicate with other processes. In addition, as for the way of changing the flow of control of programs, what is so called "Context switching",  threads are less expensive than processes.
* 



[Thread]
* A thread is a single sequential flow of control within a program.
* A thread is unit of execution and Operating system must allocate a kernel object for each thread, along with a set of data structures.
* A thread has a beginning, a sequence, and an end, just as a sequential programs have their own. 
* Thus, at any given time during the runtime of the thread, there is a single point of execution.
* However, a thread itself is not a program; a thread cannot run on its own.
* Rather, it runs within a program.
* A thread 
  
* 한 브라우저에 멈춤현상 등 문제가 생겨 강제 종료를 해야할 때 하나의 창을 닫으면 모든 인터넷 브라우저 창이 닫히는 이유가 프로세스 하나에서 동작되기 때문이다. ?
* 










> 참고
>> https://www.geeksforgeeks.org/difference-between-process-and-thread/
>> https://stackoverflow.com/questions/5593328/software-threads-vs-hardware-threads
>> https://www.backblaze.com/blog/whats-the-diff-programs-processes-and-threads/
