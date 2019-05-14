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


Ref: [sql语句中GROUP BY 和 HAVING的使用 count()](https://hejiajunsh.iteye.com/blog/1833847)
~~~~
mysql> select count(class) from courses
    -> ;
+--------------+
| count(class) |
+--------------+
|           10 |
+--------------+
1 row in set (0.04 sec)

mysql> select count(student) from courses group by class
    -> ;
+----------------+
| count(student) |
+----------------+
|              7 |
|              1 |
|              1 |
|              1 |
+----------------+
4 rows in set (0.01 sec)

mysql> select class from courses group by class having count(student) > 5;
+-------+
| class |
+-------+
| Math  |
+-------+
1 row in set (0.01 sec)
~~~~

看了 note 之后

>学生在每个课中不应被重复计算。

查询去重统计语法 [mysql count distinct 统计结果去重](https://my.oschina.net/jiec/blog/471730)

~~~~
mysql> select count(distinct student) from courses group by class
    -> ;
+-------------------------+
| count(distinct student) |
+-------------------------+
|                       1 |
|                       1 |
|                       1 |
|                       6 |
+-------------------------+
4 rows in set (0.01 sec)
~~~~

项目四：交换工资（难度：简单）


创建一个 salary表，如下所示，有m=男性 和 f=女性的值 。


例如:

| id | name | sex | salary |
|----|------|-----|--------|
| 1  | A    | m   | 2500   |
| 2  | B    | f   | 1500   |
| 3  | C    | m   | 5500   |
| 4  | D    | f   | 500    |

之前的 Query，全用小写，深感不符合 StyleGuide，看了 [SQL编程格式的优化建议](https://zhuanlan.zhihu.com/p/27466166)

~~~~
mysql> insert into salary value('1','A','m',2500);
Query OK, 1 row affected (0.00 sec)

mysql> insert into salary value('2','B','f',1500);
Query OK, 1 row affected (0.01 sec)

mysql> insert into salary value('3','C','m',5500);
Query OK, 1 row affected (0.00 sec)

mysql> insert into salary value('4','D','f',500);
Query OK, 1 row affected (0.00 sec)

mysql> select * from salary
    -> ;
+----+------+------+--------+
| id | name | sex  | salary |
+----+------+------+--------+
|  1 | A    | m    |   2500 |
|  2 | B    | f    |   1500 |
|  3 | C    | m    |   5500 |
|  4 | D    | f    |    500 |
+----+------+------+--------+
4 rows in set (0.00 sec)
~~~~


~~~~
mysql> UPDATE salary
    -> SET sex=
    -> CASE sex
    -> WHEN 'm'
    -> THEN 'f'
    -> ELSE 'm'
    -> END;
Query OK, 4 rows affected (0.01 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> select * from salary;
+----+------+------+--------+
| id | name | sex  | salary |
+----+------+------+--------+
|  1 | A    | f    |   2500 |
|  2 | B    | m    |   1500 |
|  3 | C    | f    |   5500 |
|  4 | D    | m    |    500 |
+----+------+------+--------+
4 rows in set (0.00 sec)
~~~~
如何使用SQL语句交换男女性别
https://blog.csdn.net/u012351768/article/details/75529368

## 2.2 MySQL 基础 （三）- 表联结
### #学习内容#
* MySQL别名
* INNER JOIN
* LEFT JOIN
* CROSS JOIN
* 自连接
* UNION
* 以上几种方式的区别和联系
### #作业#

项目五：组合两张表 （难度：简单）

在数据库中创建表1和表2，并各插入三行数据（自己造）

表1: Person

+-------------+---------+
| 列名         | 类型     |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+

PersonId 是上表主键

表2: Address

+-------------+---------+
| 列名         | 类型    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+

AddressId 是上表主键

编写一个 SQL 查询，满足条件：无论 person 是否有地址信息，都需要基于上述两表提供 person 的以下信息：FirstName, LastName, City, State

~~~~
mysql> CREATE TABLE Person (
    -> PersonId INT NOT NULL PRIMARY KEY,
    -> FirstName VARCHAR(255),
    -> LastName VARCHAR(255)
    -> );
Query OK, 0 rows affected (0.08 sec)

mysql> insert into Person value('1','Jerry','Huang');
Query OK, 1 row affected (0.02 sec)

mysql> insert into Person value('2','Zhang','Fei');
Query OK, 1 row affected (0.00 sec)

mysql> insert into Person value('3','Cris','Paul');
Query OK, 1 row affected (0.00 sec)

mysql> select * from Person
    -> ;
+----------+-----------+----------+
| PersonId | FirstName | LastName |
+----------+-----------+----------+
|        1 | Jerry     | Huang    |
|        2 | Zhang     | Fei      |
|        3 | Cris      | Paul     |
+----------+-----------+----------+
3 rows in set (0.00 sec)
~~~~

~~~~
mysql> CREATE TABLE Address (
    -> AddressId INT NOT NULL PRIMARY KEY,
    -> PersonId INT NOT NULL PRIMARY KEY,
    -> City VARCHAR(255),
    -> State VARCHAR(255)
    -> );
ERROR 1068 (42000): Multiple primary key defined
mysql> CREATE TABLE Address (
    -> AddressId INT NOT NULL PRIMARY KEY,
    -> PersonId INT NOT NULL ,
    -> City VARCHAR(255),
    -> State VARCHAR(255)
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> insert into Person value('1','1','BeiJing','BeiJing');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into Person value('2','2','NanJing','Jiangsu');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into Person value('3','3','Guangxi','Nanning');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into Address value('1','1','BeiJing','BeiJing');
Query OK, 1 row affected (0.01 sec)

mysql> insert into Address value('2','2','NanJing','Jiangsu');
Query OK, 1 row affected (0.01 sec)

mysql> insert into Address value('3','3','Guangxi','Nanning');
Query OK, 1 row affected (0.00 sec)

mysql> select * from Address;
+-----------+----------+---------+---------+
| AddressId | PersonId | City    | State   |
+-----------+----------+---------+---------+
|         1 |        1 | BeiJing | BeiJing |
|         2 |        2 | NanJing | Jiangsu |
|         3 |        3 | Guangxi | Nanning |
+-----------+----------+---------+---------+
3 rows in set (0.00 sec)
~~~~



语法：select 表1.字段 [as 别名],表n.字段 from 表1 [别名],表n where 条件;

Ref：12.8.3 多表联合查询 http://mysql.phpxy.com/75314

~~~~
mysql> SELECT Person.PersonId,Person.FirstName,Person.LastName,Address.City,Address.State
    -> FROM Person, Address
    -> WHERE Person.PersonId = Address.PersonId;
+----------+-----------+----------+---------+---------+
| PersonId | FirstName | LastName | City    | State   |
+----------+-----------+----------+---------+---------+
|        1 | Jerry     | Huang    | BeiJing | BeiJing |
|        2 | Zhang     | Fei      | NanJing | Jiangsu |
|        3 | Cris      | Paul     | Guangxi | Nanning |
+----------+-----------+----------+---------+---------+
3 rows in set (0.00 sec)
~~~~


项目六：删除重复的邮箱（难度：简单）

编写一个 SQL 查询，来删除 email 表中所有重复的电子邮箱，重复的邮箱里只保留 **Id ***最小 *的那个。

+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+

Id 是这个表的主键。

例如，在运行你的查询语句之后，上面的 Person表应返回以下几行:

+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | a@b.com |
| 2  | c@d.com  |
+----+------------------+


~~~~

~~~~
