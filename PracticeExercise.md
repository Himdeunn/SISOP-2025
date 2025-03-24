# LAPORAN SISTEM OPERASI
## TUGAS PRACTICE EXERCISE

Nama: Tegar Aprilian Wibowo
NRP: 3124500049
Dosen Pengajar: Dr. Ferry Astika Saputra ST, M.Sc  
Program Studi: D3 Teknik Informatika  
Institusi: Politeknik Elektronika Negeri Surabaya (PENS)  
Tahun: 2025  

---

### 1.1 What are the three main purposes of an operating system?
1. Resource Management: The operating system manages hardware resources such as CPU, memory, and I/O devices, ensuring efficient allocation and utilization.  
2. Abstraction and Simplification: It provides a simplified interface for users and applications to interact with the hardware, hiding the complexities of the underlying system.  
3. Security and Protection: The operating system ensures that different processes and users do not interfere with each other, providing a secure environment.  

---

### 1.2 When is it appropriate for the operating system to forsake efficiency and "waste" resources? Why is such a system not really wasteful?
It is appropriate to "waste" resources when prioritizing user experience, system stability, or security. For example:  
- Redundancy: Keeping multiple copies of data to ensure fault tolerance.  
- Over-provisioning: Allocating more resources than needed to handle peak loads.  
- Security Measures: Using additional resources for encryption or monitoring.  

Such systems are not truly wasteful because the "wasted" resources serve critical purposes like reliability, performance, and security, which outweigh the cost of inefficiency.  

---

### 1.3 What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
The main difficulty is ensuring predictable and deterministic response times. Real-time systems require tasks to be completed within strict deadlines, and the operating system must prioritize tasks accordingly. This involves:  
- Efficient scheduling algorithms.  
- Minimizing latency and jitter.  
- Handling interrupts and I/O operations without causing delays.  

---

### 1.4 Should the operating system include applications such as web browsers and mail programs? Argue both sides.
*Yes, it should include them*:  
- Convenience: Pre-installed applications provide a ready-to-use system for users.  
- Integration: Applications can be tightly integrated with the OS for better performance and security.  
- Consistency: Ensures a uniform user experience across devices.  

*No, it should not include them*:  
- Bloatware: Including unnecessary applications can bloat the OS, consuming resources.  
- Flexibility: Users may prefer alternative applications, and pre-installed apps limit choice.  
- Security Risks: More applications increase the attack surface for potential vulnerabilities.  

---

### 1.5 How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security)?
- Kernel Mode: The OS runs in kernel mode, allowing direct access to hardware and critical system resources.  
- User Mode: Applications run in user mode, with restricted access to hardware and sensitive areas of the system.  

This separation prevents user applications from interfering with the OS or other applications, ensuring system stability and security.  

---

### 1.6 Which of the following instructions should be privileged?
Privileged instructions are those that can only be executed in kernel mode to protect system integrity. The privileged instructions are:  
- a. Set value of timer.  
- c. Clear memory.  
- e. Turn off interrupts.  
- f. Modify entries in device-status table.  
- g. Switch from user to kernel mode.  
- h. Access I/O device.  

Non-privileged instructions:  
- b. Read the clock.  
- d. Issue a trap instruction.  

---

### 1.7 Describe two difficulties that could arise from placing the OS in a memory partition that cannot be modified.
1. Limited Flexibility: The OS cannot dynamically adjust its memory usage, making it difficult to handle varying workloads or new features.  
2. Performance Bottlenecks: If the OS cannot modify its own memory, it may struggle to optimize performance or respond to system events efficiently.  

---

### 1.8 What are two possible uses of multiple modes of operation in CPUs?
1. Enhanced Security: Additional modes can provide finer-grained access control, isolating critical processes from less trusted ones.  
2. Specialized Operations: Modes can be designed for specific tasks, such as virtualization or real-time processing, improving efficiency.  

---

### 1.9 How could timers be used to compute the current time?
Timers can be used to track elapsed time by counting clock ticks. For example:  
- A system timer increments at a fixed frequency (e.g., 1,000 ticks per second).  
- The OS records the number of ticks since a known start time (e.g., system boot).  
- By multiplying the tick count by the interval between ticks, the OS can calculate the current time.  

---

### 1.10 Give two reasons why caches are useful. What problems do they solve? What problems do they cause?
*Reasons caches are useful*:  
1. Speed: Caches provide faster access to frequently used data, reducing latency.  
2. Efficiency: They reduce the load on slower storage devices (e.g., disks) by serving data from faster memory.  

*Problems they solve*:  
- Slow access times for data stored in main memory or secondary storage.  
- High latency in fetching data from remote or slow devices.  

*Problems they cause*:  
- Cache Coherence: Ensuring consistency between cache and main memory.  
- Cache Pollution: Storing unnecessary data, reducing effective cache size.  

*Why not make caches as large as the device they cache?*  
- Cost: Larger caches are more expensive.  
- Diminishing Returns: Beyond a certain size, the performance gains do not justify the cost.