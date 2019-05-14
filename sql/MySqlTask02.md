【任务二】

2.1 MySQL 基础 （二）- 表操作
 
#学习内容#

1. MySQL表数据类型

2. 用SQL语句创建表

- 语句解释
- 设定列类型 、大小、约束
- 设定主键

3. 用SQL语句向表中添加数据

- 语句解释
- 多种添加方式（指定列名；不指定列名）

4. 用SQL语句删除表

- 语句解释
- DELETE
- DROP
- TRUNCATE
- 不同方式的区别

5. 用SQL语句修改表

- 修改列名
- 修改表中数据
- 删除行
- 删除列
- 新建列
- 新建行

### #作业#

项目三：超过5名学生的课（难度：简单）


创建如下所示的courses 表 ，有: student (学生) 和 class (课程)。


例如,表:

+---------+------------+

| student | class      |
+---------+------------+
| A       | Math       |
| B       | English    |
| C       | Math       |
| D       | Biology    |
| E       | Math       |
| F       | Computer   |
| G       | Math       |
| H       | Math       |
| I       | Math       |
| A      | Math       |
+---------+------------+

~~~~

mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| Email              |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| yiibaidb           |
+--------------------+
6 rows in set (0.13 sec)

mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> create table courses (student varchar(5) not null,
    -> class varchar(20) not null );
Query OK, 0 rows affected (0.24 sec)

mysql>
mysql> insert into courses value('A','Math');
Query OK, 1 row affected (0.01 sec)

mysql> select * from courses
    -> ;
+---------+-------+
| student | class |
+---------+-------+
| A       | Math  |
+---------+-------+
1 row in set (0.00 sec)

mysql> insert into courses value('B','English');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('C','Math');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('D','Biology');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('E','Math');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('F','Computer');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('G','Math');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('H','Math');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('I','Math');
Query OK, 1 row affected (0.00 sec)

mysql> insert into courses value('A','Math');
Query OK, 1 row affected (0.00 sec)
mysql> select * from courses;
+---------+----------+
| student | class    |
+---------+----------+
| A       | Math     |
| B       | English  |
| C       | Math     |
| D       | Biology  |
| E       | Math     |
| F       | Computer |
| G       | Math     |
| H       | Math     |
| I       | Math     |
| A       | Math     |
+---------+----------+
10 rows in set (0.00 sec)
~~~~


编写一个 SQL 查询，列出所有超过或等于5名学生的课。


