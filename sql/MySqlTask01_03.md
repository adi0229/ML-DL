# DataWhale SQL 组队打卡学习营【任务一】
## 1.1 MySQL 软件安装及数据库基础

- 官网下载-> Mac 8.0.15 社区版：https://dev.mysql.com/downloads/mysql/
  - 128G 小容量硬盘，为了省空间，先下载了`mysql-test-8.0.16-macos10.14-x86_64.tar.gz`，解压出来是一堆文件，不知道如何安装。
  - [mac 安装mysql详细教程](https://www.jianshu.com/p/07a9826898c0)，下载 dmg 文件
- [安装](https://dev.mysql.com/doc/refman/8.0/en/osx-installation.html)

选择默认的`Strong password Encryption`，基于`SHA256`的授权方法。
 ~~~~
adi0229 (adi0229 *) ~
$ alias mysql=/usr/local/mysql/bin/mysql
adi0229 (adi0229 *) ~
$ alias mysqladmin=/usr/local/mysql/bin/mysqladmin
adi0229 (adi0229 *) ~
$ PATH="$PATH":/usr/local/mysql/bi
~~~~
~~~~
# 登录出错
$ mysqladmin --version
/usr/local/mysql/bin/mysqladmin  Ver 8.0.16 for macos10.14 on x86_64 (MySQL Community Server - GPL)
adi0229 (adi0229 *) ~
$ mysql
ERROR 1045 (28000): Access denied for user 'adi0229'@'localhost' (using password: NO)
~~~~ 
搜到一篇博文，[解决MySQL登录ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using passwor)问题](https://blog.csdn.net/lisongjia123/article/details/57418989)，其中步骤太繁琐，重新输入密码，成功登录。
~~~~
# 登录成功
$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 12
Server version: 8.0.16 MySQL Community Server - GPL

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

~~~~ 

~~~~
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.04 sec)
~~~~

## 1.2 MySQL 基础 （一）- 查询语句

### 1.2.1 导入示例数据库  https://www.yiibai.com/mysql/how-to-load-sample-database-into-mysql-database-server.html
~~~~
mysql> select city,phone,country from `offices`;
+---------------+------------------+-----------+
| city          | phone            | country   |
+---------------+------------------+-----------+
| San Francisco | +1 650 219 4782  | USA       |
| Boston        | +1 215 837 0825  | USA       |
| NYC           | +1 212 555 3000  | USA       |
| Paris         | +33 14 723 4404  | France    |
| Beijing       | +86 33 224 5000  | China     |
| Sydney        | +61 2 9264 2451  | Australia |
| London        | +44 20 7877 2041 | UK        |
+---------------+------------------+-----------+
7 rows in set (0.00 sec)

mysql> select city from `offices`
    ->
    -> ;
+---------------+
| city          |
+---------------+
| San Francisco |
| Boston        |
| NYC           |
| Paris         |
| Beijing       |
| Sydney        |
| London        |
+---------------+
7 rows in set (0.00 sec)

mysql> select city,country from `offices`;
+---------------+-----------+
| city          | country   |
+---------------+-----------+
| San Francisco | USA       |
| Boston        | USA       |
| NYC           | USA       |
| Paris         | France    |
| Beijing       | China     |
| Sydney        | Australia |
| London        | UK        |
+---------------+-----------+
7 rows in set (0.00 sec)
~~~~

### 1.2.2 SQL是什么？MySQL是什么？

SQL(Structured Query Language)维基百科定义：

>SQL 全名是结构化查询语言，是用于数据库中的标准数据查询语言，IBM 公司最早使用在其开发的数据库系统中。1986年10月，美国国家标准学会 对 SQL 进行规范后，以此作为关系式数据库管理系统的标准语言，1987年得到国际标准组织的支持下成为国际标准。不过各种通行的数据库系统在其实践过程中都对SQL 规范作了某些编改和扩充。所以，实际上不同数据库系统之间的SQL不能完全相互通用。
http://zh.wikipedia.org/zh-cn/SQL

MySQL是甲骨文公司旗下的关系型数据库管理系统。
https://www.wikiwand.com/zh-cn/MySQL

### 1.2.9. SQL代码规范

[SQL编程格式的优化建议] [https://zhuanlan.zhihu.com/p/27466166](https://zhuanlan.zhihu.com/p/27466166)
[SQL Style Guide] [https://www.sqlstyle.guide/](https://www.sqlstyle.guide/)

# 作业：项目 1

参考：MySQL 教程 http://www.runoob.com/mysql/mysql-tutorial.html

~~~~
mysql> CREATE TABLE email (
    -> ID INT NOT NULL PRIMARY KEY,
    -> Email VARCHAR(255)
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO email VALUES('1','a@b.com');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO email VALUES('2','c@d.com');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO email VALUES('3','a@b.com');
Query OK, 1 row affected (0.00 sec)

mysql> select * from `Email`
    -> ;
+----+---------+
| ID | Email   |
+----+---------+
|  1 | a@b.com |
|  2 | c@d.com |
|  3 | a@b.com |
+----+---------+
3 rows in set (0.00 sec)
~~~~


~~~~
mysql> CREATE TABLE World (
    -> name VARCHAR(50) NOT NULL,
    -> continent VARCHAR(50) NOT NULL,
    -> area INT NOT NULL,
    -> population INT NOT NULL,
    -> gdp INT NOT NULL
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO World
    ->   VALUES('Afghanistan','Asia',652230,25500100,20343000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO World
    ->   VALUES('Albania','Europe',28748,2831741,12960000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO World
    ->   VALUES('Algeria','Africa',2381741,37100000,188681000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO World
    ->   VALUES('Andorra','Europe',468,78115,3712000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO World
    ->   VALUES('Angola','Africa',1246700,20609294,100990000);
Query OK, 1 row affected (0.00 sec)

mysql> select * from `World`
    -> ；
    -> ;
+-------------+-----------+---------+------------+-----------+
| name        | continent | area    | population | gdp       |
+-------------+-----------+---------+------------+-----------+
| Afghanistan | Asia      |  652230 |   25500100 |  20343000 |
| Albania     | Europe    |   28748 |    2831741 |  12960000 |
| Algeria     | Africa    | 2381741 |   37100000 | 188681000 |
| Andorra     | Europe    |     468 |      78115 |   3712000 |
| Angola      | Africa    | 1246700 |   20609294 | 100990000 |
+-------------+-----------+---------+------------+-----------+
5 rows in set (0.00 sec)
~~~~

