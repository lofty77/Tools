### which
在PATH 路径下查找命令（查找后就不会继续找了）
```
liang.liang@ubuntu:~/code/test$ which python
/home/liang.liang/anaconda3/bin/python
```

### whereis
这个命令可以用来查找二进制（命令）、源文件、man文件。
与which不同的是这条命令可以是通过文件索引数据库而非PATH来查找的，所以查找的面比which要广。例如：
```
liang.liang@ubuntu:~/code/test$ whereis python
python: /usr/bin/python3.5 /usr/bin/python /usr/bin/python3.5m-config 
/usr/bin/python2.7 /usr/bin/python3.5m /usr/bin/python3.5-config 
/usr/lib/python3.5 /usr/lib/python2.7 /etc/python3.5 
/etc/python /etc/python2.7 /usr/local/lib/python3.5 
/usr/local/lib/python2.7 /usr/include/python3.5 
/usr/include/python3.5m /usr/share/python 
/home/liang.liang/anaconda3/bin/python3.7m 
/home/liang.liang/anaconda3/bin/python 
/home/liang.liang/anaconda3/bin/python3.7 
/home/liang.liang/anaconda3/bin/python3.7-config 
/home/liang.liang/anaconda3/bin/python3.7m-config 
/usr/share/man/man1/python.1.gz

```

### find
查找文件的命令。  
#### 基本格式
    find 路径 -选项 参数 ...

比如： 
    find ./ -name "test"
    
```
liang.liang@ubuntu:~/code/test$ ls
f1  hello_world
liang.liang@ubuntu:~/code/test$ find ./ -name "hello*"
./hello_world
liang.liang@ubuntu:~/code/test$ 

```

### grep
查找文件内容的命令
#### 基本格式
    grep -选项 搜索关键字 文件
```
liang.liang@ubuntu:~/code/test$ ls
f1  hello_world
liang.liang@ubuntu:~/code/test$ grep -r "liang.liang@163" ./
./f1:liang.liang@163
liang.liang@ubuntu:~/code/test$ 
```


### Others
不懂就在linux下 man command  
https://github.com/guodongxiaren/LinuxTool
