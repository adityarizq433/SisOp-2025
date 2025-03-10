# TUGAS 2 SISTEM OPERASI 
## PRACTICE EXERCISE

**Nama** : Mukhamad Aditya Rizq Qiya Mullail  
**NRP** : 3124500050  
**Dosen Pengajar** : Dr Ferry Astika Saputra ST, M.Sc  
**PROGRAM STUDI** D3 TEKNIK INFORMATIKA  
**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)  
TAHUN 2025**

---

### 1. What are the three main purposes of an operating system?
- **Resource Management**  
  The OS manages hardware resources such as the CPU, memory, storage, and peripheral devices. It ensures efficient allocation and utilization of these resources among multiple applications and users.
- **Abstraction and Simplification**  
  The OS provides a simplified interface for users and applications to interact with the hardware. It hides the complexity of hardware operations through abstractions like file systems, device drivers, and system calls.
- **System Protection and Security**  
  The OS ensures that different programs and users do not interfere with each other. It enforces security policies, manages user permissions, and protects the system from unauthorized access or malicious activities.

---

### 2. When is it appropriate for the operating system to forsake efficiency and "waste" resources? Why is such a system not really wasteful?
It is appropriate for the operating system to forsake efficiency and "waste" resources in scenarios where improving reliability, security, or user experience takes priority over raw performance. While this may seem wasteful, such trade-offs are often necessary to achieve higher-level goals.

#### a. Redundancy for Reliability:
- The OS may allocate extra resources (e.g., memory, storage, or CPU cycles) to create backups, redundancy, or fail-safes.  
- **Why it's not wasteful**: Ensures system stability and data integrity, preventing costly failures or data loss.

#### b. Security Measures:
- The OS might use additional resources to enforce security policies, such as encryption, access control, or sandboxing applications.  
- **Why it's not wasteful**: The cost of a security breach far outweighs the resource overhead.

#### c. User Experience and Responsiveness:
- The OS may prioritize responsiveness over efficiency, such as preloading frequently used applications into memory.  
- **Why it's not wasteful**: A more responsive system enhances productivity and user satisfaction.

#### d. Future-Proofing and Scalability:
- The OS might reserve resources for future tasks or scalability.  
- **Why it's not wasteful**: Ensures the system can handle unexpected workloads.

---

### 3. What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
The main difficulty is ensuring **deterministic timing and predictability**. Real-time systems must complete tasks within strict deadlines.

#### Key challenges:
- **Guaranteeing Timely Execution**: Scheduling algorithms must prioritize tasks based on deadlines.
- **Minimizing Latency and Jitter**: Reducing interrupt handling times, context switching overhead, etc.
- **Resource Management Under Constraints**: Limited CPU, memory, and power resources must be efficiently allocated.
- **Handling Concurrency and Synchronization**: Avoiding race conditions and deadlocks.
- **Predictable Behavior in All Scenarios**: Must function correctly even under high load.
- **Integration with Hardware**: Precise control over hardware resources is required.

---

### 4. Should the operating system include applications such as web browsers and mail programs?
**Yes, it should include them:**
- **Convenience**: Pre-installed applications provide a ready-to-use system.
- **Integration**: Apps can be optimized for better security and performance.
- **Consistency**: Ensures a uniform user experience.

**No, it should not include them:**
- **Bloatware**: Increases system resource usage unnecessarily.
- **Flexibility**: Users may prefer alternative applications.
- **Security Risks**: Increases the attack surface for vulnerabilities.

---

### 5. How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security)?
- **Kernel Mode**: The OS runs in kernel mode, allowing direct access to hardware and critical system resources.
- **User Mode**: Applications run in user mode, with restricted access to prevent interference with the OS or other applications.

This separation prevents user programs from disrupting system stability and security.

---

### 6. Which of the following instructions should be privileged?
**Privileged instructions:**
- Set value of timer.
- Clear memory.
- Turn off interrupts.
- Modify entries in the device-status table.
- Switch from user to kernel mode.
- Access I/O device.

**Non-privileged instructions:**
- Read the clock.
- Issue a trap instruction.

---

### 7. Describe two difficulties that could arise from placing the OS in a memory partition that cannot be modified.
1. **Limited Flexibility**: The OS cannot dynamically adjust its memory usage, making it difficult to handle varying workloads.
2. **Performance Bottlenecks**: The OS cannot optimize its performance or respond to system events efficiently.

---

### 8. What are two possible uses of multiple modes of operation in CPUs?
1. **Enhanced Security**: Finer-grained access control can isolate critical processes.
2. **Specialized Operations**: Specific modes for virtualization or real-time processing can improve efficiency.

---

### 9. How could timers be used to compute the current time?
1. A system timer increments at a fixed frequency (e.g., 1,000 ticks per second).
2. The OS records the number of ticks since a known start time (e.g., system boot).
3. By multiplying the tick count by the interval between ticks, the OS calculates the current time.

---

### 10. Give two reasons why caches are useful. What problems do they solve? What problems do they cause?
#### **Reasons caches are useful:**
- **Speed**: Faster access to frequently used data.
- **Efficiency**: Reduces the load on slower storage devices.

#### **Problems they solve:**
- Slow access times for data in main memory or secondary storage.
- High latency in fetching data from remote or slow devices.

#### **Problems they cause:**
- **Cache Coherence**: Ensuring consistency between cache and main memory.
- **Cache Pollution**: Storing unnecessary data reduces effective cache size.

#### **Why not make caches as large as the device they cache?**
- **Cost**: Large caches are expensive.
- **Diminishing Returns**: Beyond a certain size, performance gains do not justify the cost.
