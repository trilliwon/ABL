---
layout: post
title:  "[In progress] MariaDB Scalable Lock Manager"
date:   2017-12-08 20:00:00 +0900
categories: concurrent_programming
permalink: /lock_manager/
---

# [innobase](https://github.com/MariaDB/server/tree/10.3/storage/innobase)

# lock_sys_t

[void lock_sys_create()](https://github.com/MariaDB/server/blob/976f6fb1b6320f7eb2cd228d9690de85fec330e8/storage/innobase/lock/lock0lock.cc#L486)
# Shared/Exclusive mode Lock

- Declared in `include/lock0types.h`

```
/* Basic lock modes */
enum lock_mode {
	LOCK_IS = 0,	/* intention shared */
	LOCK_IX,	/* intention exclusive */
	LOCK_S,		/* shared */
	LOCK_X,		/* exclusive */
	LOCK_AUTO_INC,	/* locks the auto-inc counter of a table
			in an exclusive mode */
	LOCK_NONE,	/* this is used elsewhere to note consistent read */
	LOCK_NUM = LOCK_NONE, /* number of lock modes */
	LOCK_NONE_UNSET = 255
};

```

# TODO

- [x] benchmark (sysbench, perf) [DONE]
- [ ] understand related codes [DOING]
  - [/innobase/lock/lock0lock.cc](https://github.com/MariaDB/server/tree/10.3/storage/innobase/lock)
  - [innobase/include/lock0lock.h](https://github.com/MariaDB/server/blob/10.3/storage/innobase/include/lock0lock.h)
- [ ] design for read-only transaction
- [ ] implementation for read-only transaction
- [ ] benchmark (sysbench, perf)
- [ ] design for read/write transaction
- [ ] implementation for read/write transaction
- [ ] benchmark (sysbench, perf)

# Code Review

### TA's Code Review
```
// lock system structure
include/lock0lock.h:937
struct lock_sys_t {
    ..
    LockMutex mutex; // hash table에 접근할 때 사용하는 global mutex
    hash_table_t* rec_hash; // record lock hash table

}

// lock system이 초기화되는 곳
srv/srv0start.cc:1861
lock_sys_create()
 - lock system global mutex 초기화
 - rec_hash를 hash_create() 함수로 초기화

// record lock을 잡는 함수
lock/lock0lock.cc:2594
lock_rec_lock()
 - locking table에 lock을 매달아 두는 entry point
 - 여기서 shared lock을 잡을지 exclusive lock을 잡을지.. conflict되는애가 있는지 확인해서 기다릴지 진행할지..
 - parameter
   - impl : implicit locking인지.
   - mode: shared인지 exclusive인지
   - heap no: page 안에서 위치가 어딘지
   - ...

// lock_rec_lock 내부 설명
lock/lock0lock.cc:2624
lock_rec_lock_fast() - 아무도 없을거라고 기대하고 빠르게 락 획득 시도
lock_rec_lock_slow() - 락을 잡을려는 누군가가 있는 것 같을때
lock_rec_other_has_conflicting() : 혹시 다른 애가 conflict한 lock 잡고있니?
for loop (line 1452) 도는게 list에서 처음부터 다 보는것
lock_rec_has_to_wait() (line 1456): 나 혹시 기다려야하니??
lock_mode_compatible() (line 901)을 통해 같이 잡을 수 있는지 확인. lock_compatibility_matrix를 통해

// record lock을 주로 부르는 path (read)
row/row0sel.cc:880
row_sel_get_clust_rec()
 - lock_clust_rec_read_check_and_lock()
   - lock_rec_lock()
lock_rec_lock()은 주로 lock_clust_rec_read_check_and_lock() 에서 불릴 것이다.
read-only transaction들을 수행했을 때 문제가 여기서부터 시작될것. lock_mutex_enter()를 부른다.

// lock을 해제하는곳
lock/lock0lock.cc:5197
lock_release()
 - transaction이 잡았던 lock들을 for문을 돌면서 해제한다.
 - lock_req_dequeue_from_page()

// lock 해제를 부르는 곳
trx/trx0trx.cc:1993
trx_commit()
 - trx_commit_low()
  - trx_commit_in_memory()
   - lock_trx_release_locks()
transaction이 잡았던 lock들은 commit할때 다 푼다. Strict 2PL
```

# Benchmark

>## sysbench

- version 1.0.10
- lua script : `/usr/share/sysbench/oltp_read_only.lua`
- create database that sysbench will use `sbtest` and grant privileges to it

```
CREATE DATABASE sbtest;
CREATE USER sbtest@localhost;
GRANT ALL PRIVILEGES ON sbtest.* TO sbtest@localhost
```

- perf install

```
sudo apt-get install linux-tools-generic linux-tools-`uname -r`
```

>## Performance measurement

1. `cd ... /mariadb/run/bin/` and `./mysqld` or `./mysql --defaults-file=../my.cnf`
2. ``` sudo perf record -g -p `pidof mysqld` ```
3. `sysbench --threads=100 --rand-type=uniform --mysql-user=root --mysql-socket=mariadb.sock --db-driver=mysql oltp_read_only.lua prepare`
4. `sysbench --threads=100 --rand-type=uniform --mysql-user=root --mysql-socket=mariadb.sock --db-driver=mysql oltp_read_only.lua run`
5. `cd ... /mariadb/run/bin/` and `./mysqladmin -uroot shutdown`
6. `sudo perf report -g graph --no-children`


---


# References

## MariaDB, sysbench
- [1](https://github.com/akopytov/sysbench)
- [2](https://github.com/akopytov/sysbench/issues/58)
- [3](https://mariadb.org/using-lua-enabled-sysbench/)
- [4](https://mariadb.com/kb/en/library/sysbench-benchmark-setup/)
