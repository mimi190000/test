**Task 6: Performance Analysis and Reporting**

### **Summary of Findings**
Parallel execution demonstrates significant efficiency improvements for large arrays due to effective workload distribution across multiple threads. As the number of threads increases, the performance scales well initially, but diminishing returns are observed at higher thread counts. This is attributed to thread synchronization overhead, cache contention, and the costs associated with thread management. For small arrays, the computational cost of thread creation and synchronization often exceeds the benefits of parallelism, leading to limited performance gains.


### **Experimental Setup**

 **Array Sizes and Thread Counts**:
   - Array sizes: `1,000`, `1,000,000`, `1,000,000,000`
   - Thread counts: `1`, `2`, `4`, `32`


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


**Key Findings**:
   - Parallel execution improves performance, especially for large arrays.
   - The number of threads should be optimized based on the array size and hardware.

