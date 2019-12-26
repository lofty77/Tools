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

登录MySQL测试，如下代码所示：
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
