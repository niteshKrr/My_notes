# Multi-Tasking Operating System


## Multi-Tasking Operating System

**A Multi-tasking Operating System** is an OS that allows multiple tasks (or processes) to run simultaneously by sharing CPU time among them. It achieves this by rapidly switching between tasks, giving the illusion that multiple tasks are being executed at the same time, even though, in reality, the CPU can only execute one task at any given moment (in a single-core system).

* Almost similar to Multi-programming OS + time-sharing
* Each process is executed for a maximum fixed interval of time, then another program is sent to the CPU.
* It is also known as time-sharing systems.


![loading...](../../../images/operating_system/types_of_os/multi_tasking.webp)



## Key Features of a Multitasking OS

!!! success ""

    1. **Multiple Tasks at the Same Time :-**
    Multi-tasking allows the CPU to handle several tasks at once by switching between them frequently.

    2. **Time-sharing :-**
    Each task is assigned a small unit of time (called a time slice or quantum). The OS rapidly switches between tasks during these time slices, ensuring that each task gets CPU time. This switching is so fast that users experience it as if all tasks are running simultaneously.

    3. **Preemptive vs. Cooperative Multi-tasking :-**
        * **Preemptive Multi-tasking :-** The OS can forcibly take control of the CPU from a running process after its time slice is over and give it to another process. Modern operating systems like Linux, Windows, and macOS use preemptive multi-tasking.
        * **Cooperative Multi-tasking :-** In this older method, the OS relies on each process to voluntarily give up control of the CPU. This method was used in early versions of operating systems like Windows 3.x.

    4. **Context Switching :-**
    When the OS switches between tasks, it saves the state of the current task (e.g., registers, program counter) and loads the state of the next task to resume its execution. This is called context switching. This happens so fast that users do not notice the switch.

    5. **Task Prioritization :-**
    The OS assigns priority to tasks. High-priority tasks get more CPU time or are executed before low-priority tasks. This ensures that critical tasks are not delayed by less important ones.

    6. **Concurrency :-**
    Multi-tasking introduces concurrency by overlapping the execution of multiple tasks. However, it doesn't mean tasks are truly running in parallel (unless on a multi-core processor). Instead, tasks share CPU resources in quick succession.


---


## Types of Multi-tasking OS

### 1. Single-core Multi-tasking

In a single-core processor, multi-tasking is achieved by time-sharing where the CPU switches between different processes very quickly.

### 2. Multi-core Multi-tasking

In a system with multiple cores, multi-tasking can involve parallel execution, where different processes are run on separate CPU cores, allowing true simultaneous execution of multiple tasks.


---


## Multi-tasking vs. Multi-programming

!!! tip ""

    * **Multi-tasking:** Focuses on the illusion of simultaneous task execution by switching between tasks very quickly (time-sharing). It often operates in systems where users interact with applications in real-time.

    * **Multi-programming:** Focuses on maximizing CPU utilization by keeping multiple programs in memory and switching between them when one is waiting (like for I/O). It was mainly used in older batch processing systems.


