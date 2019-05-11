# DataWhale SQL 组队打卡学习营【任务一】
# 1.1 MySQL 软件安装及数据库基础

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
