---
layout: post
title:  "Concurrent Programming Notes"
date:   2017-12-15 21:40:00 +0900
categories: concurrent
permalink: /concurrent01/
tag: [compiler, programming, parse tree, ast]
---

# Sequential computation vs Concurrent computation

# Parallel vs Concurrent

# Mutual Exclusion - Safety property
# No Starvation - Liveness
# Producer / Consumer - Safety property

# Amdahl's Low
> ### speed up = (1-thread execution time) / (n-threads execution time)
> ### speed up = 1/(ParallelPart/N + SequentialPart)



# Coarse grained algorithm vs Fine grained algorithm

# Time, Event, Interval, Thread

# Events of two or more threads

>## A -> B ≠> B -> A
>### "Happen before"

# a<sup>k</sup><sub>0</sub>
> k-th occurrence of event a<sub>0</sub>

# Locks (Mutual Exclusion)
```
public interface Lock {
  public void lock();  // Acquire
  public void unlock(); // Release
}
```

# Deadlock free
  - if some thread call lock()
  - and never return
  - Then other threads must complete lock() and unlock() calls infinitely often
  - System as a whole makes progress, Even if individuals starve

# Starvation free
  - If some thread calls lock()
  - It will eventually return
  - Individual threads make progress

`victim = i; // other go first`

# Lock free
# Wait free

# Peterson's Algorithm
```
lock() {
  flag[i] = true;
  victim = i;
  while (flag[j] && victim == i) { };
}

unlock() {
  flag[i] = false;
}
```
# Bakery Algorithm

```
lock() {
  flag[i] = true;
  label[i] = max(label[0], ...,label[n-1])+1;
  while ((Exist)k flag[k] && (label[i],i) > (label[k],k));
}

unlock() {
  flag[i] = false;
}

```

# Sequential Specification

- ## If(precondition)
  - the object is in such-and-such a state – before you call the method,
- ## Then (postcondition)
  - the method will return a particular value – or throw a particular exception.
- ## and(postcondition, con’t)
  - the object will be in some other state
  - when the method returns,


# Linearizability
  - ## Each method should
    - ### “take effect”
    - ### Instantaneously
    - ### Between invocation and response events
  - ## Object is correct if this “sequential” behavior is correct
  - ## Any such concurrent object is
   - # Linearizable<sup>TM</sup>

# Progress Conditions
- ## Deadlock-free: some thread trying to acquire the lock eventually succeeds.
- ## Starvation-free: every thread trying to acquire the lock eventually succeeds.
- ## Lock-free: some thread calling a method eventually returns.
- ## Wait-free: every thread calling a method eventually returns.
