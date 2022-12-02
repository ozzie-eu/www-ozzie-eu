---
title: "MySQL vs MariaDB: Performance on Bug Management "
date: 2022-12-02T12:00:34Z
tags:
- mysql
- mariadb
categories:
- backend
draft: false
---
Cleaning up the e-mail inbox, I discovered a 7-year-old bug report I made on the MySQL bugs database: [Bug #79497](https://bugs.mysql.com/bug.php?id=79497). Someone verified it on the same day. It has been simmering there, journeying into oblivion.
An optimistic guess might be that it is solved, but they forgot to close it.
On a quick revisit to the topic, I used an Ubuntu terminal environment on Windows (WSL), installed MySQL 8 (in mind that the bug report was on version 5.7), and imported the same [demo database](https://dev.mysql.com/doc/employee/en/employees-installation.html).
To my surprise, the bug is still there, despite being evaluated at the time as LEVEL S2: SERIOUS.
At the same time as the bug report on MySQL, I also sent it to the MariaDB [bug database](https://jira.mariadb.org/browse/MDEV-9232).
It's not solved on either RDBMS, but at least MariaDB is keeping track on updates: on MySQL. 
Maybe if Oracle fixed this on MySQL, MariaDB would get the source and patch theirs the same way. 

- MySQL: [https://github.com/mysql/mysql-server](https://github.com/mysql/mysql-server)
- MariaDB: [https://github.com/MariaDB/server](https://github.com/MariaDB/server)


