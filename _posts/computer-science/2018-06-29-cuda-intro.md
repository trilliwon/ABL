---
layout: post
title: Intro to CUDA
date: '2018-06-29 19:53:00 +0900'
tag:
  - Computer Science
  - CUDA
published: true
---


# CUDA/GPU Resources


---

- [NVIDIA CUDA Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)
- [CUDA Runtime API](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)
- [CUDA C Best Practices Guide](https://docs.nvidia.com/cuda/pdf/CUDA_C_Best_Practices_Guide.pdf)

- https://www.youtube.com/watch?v=F620ommtjqk&list=PLGvfHSgImk4aweyWlhBXNF6XISY3um82_
- https://github.com/1adrianb/bnn.torch/blob/master/BinarySpatialConvolution.cu
- https://devblogs.nvidia.com/efficient-matrix-transpose-cuda-cc/
- https://github.com/debowin/cuda-tiled-matrix-multiplication/blob/master/matrixmul_kernel.cu


---

# CUDA #1

---

## GPU Computing: Step by Step

- Setup inputs on the host (CPU-accessible memory)
- Allocate memory for outputs on the host
- Allocate memory for inputs on the GPU
- Allocate memory for outputs on the GPU
- Copy inputs from host to GPU
- Start GPU kernel (function that executed on GPU)
- Copy output from GPU to host

/Cuda.png

---

## Keywords

- **Thread** - Distributed by the CUDA runtime (threadIdx)
- **Block** - A user defined group of 1 to ~512 threads (blockIdx)
- **Grid** - A group of one or more blocks. A grid is created for each CUDA kernel function called

---

## Kernels

---

> CUDA C extends C by allowing the programmer to define C functions, called **kernels**, that, when called, are executed **N times** in parallel by **N different CUDA threads**, as opposed to only once like regular C functions.

> A kernel is defined using the `__global__` declaration specifier and the number of CUDA threads that execute that kernel for a given kernel call is specified using a new `<<<...>>>`execution configuration syntax.

> Each thread that executes the kernel is given a unique thread ID that is accessible within the kernel through the built-in `threadIdx` variable.

---

# CUDA Parallel Patterns

---

### [Darve_Teaching](http://mc.stanford.edu/Darve_Teaching)

## Parallel Patterns

- Think at a higher level than individual CUDA kernels
- Specify **what** to compute, not **how** to compute it
- Let programmer worry about algorithm
- Defer pattern implementation to someone else

---

## Common Parallel Computing Scenarios

- Many parallel threads need to generate a single result
	- **Reduce**
- Many parallel threads need to partition data
	- **Split**
- Many parallel threads produce variable output / thread
	- **Compact / Expand**
- **Blocking**
- **Reduction**
- **Scan**

---

## Primordial CUDA Pattern: Blocking  
  
- Partition data to operate in well-sized blocks
	- Small enough to be staged in shared memory
	- Assign each data partition to a thread block
	- No different from cache blocking!
- Provides several performance benefits
	- Have enough blocks to keep processors busy
	- Working in shared memory cuts memory latency dramatically
	- Likely to have coherent access patterns on load/store to shared memory

---

## Blocking

- Partition data into subsets that fit into shared memory
- Handle each data subset with one thread block
- Load the subset from global memory to shared memory, **using multiple threads to exploit memory-level parallelism**
- Perform the computation on the subset from shared memory
- Copy the result from shared memory back to global memory
- **All CUDA kernels are built this way**
	- Blocking may not matter for a particular problem, but you’re still forced to think about it
	- Not all kernels require `__shared__` memory
	- All kernels do require registers
- **All of the parallel patterns we’ll discuss have CUDA implementations that exploit blocking in some fashion**

---

## Reduction

- **Reduce** vector to a single value
- Via an associative operator (+, *, min/max, AND/OR, ...)
- CPU: sequential implementation
	- `for(int i = 0, i < n, ++i) ...`
- GPU: "tree"-based implementation

/tree.png

---

## Parallel Reduction Complexity

- `Log(N)` parallel steps, each step S does N/2^S independent ops
	- **Step Complexity** is `O(log N)`
- For N = 2^D, performs \\( \sum_{S \in [1..D]} 2^{D-S} = N-1 \\) operations
	- **Work Complexity** is O(N) – It is **work-efficient**
	- i.e. does not perform more operations than a sequential algorithm
- With P threads physically in parallel (P processors), **time complexity** is O(N/P + log N)
	- Compare to O(N) for sequential reduction

---

## Split Operation

- Given:array of true and false elements (and payloads)
- Return an array with all true elements at the beginning
- Examples: sorting, building trees

## Variable Output Per Thread: Compact
- Remove null elements
- Example: collision detection

## Variable Output Per Thread: General Case
- Reserve Variable Storage Per Thread
- Example: [binning or bucketing](https://en.wikipedia.org/wiki/Data_binning)

## Split, Compact, Expand
- Each thread must answer a simple question: _"Where do I write my output?"_
- The answer depends on what other threads write!
- **Scan** provides an efficient parallel answer

---

## Scan (a.k.a. Parallel Prefix Sum)

- Given an array \\( A = [a_0, a_1, ..., a_{n-1}] \\) and a binary associative operator \\( \oplus \\) with identity I,

$$scan(A) = [I, a_0, (a_0 \oplus a_1), ... , (a_0 \oplus a_1 + \oplus ... \oplus a_{n-2})]$$

- Prefix sum: if \\(\oplus\\) is addition, then scan on the series


/scan_and_result.png

### Applications of Scan
- Scan is a simple and useful parallel building block for many parallel algorithms:
	- Radix sort
	- Quicksort(seg.scan)
	- String comparison
	- Lexical analysis
	- Stream compaction 
	- Run-length encoding
	- Polynomial evaluation
	- Solving recurrences
	- Tree operations
	- Histograms
	- Allocation
	- Etc.

- Fascinating, since scan is **unnecessary** in sequential computing!
	- inclusive (include 
	- exclusive

- 2-phase scan
	1. Per-block scan & reduce
	2. Scan per-block sums


## Segmented Scan
- Scan + Barriers/Flags associated with certain positions in the input arrays
- Operations don’t propagate beyond barriers
- Irregular workload since segments can be of any length
- Efficiently storing and propagating information about segments
- Scans over all segments should happen in parallel
	- Overall work and space complexity should be O(n) regardless of the number of segments

## Representing Segments
- Possible Representations are
	- Vector of segment lengths
	- Vector of indices which are segment heads
	- Vector of flags: 1 for segment head, 0 if not
- First two approaches hard to parallelize as different size as input
- We use the third as it is the same size as input

### Segmented Scan - Flag Storage
- Space-inefficient to store one flag in an integer
- Store one flag in a byte striped across 32 words
- More efficient memory access
### Segmented Scan – implementation
- Similar to Scan
	- O(n) space and work complexity
	- Has two stages – reduce and down-sweep
- Unique to segmented scan
	- Requires an additional flag per element for intermediate computation
	- These flags prevent data movement between segments

### Segmented Scan – Advantages
- Operations in parallel over all the segments
- Irregular workload since segments can be of any length
- Can simulate divide-and-conquer recursion