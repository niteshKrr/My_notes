# Introduction to Process Scheduling

## Process Scheduling 🔥
- Basis of Multi-programming OS.
- **By switching the CPU among processes, the OS can make the computer more productive.**
- Many processes are kept in memory at a time, when a process must wait(I/O operations) or time quantum expires, the OS takes the CPU away from that process & gives the CPU to another process & this pattern continues.

---

## Terminologies 📚

!!! info "CPU Scheduler"

    - Whenever the CPU become ideal, OS must select one process from the ready queue to be executed.
    - Done by **STS (short-term scheduler)**.

!!! info "Non-Preemptive scheduling `(not emptied pre (before) - ❌ time quantum)`"
    - Once CPU has been allocated to a process, the **process keeps the CPU until it releases CPU either by terminating or by switching to wait-state (process is doing I/O)**.
    - **`Starvation`**, as a process with long burst time may starve less burst time process.
    - **Low CPU utilization.**

!!! info "Preemptive scheduling `(emptied pre (before) - ✅ time quantum)`"
    - **CPU is taken away from a process after time quantum expires** along with terminating or switching to wait-state.
    - **`Less Starvation`**
    - **High CPU utilization**

!!! info "Terminologies associated with CPU scheduling"
    - **Throughput:** No. of processes completed per unit time.
    - **Arrival time (AT):** Time when process is arrived at the ready queue.
    - **Burst time (BT):** The time required by the process for its execution.
    - **Turn-around time (TAT):** Time taken from first time process enters ready state till it terminates. **(CT - AT)**
    -  **Wait time (WT):** Time process spends waiting for CPU. (WT = TAT – BT)
    -  **Response time:** Time duration between process getting into ready queue and process getting CPU for the first time.
    -  **Completion Time (CT):** Time taken till process gets terminated.

---

## Goals of CPU scheduling ⚽️
- Maximum CPU utilization
- Minimum Turnaround time (TAT).
- Min. Wait-time
- Min. response time.
- Max. throughput of system.