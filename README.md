Microsoft Windows [Version 10.0.22621.2070]
(c) Microsoft Corporation. All rights reserved.

C:\Users\lagad>cd/

C:\>cd xampp

C:\xampp>cd mysql

C:\xampp\mysql>cd bin

C:\xampp\mysql\bin>mysql.exe -u root


Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 10.4.28-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| student            |
| test               |
+--------------------+
6 rows in set (0.001 sec)

MariaDB [(none)]> use student
Database changed

MariaDB [student]> create table customer (Cust_id int not null, Name varchar(20) not null, Country varchar(20) not null, City varchar (20));
Query OK, 0 rows affected (0.019 sec)

MariaDB [student]> desc customer;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| Cust_id | int(11)     | NO   |     | NULL    |       |
| Name    | varchar(20) | NO   |     | NULL    |       |
| Country | varchar(20) | NO   |     | NULL    |       |
| City    | varchar(20) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.006 sec)

MariaDB [student]> alter table customer modify Cust_id int not null UNIQUE;
Query OK, 0 rows affected (0.053 sec)
Records: 0  Duplicates: 0  Warnings: 0

MariaDB [student]> desc customer;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| Cust_id | int(11)     | NO   | PRI | NULL    |       |
| Name    | varchar(20) | NO   |     | NULL    |       |
| Country | varchar(20) | NO   |     | NULL    |       |
| City    | varchar(20) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.005 sec)

MariaDB [student]> CREATE TABLE order_info (Order_id int NOT NULL, Order_num int NOT NULL, Cust_id int, PRIMARY KEY (Order_id),    FOREIGN KEY (Cust_id) REFERENCES personal_info(Cust_id) );

Query OK, 3 rows affected (0.006 sec)

MariaDB [student]>
+-----------+---------+------+-----+---------+-------+
| Field     | Type    | Null | Key | Default | Extra |
+-----------+---------+------+-----+---------+-------+
| Order_id  | int(11) | NO   | PRI | NULL    |       |
| Order_num | int(11) | NO   |     | NULL    |       |
| Cust_id   | int(11) | YES  | MUL | NULL    |       |
+-----------+---------+------+-----+---------+-------+
3 rows in set (0.024 sec)

MariaDB [student]> create table data(id int primary key, name varchar(20),age int);
Query OK, 0 rows affected (0.022 sec)

MariaDB [student]> desc data;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int(11)     | NO   | PRI | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
| age   | int(11)     | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.005 sec)

MariaDB [student]> insert into data(id, name, age)values(700,'ram',19),(701
,'ravi',17),(702,'teja',20);
Query OK, 3 rows affected (0.006 sec)
Records: 3  Duplicates: 0  Warnings: 0

MariaDB [student]> select * from data;
+-----+------+------+
| id  | name | age  |
+-----+------+------+
| 700 | ram  |   19 |
| 701 | ravi |   17 |
| 702 | teja |   20 |
+-----+------+------+
3 rows in set (0.000 sec)

MariaDB [student]> select * from data where name like '%vishnu%';
Empty set (0.000 sec)

MariaDB [student]> select * from data where name like '%teja%';
+-----+------+------+
| id  | name | age  |
+-----+------+------+
| 702 | teja |   20 |
+-----+------+------+
1 row in set (0.000 sec)

MariaDB [student]> select * from data where age in (17);
+-----+------+------+
| id  | name | age  |
+-----+------+------+
| 701 | ravi |   17 |
+-----+------+------+
1 row in set (0.001 sec)

MariaDB [student]> select * from data where age in (16);
Empty set (0.000 sec)

MariaDB [student]> select * from data where age in (age>19);
Empty set (0.000 sec)

MariaDB [student]> select * from data where age in (18,20);
+-----+------+------+
| id  | name | age  |
+-----+------+------+
| 702 | teja |   20 |
+-----+------+------+
1 row in set (0.000 sec)

MariaDB [student]> select * from data where age in (17,20);
+-----+------+------+
| id  | name | age  |
+-----+------+------+
| 701 | ravi |   17 |
| 702 | teja |   20 |
+-----+------+------+
2 rows in set (0.000 sec)

MariaDB [student]> show tables;
+-------------------+
| Tables_in_student |
+-------------------+
| customer          |
| data              |
+-------------------+
2 rows in set (0.001 sec)

MariaDB [student]>
