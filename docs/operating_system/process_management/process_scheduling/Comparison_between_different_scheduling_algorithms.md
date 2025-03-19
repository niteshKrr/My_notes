# Comparison between Process Scheduling Algorithms 🤼‍♂️

|  | Design | Preemption | Convoy Effect | Overhead `(context switching)` |
| ----------- | ----------- | ----------- | -----------| ----------- |
| **First come First Serve** | Simple | No | Yes | No |
| **Shortest Job First** | Complex (how to find out `burst time`) | No | Yes | No |
| **Pre-emptive Shortest Job First** | Complex | Yes | No | Yes |
| **Priority Scheduling** | Complex (how to give suitable `priority`) | No | Yes | No |
| **Pre-Emptive Priority** | Complex | Yes | Yes (low priority might never get CPU) | Yes |
| **Round Robin** | Simple | Yes | No | Yes |
| **Multi-level Queue** | Complex | Yes | Yes | Yes |
| **Multi-level Feedback Queue** | Complex | Yes | Yes (though we try to reduce it using **aging**) | Yes |