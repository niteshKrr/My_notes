# Introduction to Concurrency 😎

## Concurrency 🤔

!!! success ""
    - Concurrency is the execution of the multiple instruction sequences at the same time.
    - It happens in the operating system when there are **several process threads running in parallel**.

---

## Thread

!!! quote ""
    - Single sequence stream within a process.
    - An independent path of execution in a process.
    - Light-weight process.
    - Used to achieve parallelism by dividing a process’s tasks which are independent path of execution.
    - E.g., Multiple tabs in a browser, text editor (When you are typing in an editor, spell checking, formatting of text and saving the text are done concurrently by multiple threads.)

---

### Thread Scheduling

!!! tip ""
    - Threads are scheduled for execution based on their priority.
    - Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.

---

### Threads context switching

!!! info ""
    - OS saves current state of thread & switches to another thread of same process.
    - Doesn’t includes switching of memory address space. (But Program counter, registers & stack are included.)
    - Fast switching as compared to process switching
    - CPU’s cache state is preserved.

---

## How each thread get access to the CPU?

!!! example ""
    - Each thread has its own program counter.
    - Depending upon the thread scheduling algorithm, OS schedule these threads.
    - OS will fetch instructions corresponding to PC of that thread and execute instruction.
    - I/O or TQ, based context switching is done here as well
        - We have TCB (Thread control block) like PCB for state storage management while performing context switching.

---

## Will single CPU system would gain by multi-threading technique?

!!! danger ""
    - Never.
    - As two threads have to context switch for that single CPU.
    - This won’t give any gain.
    - **for the CPU intensive tasks, there won't be gain, but for i/o or network related tasks, we will definitely benefit from using multithreading**.

---

## Benefits of Multi-threading

!!! info ""
    - Responsiveness
    - Resource sharing: Efficient resource sharing.
    - Economy: It is more economical to create and context switch threads.
        - Also, allocating memory and resources for process creation is costly, so better to
    divide tasks into threads of same process.
    - Threads allow utilization of multiprocessor architectures to a greater scale and efficiency.

---
