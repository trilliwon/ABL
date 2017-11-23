---
layout: post
title:  "DB Transaction"
date:   2017-11-22 13:00:00 +0900
categories: db
---

## Transaction

>+ Series of actions carried out by the user or application, which accesses or changes the contents of a database

>+ A unit of work performed within a DBMS against a DB

>+ Transforms a database from one consistent state to another, although consistency may be violated during transaction

>+ Each transaction must succeed or fail as a complete unit; it can never be only partially complete.

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
  >- Lost update problem
  >- Uncommitted dependency problem(The dirty read problem)
  >- Inconsistent analysis problem(The incorrect summary problem)
