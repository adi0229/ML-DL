~~~~
Last login: Wed May 22 21:49:04 on ttys003
adi0229 (adi0229 *) ~
$ mysql
-bash: mysql: command not found
adi0229 (adi0229 *) ~
$ mysqladmin --version
-bash: mysqladmin: command not found
adi0229 (adi0229 *) ~
$ alias mysql=/usr/local/mysql/bin/mysql
adi0229 (adi0229 *) ~
$ alias mysqladmin=/usr/local/mysql/bin/mysqladmin
adi0229 (adi0229 *) ~
$ PATH="$PATH":/usr/local/mysql/bin
adi0229 (adi0229 *) ~
$ mysqladmin --version
/usr/local/mysql/bin/mysqladmin  Ver 8.0.16 for macos10.14 on x86_64 (MySQL Community Server - GPL)
adi0229 (adi0229 *) ~
$ mysql
ERROR 1045 (28000): Access denied for user 'adi0229'@'localhost' (using password: NO)
adi0229 (adi0229 *) ~
$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 8.0.16 MySQL Community Server - GPL

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database muggle
    -> ;
Query OK, 1 row affected (0.15 sec)

mysql> show database;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'database' at line 1
mysql> show datbases;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'datbases' at line 1
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| Email              |
| information_schema |
| muggle             |
| mysql              |
| performance_schema |
| sys                |
| yiibaidb           |
+--------------------+
7 rows in set (0.15 sec)

mysql> use muggle
Database changed
mysql> create table commment (
    -> amt int not null ,
    -> id varchar not null,
    -> timestamp int not null,
    -> show datbases;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'not null,
timestamp int not null,
show datbases' at line 3
mysql> create table commment (
    -> amt int not null,
    -> id varchar not null,
    -> timestamp int not null,
    -> score int not null,
    -> primary key (id)
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'not null,
timestamp int not null,
score int not null,
primary key (id)
)' at line 3
mysql> create table commment (
    -> amt int not null,
    -> id varchar(255) not null,
    -> timestamp int not null,
    -> score int not null,
    -> primary key (id)
    -> );
Query OK, 0 rows affected (0.16 sec)

mysql> insert into commment
    -> values(20,'713223379','1556875196',5);
Query OK, 1 row affected (0.03 sec)

mysql> insert into commment
    -> values(5,'713221831','1556875076',61);
Query OK, 1 row affected (0.01 sec)

mysql> insert into commment
    -> values(5,'713231701',1556875076,5);
Query OK, 1 row affected (0.01 sec)

mysql> select * from commment;
+-----+-----------+------------+-------+
| amt | id        | timestamp  | score |
+-----+-----------+------------+-------+
|   5 | 713221831 | 1556875076 |    61 |
|  20 | 713223379 | 1556875196 |     5 |
|   5 | 713231701 | 1556875076 |     5 |
+-----+-----------+------------+-------+
3 rows in set (0.00 sec)

mysql> update comment set timetamp = 1556875196 where timestamp = '1556875196';
ERROR 1146 (42S02): Table 'muggle.comment' doesn't exist
mysql> updata commment set timetamp = 1556875196 where timestamp = '1556875196';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'updata commment set timetamp = 1556875196 where timestamp = '1556875196'' at line 1
mysql> update comment set timetamp = 1556875196 where timestamp = '1556875196'' at line 1;
    '> ;
    '>
    '>
    '> ;
    '> ;
    '> ??
    '> mysql
    '> '
    -> ;
ERROR 1146 (42S02): Table 'muggle.comment' doesn't exist
mysql> rename commment to comment;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'commment to comment' at line 1
mysql> rename table commment to comment;
Query OK, 0 rows affected (0.06 sec)

mysql> update comment set timestamp = 1556875196 where timestamp = '1556875196';
Query OK, 0 rows affected (0.01 sec)
Rows matched: 1  Changed: 0  Warnings: 0

mysql> update comment set timestamp = 1556875076  where timestamp = '1556875076';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 2  Changed: 0  Warnings: 0

mysql> select * from comment;
+-----+-----------+------------+-------+
| amt | id        | timestamp  | score |
+-----+-----------+------------+-------+
|   5 | 713221831 | 1556875076 |    61 |
|  20 | 713223379 | 1556875196 |     5 |
|   5 | 713231701 | 1556875076 |     5 |
+-----+-----------+------------+-------+
3 rows in set (0.00 sec)

mysql> select * from comment where score = 5;
+-----+-----------+------------+-------+
| amt | id        | timestamp  | score |
+-----+-----------+------------+-------+
|  20 | 713223379 | 1556875196 |     5 |
|   5 | 713231701 | 1556875076 |     5 |
+-----+-----------+------------+-------+
2 rows in set (0.00 sec)

mysql> mysqldump -u root -p muggle comment>muggle_comment.sql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysqldump -u root -p muggle comment>muggle_comment.sql' at line 1
mysql> mysqldump -u root -p muggle comment > muggle_comment.sql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysqldump -u root -p muggle comment > muggle_comment.sql' at line 1
mysql> mysqldump -u root -p muggle comment> muggle_comment.sql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysqldump -u root -p muggle comment> muggle_comment.sql' at line 1
mysql> mysqldump -u root -p h65sj7979 muggle > muggle.sql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysqldump -u root -p h65sj7979 muggle > muggle.sql' at line 1
mysql> mysqldump -u root -p h65sj7979 muggle > muggle.sql
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysqldump -u root -p h65sj7979 muggle > muggle.sql' at line 1
mysql> quit()
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'quit()' at line 1
mysql> exit()
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'exit()' at line 1
mysql> \q
Bye
adi0229 (adi0229 *) ~
$ cd /Users/apple/Desktop
adi0229 (adi0229 *) Desktop
$ mkdir muggle
adi0229 (adi0229 *) Desktop
$ cd muggle
adi0229 (adi0229 *) muggle
$ mysqldump -u root -p mugglee>muggle.sql
Enter password:
mysqldump: Got error: 1049: Unknown database 'mugglee' when selecting the database
adi0229 (adi0229 *) muggle
$ mysqldump -u root -p muggle>muggle.sql
Enter password:
adi0229 (adi0229 *) muggle
$
~~~~
