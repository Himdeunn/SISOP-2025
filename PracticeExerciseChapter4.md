# Chapter 4 – Threads & Concurrency: Practice Exercises

<br>

## 4.1 – Provide three programming examples in which multithreading provides better performance than a single-threaded solution

1. **Web Server Handling Multiple Requests**  
   A multithreaded web server creates a new thread to handle each HTTP request from a client. This is significantly more efficient than handling requests sequentially in a single-threaded manner, especially under high traffic.

2. **Parallel Image Processing**  
   Large images can be divided into smaller parts and processed in parallel by multiple threads for tasks such as applying filters, resizing, or converting color spaces.

3. **Real-time Gaming Engine**  
   In modern games, separate threads are used for rendering graphics, computing physics, and handling AI. This allows smoother gameplay and better utilization of CPU cores.

<br>

## 4.2 – Using Amdahl’s Law, calculate the speedup gain of an application that has a 60 percent parallel component for:

#### (a) Two processing cores
Amdahl’s Law:
```math
Speedup = \frac{1}{(1 - P) + \frac{P}{N}}
```

Where:  
- \( P = 0.6 \) (60% parallelizable)  
- \( N = 2 \)

```math
Speedup = \frac{1}{(1 - 0.6) + \frac{0.6}{2}} = \frac{1}{0.4 + 0.3} = \frac{1}{0.7} \approx 1.43
```

#### (b) Four processing cores

```math
Speedup = \frac{1}{(1 - 0.6) + \frac{0.6}{4}} = \frac{1}{0.4 + 0.15} = \frac{1}{0.55} \approx 1.82
```

<br>

## 4.3 – Does the multithreaded web server described in Section 4.1 exhibit task or data parallelism?

**Answer:**  
It exhibits **task parallelism**, as each thread handles a distinct task (serving different HTTP requests), even though the tasks are similar in nature.

<br>

## 4.4 – What are two differences between user-level threads and kernel-level threads? Under what circumstances is one type better than the other?

| Aspect                   | User-Level Threads                     | Kernel-Level Threads                  |
|-------------------------|----------------------------------------|---------------------------------------|
| Management              | Managed in user space                  | Managed by the operating system       |
| Context Switching       | Fast and efficient                     | Slower due to kernel interaction      |

**When is one better?**  
User-level threads are ideal for applications that don’t require frequent system calls, while kernel-level threads are better for multitasking and CPU-intensive processes that benefit from true parallelism.

<br>

## 4.5 – Describe the actions taken by a kernel to context-switch between kernel-level threads

**Answer:**
1. The kernel saves the current thread’s state (program counter, registers, stack pointer, etc.).
2. It selects the next thread to execute based on the scheduling algorithm.
3. It loads the saved state of the selected thread.
4. Execution continues from the point where the new thread was previously paused.

