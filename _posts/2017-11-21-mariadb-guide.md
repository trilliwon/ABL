---
layout: post
title:  "Mariadb Guide"
date:   2017-11-21 20:00:00 +0900
category: mariaDB
---

## [Installation](https://downloads.mariadb.org/mariadb/repositories/#mirror=kaist&distro=Ubuntu&distro_release=xenial--ubuntu_xenial&version=10.2)

- `sudo apt-get update`
- `sudo apt-get install mariadb-server`


## Version check

- `mysqladmin --version`

## Execution

- `mysql -u root -p`

## [Starting and Stopping MariaDB](https://mariadb.com/kb/en/library/starting-and-stopping-mariadb-automatically/)

- `mysql.server start`
- `mysql.server stop`

## Create a user account

- `'newusername'@'localhost' IDENTIFIED BY 'userpassword';`

## [mariadb.com](https://mariadb.com/kb/en/library/training-tutorials/)
