https://blog.csdn.net/anningzte/article/details/52125665  

大端小端问题总结
- 大端小端的前提是多字节序存储（例如int类型，对于32位机器，int 是4个字节）
- 只要记住小端就行，大端就是小端的反向
- 小端 ： 数据的低位（以字节为单位）存放在内存的低位
- 大端 ： 数据的低位存放在内存的高位

测试大端小端的代码

```c
  int i = 0x12345445;     //四字节
  char *p = (char *)&i;   //将整型变量地址  的  首地址（第一个字节，即低地址）赋给指针p
  printf("%x %x\n",*p,*(p+1));
```

也可以用union来测试，主要思路是union 中可以定义一个int a 及 一个数组 char b[4].
数组的特点是 b[0] b[1] b[2] b[3] 是地址低位到高位
通过读取a 就可以判断是大端还是小端
https://www.cnblogs.com/YiRanYouQingFeng/p/9657850.html
