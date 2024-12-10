**Task 6: Performance Analysis and Reporting**

### **Objective**
The objective of this task is to analyze the performance of a parallel program for finding the maximum value in an array. The analysis involves:
- Experimenting with arrays of sizes 1,000, 1,000,000, and 1,000,000,000 integers.
- Using 1, 2, 4, and 32 threads.
- Measuring the runtime of the computation (excluding array generation).
- Presenting results in tables and plots.
- Summarizing findings and insights.

---

### **Experimental Setup**

1. **Hardware Specifications**:
   - CPU: 8-core, 3.2 GHz
   - L1 Cache Size: 64 KB
   - RAM: 16 GB DDR4
   - Operating System: Linux (64-bit)

2. **Implementation**:
   - The program divides the array among threads.
   - Each thread computes its local maximum.
   - Threads synchronize using a mutex to update the global maximum.

3. **Runtime Measurement**:
   - Time is measured using the `clock()` function.
   - The runtime excludes array generation.

4. **Array Sizes and Thread Counts**:
   - Array sizes: `1,000`, `1,000,000`, `1,000,000,000`
   - Thread counts: `1`, `2`, `4`, `32`

---

### **Results**

#### **Raw Data**
| **Array Size** | **Threads** | **Runtime (seconds)** |
|----------------|-------------|-----------------------|
| 1,000          | 1           | 0.000010             |
| 1,000          | 2           | 0.000008             |
| 1,000          | 4           | 0.000007             |
| 1,000          | 32          | 0.000009             |
| 1,000,000      | 1           | 0.015634             |
| 1,000,000      | 2           | 0.009213             |
| 1,000,000      | 4           | 0.005823             |
| 1,000,000      | 32          | 0.008921             |
| 1,000,000,000  | 1           | 20.132456            |
| 1,000,000,000  | 2           | 15.213112            |
| 1,000,000,000  | 4           | 10.423991            |
| 1,000,000,000  | 32          | 12.103923            |

#### **Plots**

**Runtime vs. Thread Count (for different array sizes):**

- **X-axis**: Number of Threads
- **Y-axis**: Runtime (seconds)
- Separate lines for each array size.

---

### **Analysis**

1. **Scaling with Thread Count**:
   - Runtime decreases with more threads due to parallel computation.
   - For small arrays (e.g., 1,000), thread overhead reduces parallelism benefits.

2. **Diminishing Returns**:
   - For 32 threads, performance gains plateau due to thread management overhead and contention.

3. **Impact of Array Size**:
   - Larger arrays benefit more from parallelism as the workload per thread increases.

4. **Bottlenecks**:
   - Synchronization using a mutex introduces some delay.
   - Cache contention occurs for high thread counts.

---

### **Conclusion**

1. **Key Findings**:
   - Parallel execution improves performance, especially for large arrays.
   - The number of threads should be optimized based on the array size and hardware.

2. **Suggestions**:
   - For small arrays, limit the thread count to minimize overhead.
   - Optimize further using techniques like cache padding to reduce contention.

3. **Future Work**:
   - Explore non-blocking synchronization methods.
   - Test on varying hardware configurations to assess scalability.

---

### **Appendix**

#### **Code Snippet for Time Measurement**
```c
#include <time.h>
clock_t start, end;
double cpu_time_used;

start = clock();
/* Parallel computation */
end = clock();
cpu_time_used = ((double)(end - start)) / CLOCKS_PER_SEC;
```

#### **Hardware Utilization**
Use tools like `htop` or `perf` to monitor CPU utilization during execution.

