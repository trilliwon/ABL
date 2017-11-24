---
layout: post
title:  "DB Transaction"
date:   2017-11-22 13:00:00 +0900
categories: db
---

# Transaction

- Series of actions carried out by the user or application, which accesses or changes the contents of a database
- A unit of work performed within a DBMS against a DB
- Transforms a database from one consistent state to another, although consistency may be violated during transaction
- Each transaction must succeed or fail as a complete unit; it can never be only partially complete.

## Properties of Transactions


### ACID Properties

#### Atomicity
- A transaction’s changes to the state are atomic: either all happen or none happen.

#### Consistency
- A transaction must transform a database from one consistent state to another

#### Isolation
- Even though transactions execute concurrently, it appears to each transaction T, that others executed either before T or after T, but not both.

#### Durability
- Once a transaction completes successfully (commits), its changes to the state survive failures and retain its changes

## Concurrency Control

- Process of managing simultaneous transactions on the database without having them interfere with one another
- Mainly focuses on the isolation property of transactions

### Why is concurrency control needed?

- Prevents the interference when two or more transactions are accessing the database simultaneously and at least one is updating data
- Although two transactions may be correct in themselves, interleaving of operations may produce an incorrect result
- Three potential problem
  - Lost update problem
  - Uncommitted dependency problem(The dirty read problem)
  - Inconsistent analysis problem(The incorrect summary problem)

---

## Serializabiltity

- The objective of concurrency control is to schedule transactions in such a way as to avoid any interference
- Could run transactions serially, but this limits the degree of concurrency or parallelism in a system

### Schedule
- a sequence of reads and writes by a set of concurrent transactions

### Serial schedule
- a schedule where the operations of each transaction are executed consecutively without any interleaved operations from other transactions
- Not guarantee that the results of all serial schedules of a given set of transactions will be identical
  - Every serial schedule is regarded correct

### Nonserial schedule
- a schedule where the operations from a set of concurrent transactions are interleaved

### Objective of serializability
- The **objective of serializability** is to find nonserial schedules that allow transactions to execute concurrently without interfering with one another
- In other words, want to find nonserial schedules that are equivalent to some serial schedule
  - Such a schedule is called serializable

### Equivalent
- Intuitively, two schedules s1 and s2 are equivalent if
  - Every read in s2 accesses the same value as the corresponding read in s1
  - The last values written into the database for every data item should be the same for s1 and s2

### Ordering of read/writes is important

- If two transactions either read or write completely separate data items, they do not conflict and the order is not important
- If two transactions only read the same data item, they do not conflict and the order is not important
- If one transaction writes a data item and another reads or writes the same data item, the order is important

### Precedence graph
- Under the constrained write rule(a transaction updates a data item based on its old value, which have always been first read), use the precedence graph to test for serializability
- Precedence graph
- Draw an arc Ti -> Tj (meaning Ti must come before Tj in its equivalent serial schedule s') if
  - Ti executes read(x) and Tj is the next transaction to execute write(x)
  - Ti executes write(x) and Tj executes read(X) to read the value written by Ti
- A schedule s is serializable iff there is no cycle in the precedence graph
- Node : transaction

## Concurrency Control Techniques

- Control concurrent transactions executed in a serializable schedule
- Typical techniques
  - Two-phase locking protocol
  - Timestamp ordering technique
  - Optimistic technique
