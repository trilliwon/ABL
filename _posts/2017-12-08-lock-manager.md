---
layout: post
title:  "[In progress] MariaDB Scalable Lock Manager"
date:   2017-12-08 20:00:00 +0900
categories: concurrent_programming
permalink: /lock_manager/
---

# TODO

- [x] benchmark (sysbench, perf)
- [ ] understand related code [/storage/innobase/lock](https://github.com/MariaDB/server/tree/10.3/storage/innobase/lock)
- [ ] design for read-only transaction
- [ ] implementation for read-only transaction
- [ ] benchmark (sysbench, perf)
- [ ] design for read/write transaction
- [ ] implementation for read/write transaction
- [ ] benchmark (sysbench, perf)


# Benchmark

## sysbench

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

# Performance measurement

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
