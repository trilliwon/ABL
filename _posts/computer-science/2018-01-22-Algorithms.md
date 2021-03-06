---
layout: post
title:  "Algorithms"
date:   2018-01-22 16:00:00 +0900
tag: [Computer Science, Algorithms]
---

# Data Structure

# **BASIC CONCEPTS**

## System Life Cycle

1. Requirements
2. Analysis
3. Design
4. Refinement and coding
5. Verification
  - Correctness proofs
  - Testing
  - Error removal

## Definition Of Data Abstraction

- Definition : An abstract data type (ADT) is a data type that is organized in such a way that the specification of the objects and the specification of the operations on the objects is separated from the representation of the objects and the implementation of the operations.

## Definition of Algorithm
  - An algorithm is a finite set of instructions that, if followed, accomplishes a particular task. In addition, all algorithms must satisfy the following criteria:
  1. Input : There are zero or more quantities that are externally supplied.
  2. Output : At least one quantity is produced.
  3. Definiteness : Each instruction is clear and unambiguous
  4. Finiteness : If we trace out the instructions of an algorithm, then for all cases, the algorithm terminates after a finite number of steps.
  5. Effectiveness : it also must be feasible.

## Asymptotic Notation (O, Ω, Θ)

- Definition : [Big "oh"] f(_n_) = O(g(_n_)) (read as "_f_ of _n_ is big oh of _g_ of _n_") if and only if there exist positive constants _c_ and _n_<sub>0</sub> such that f(_n_) <= cg(_n_) for all _n_, _n_ >= _n_<sub>0</sub>.

- Definition : [Omega] f(_n_) = Ω(g(_n_)) (read as "_f_ of _n_ is omega of g of _n_") if and only if there exist positive constants c and n<sub>0</sub> such that f(_n_) >= cg(_n_) for all _n_, _n_ >= _n_<sub>0</sub>.

- Definition : [Theta] f(_n_) = Θ(g(_n_)) (read as "_f_ of _n_ is theta of g of _n_") if and only if there exist positive constants c<sub>1</sub>, c<sub>2</sub>, and _n_ 0 such that c<sub>1</sub>g(_n_) <= f(_n_) <= c<sub>2</sub>g(_n_) for all _n_, _n_ >= _n_<sub>0</sub>.


---

# **Stack**
  - A stack is an ordered list in which insertions(aka. pushes and adds) and deletions(aka. pops or removes) are made at one end called the _top_.
  - _Last-In-First-Out_ (LIFO)

# **Queues**

# **Linked List**
# **Trees**
# **Graphs**
  - Operations
    - Depth First Search
    - Breadth First Search
    - Connected Components
    - Spanning Trees
    - Biconnected Components
  - Minimum Cost Spanning Trees
    - Kruskal's Algorithm
    - Prim's Algorithm
    - Sollin's Algorithm
  - Shortest Paths and Transitive Closure
  - Activity Networks

---

# **Sorting**
  - Insertion Sort
  - Quick Sort
  - Merge Sort
  - Heap Sort
  - Sorting on Several Keys
  - List and Table Sorts
  - Internal Sorting
  - External Sorting

---

# **Hashing**
  - Static Hashing
  - Dynamic Hashing
  - Bloom Filters

---

# **Priority Queues**
  - Single- and Double-Ended Priority Queues
  - Leftist Trees
  - Binomial Heaps
  - Fibonacci Heaps
  - Pairing Heaps

---

# **Efficient Binary Search Trees**
  - Optimal Binary Search Trees
  - AVL Trees
  - Red-Black Trees
  - Splay Trees
    - Bottom-Up Splay Trees
    - Top-Down Splay Trees

---

# **Multiway Search Trees**
  - m-way Search Trees
  - B-Trees
  - B<sup>+</sup>-Trees

---

# **Digital Search Structures**
  - Digital Search Trees
  - Binary Tries and Patricia
  - Multiway Tries
  - Suffix Trees
  - Tries and Internet Packet Forwarding

---

# Todo

- [algorithms](https://www.coursera.org/specializations/algorithms)
- [logic-introduction](https://www.coursera.org/learn/logic-introduction)
- [mit ocw algorithm  one](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/)
- [mit ocw algorithm two](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/)
- [mit ocw algorithm three](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-854j-advanced-algorithms-fall-2008/)
