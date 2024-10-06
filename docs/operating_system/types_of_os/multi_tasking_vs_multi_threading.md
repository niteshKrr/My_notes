# Multi-Tasking vs Multi-Threading

## Concept 🕵🏻‍♂️

* **Program :-** A Program is an executable file which contains a certain set of instructions written
to complete the specific job or operation on your computer.
    - It’s a compiled code. Ready to be executed.
    - Stored in Disk


* **Process :-** `Program under execution.` -  Resides in Computer’s primary memory (RAM).


!!! info "Threads 🪡🧶"

    - An independent path of execution in a process.
    - lightweight process. It is a smallest unit of processing.
    - A thread is a single sequence stream within in a process.
    - Used to achieve parallelism by dividing a process's tasks which are independent path of execution.
    - Threads exist within a process — every process has at least one. Threads share the process’s resources, including memory and open files.
    - E.g., Multiple tabs in a browser, text editor (When you are typing in an editor, spell-checking, formatting of text and saving the text are done concurrently by multiple threads.)

---



| Multi-Tasking      | Multi-Threading                          |
| ----------- | ------------------------------------ |
| The execution of more than one task simultaneously       | A process is divided into several different sub-tasks called as threads, which has its own path of execution. This concept is called as multithreading.  |
| Concept of more than 1 processes being context switched.       | Concept of more than 1 thread. Threads are context switched. |
| **Isolation and memory protection exists**. OS must allocate separate memory and resources to each program that CPU is executing.    | No isolation and memory protection, resources are shared among threads of that process. OS allocates memory to a process; multiple threads of that process share the same memory and resources allocated to the process. |


---

??? example "Analogy explanation of `multitasking` & `multithreading`"
    Let's say there's one computer and a maintainer, and there are 5 people in a line waiting for their chance to use PC and do their work. Maintainer maintains a rule that no individual is allowed to work continuously for consecutive 5 minutes. If his/her work completes with in 5 minutes, they leave and the next one will get the PC, else, after 5 minutes, they will go back to the end of the line and again wait for their turn.

    This is multi-tasking, (time-sharing).

    Now, suppose a individual person needs to send some mail, research some topic, and download some pics. Either he can do one task after another, or he can perform a task for some time, let's say 1 minute and then move to another task. So, he is basically switching tasks in his own time frame.  This is multi-threading. Each individual task will be called an independent thread of execution.

    This is multi-threading.


---


## Thread Scheduling

- Threads are scheduled for execution based on their priority.
- Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.


---


## Thread Context Switching Vs Process Context Switching

| Thread Context Switching      | Process Context Switching                          |
| ----------- | ------------------------------------ |
| OS saves current state of thread & switches to another thread of same process.      | OS saves current state of process & switches to another process by restoring its state.  |
| Doesn’t includes switching of memory address space. (But Program counter, registers & stack are included.)       | Includes switching of memory address space. |
| Fast switching.   | Slow switching. |
|CPU’s cache state is preserved.   | CPU’s cache state is flushed. |


---


???+ warning "If threads are so good concept, why don't we make 100s or 1000s of threads?"

    - **You can create as many threads as you want, but you will only get as much parallelism as the number of cores in your CPU.**
    - Threads are not free. `Each thread consumes memory for its stack and other data structures`. 
    - Threads also require time to create and destroy. 
    - `If you have too many threads, the overhead of managing them can exceed the benefit of parallelism`.
