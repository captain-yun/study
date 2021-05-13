### [프로세스와 스레드의 차이]

[Difference between Process and Thread]

* 프로세스는 실행 중인 프로그램을 가리킨다. 여기서 프로그램은 프로그래밍 언어를 통해 컴파일 혹은 인터프리티드된 **Binary Instructions Set**(바이너리 명령어 집합)을 가리킨다. 프로세스는 이러한 프로그램이 메모리에 적재(Load)된 형태로 프로그램의 **Execution Context**(실행 컨텍스트) 혹은 **Execution Instance** (실행중인 인스턴스) 이다. 
* 프로세스는 각각의 독립된 메모리 영역 (Code/Data/Stack/Heap)으로 구분되어 동작한다.
* 또한 Instructions set에 맞게 Task를 처리하기 위해선 Operating System(운영체제)로부터 다양한 System Resources들을 allocate(할당)받아야 한다. 
	* System resources : CPU Time, Memory space, LAN card, Audio device etc.
* 여러 개의 프로세스에 필요한 Hardware 자원(Resources)을 공급하고 프로세스 별 우선순위에 맞게 동작을 가능케 하는 것은 운영체제(이하 OS, Operating System)의 역할이다. OS는 프로그램과 하드웨어 자원 사이의 인터페이스 역할이자 총 관리 역할을 담당한다.
* 프로세스의 동작은 Process Control Block(이하 PCB)에 의해 제어되는데 PCB에는 priority, id, state 등의 정보가 저장되어 있다. OS는 프로세스의 PCB 정보를 보고 프로세스 별 우선순위에 따라 실행순서를 조율한다.
* 프로세스는 최소 1개 이상의 쓰레드를 가지고 있는데 쓰레드란 프로세스 내에서 실행되는 The unit of execution (실행의 단위)이자 A single sequential flow of control (프로그램 내 순차적인 제어 흐름)이다.
* 즉, 쓰레드는 beginning point 와 end point 이 있고 Execution Point (실행점)에 따라 Seqential하게 동작한다.
* 프로세스는 서로 프로세스간 독립적인 반면, 쓰레드는 한 프로세스 내에 별도의 stack과 register를 제외하곤 서로 share한다.

[What is Multi-Process vs Multi-Thread]
* Multi-Processing 이란 하나의 Program을 여러 개의 Process로 구성하여 Tasks를 처리하는 것이다.
* 프로세스는 서로 간 Independent 하므로 프로세스 하나가 죽어도 별도의 독립된 프로세스에겐 영향을 주지 않는다.
* 하지만 Context Switching 시 expensive하다. Overhead가 발생한다. 즉, CPU register 값등 프로세스 교체 시 발생하는 작업이 쓰레드의 Context Switching에 비해 Heavy하다.
* 프로세스가 서로 Independent 하기 때문에 서로 간 특수한 통신 기법 (= IPC) 을 사용해야 한다.
* Multi-Thread란 하나의 Program을 여러 개의 Thread로 구성하여 Tasks를 처리하는 방법이다.
* 쓰레드 간 자원을 공유하는 특성에 따라 프로세스처럼 OS에서 새로운 Resources 을 할당할 필요가 없다. 이는 Resources 효율성을 증가시킨다.
* Context Switching 시 프로세스에 비해 less-expensive하다. 이에 따라 처리속도가 증가한다.
* 하지만 Multi-Thread는 구현 시 동기화 문제 등을 고려해야하고 쓰레드 간 자원을 공유하기 때문에 하나의 쓰레드에서 문제가 발생 시 다른 쓰레드에도 영향을 준다. dependency가 높다.

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

> 참고
>> https://www.geeksforgeeks.org/difference-between-process-and-thread/
>> https://stackoverflow.com/questions/5593328/software-threads-vs-hardware-threads
>> https://www.backblaze.com/blog/whats-the-diff-programs-processes-and-threads/
>> https://www.youtube.com/watch?v=h_HwkHobfs0
