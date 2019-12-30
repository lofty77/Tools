## linux
### 使用apt 安装MySQL

删除MySQL前，先删除/var/lib/mysql和/etc/mysql，如下代码所示：
``` linux
sudo rm /var/lib/mysql/ -R  
sudo rm /etc/mysql/ -R  
sudo apt-get autoremove mysql* --purge  
sudo apt-get remove apparmor  
sudo apt-get install mysql-server mysql-common 
```

登录MySQL server
```linux
liang.liang@ubuntu:~$ mysql -uroot -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.7.28-0ubuntu0.16.04.2 (Ubuntu)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases
    -> 
```
查看mysql进程是否在运行
```linux
liang.liang@ubuntu:~$ service mysql status
● mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en
   Active: active (running) since 四 2019-12-26 06:07:37 PST; 28min ago
 Main PID: 12533 (mysqld)
   CGroup: /system.slice/mysql.service
           └─12533 /usr/sbin/mysqld

```
### 查看支持哪些数据库
```sql
mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test2              |
| yiibaidb           |
+--------------------+
6 rows in set (0.00 sec)

```

### 创建一个数据库
```
mysql> create database student;
Query OK, 1 row affected (0.01 sec)

```

### 选一个数据库
```sql
mysql> use test2;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> 
```
