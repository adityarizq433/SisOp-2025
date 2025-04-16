# Chapter 4 Exercise

## 4.1 – Provide three programming examples in which multithreading provides better performance than a single-threaded solution.

1. **Web Server**: Handles multiple client requests concurrently by assigning each connection to a separate thread.
2. **Image Processing**: Applies filters to different parts of an image simultaneously using multiple threads.
3. **Data Analytics**: Splits large datasets among threads to compute averages, sums, or aggregations in parallel.

---

## 4.2 – Using Amdahl’s Law, calculate the speedup gain of an application that has a 60 percent parallel component for (a) two processing cores and (b) four processing cores.

**Formula:**  
Speedup = 1 / ((1 - P) + P / N)

- **(a) Two cores:**  
  Speedup = 1 / (0.4 + 0.3) = 1 / 0.7 ≈ **1.43**

- **(b) Four cores:**  
  Speedup = 1 / (0.4 + 0.15) = 1 / 0.55 ≈ **1.82**

---

## 4.3 – Does the multithreaded web server described in Section 4.1 exhibit task or data parallelism?

**Task parallelism**: Each thread handles a separate client request with independent tasks.

---

## 4.4 – What are two differences between user-level threads and kernel-level threads? Under what circumstances is one type better than the other?

1. **Management**:  
   - *User-level*: Managed by a user-space library.  
   - *Kernel-level*: Managed by the OS kernel.

2. **Context Switching**:  
   - *User-level*: Fast, no kernel involvement.  
   - *Kernel-level*: Slower, involves switching to kernel mode.

**Best Use Case**:  
- Use *user-level* for quick management and no I/O.  
- Use *kernel-level* for true concurrency and I/O support.

---

## 4.5 – Describe the actions taken by a kernel to context-switch between kernel-level threads.

1. Save the current thread’s context (registers, program counter).
2. Update the current thread’s TCB.
3. Load the next thread’s context from its TCB.
4. Restore CPU state and switch to the new thread.

---

## 4.6 – What resources are used when a thread is created? How do they differ from those used when a process is created?

- **Thread**: Requires stack, registers, and control block. Shares memory and file descriptors.
- **Process**: Needs dedicated memory, open files, etc.

**Conclusion**: Threads are more lightweight and faster to create.

---

## 4.7 – Assume that an operating system maps user-level threads to the kernel using the many-to-many model and that the mapping is done through LWPs. Furthermore, the system allows developers to create real-time threads for use in real-time systems. Is it necessary to bind a real-time thread to an LWP? Explain.

Yes, binding a real-time thread to an LWP is **necessary** in many-to-many models to ensure the kernel can schedule it directly for time-critical tasks.

---
