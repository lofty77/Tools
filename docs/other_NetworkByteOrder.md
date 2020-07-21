### 参考
https://blog.csdn.net/anningzte/article/details/52125665  

### 大端小端问题总结
- 大端小端的前提是多字节序存储（例如int类型，对于32位机器，int 是4个字节）
- 只要记住小端就行，大端就是小端的反向
- 小端 ： 数据的低位（以字节为单位）存放在内存的低位
- 大端 ： 数据的低位存放在内存的高位

### 测试大端小端的代码

```c
  int i = 0x12345445;     //四字节
  char *p = (char *)&i;   //将整型变量地址  的  首地址（第一个字节，即低地址）赋给指针p
  printf("%x %x\n",*p,*(p+1));
```

也可以用union来测试，主要思路是union 中可以定义一个int a 及 一个数组 char b[4].
数组的特点是 b[0] b[1] b[2] b[3] 是内存地址从低位到高位排序。通过读取a 就可以判断是大端还是小端：
如果低位的数组在变量a的低位，就是小端。
如果低位的数组在变量a的高位，就是大端。

https://www.cnblogs.com/YiRanYouQingFeng/p/9657850.html

```C
#include <stdio.h>

union var{
        char c[4];
        int i;
};
	
int main () {
	printf("hello https://tool.lu/\n");
	
	
	union var data;
        data.c[0] = 0x04;//因为是char类型，数字不要太大，算算ascii的范围~
        data.c[1] = 0x03;//写成16进制为了方便直接打印内存中的值对比
        data.c[2] = 0x02;
        data.c[3] = 0x01;//数组中下标低的，地址也低，按地址从低到高，内存内容依次为：04,03,02,11。总共四字节！
//而把四个字节作为一个整体（不分类型，直接打印十六进制），应该从内存高地址到低地址看，0x11020304，低位04放在低地址上。
        printf("%x\n",data.i);
	
	
	
	return 0;
}
```
