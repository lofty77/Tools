## 介绍
Valgrind工具组提供了一套调试与分析错误的工具包,能够帮助你的程序工作的更加准确，更加快速。这些工具之中最有名的是Memcheck。它能够识别很多C或者C++程序中内存相关的错误，这些错误会导致程序崩溃或者出现不可预知的行为。 

接下来会以最短的篇幅告诉你如何使用Memcheck来识别你写的程序中的内存错误。你可以从用户手册中获取Memcheck的完整文档以及其他工具的使用说明。

## 准备你的程序
在编译程序时开启 `-g` 选项来引入调试信息,这样Memcheck的错误信息中能够准确的显示问题代码的序号。

## 在Memcheck下运行你的程序
如果你的程序按照以下方式运行:  
`myprog arg1 arg2`  
请使用下述命令来执行内存检查:  
`valgrind --leak-check=yes myprog arg1 arg2`  

Memcheck是默认的工具,开启`--leak-check`选项会启动内存泄露检查.  
你的程序会比正常运行慢很多(大概20到30倍),并且会使用更多的内存.Memcheck会记录检测到的内存错误和内存泄露信息.

## 解释Memcheck的输出信息
这是我们的用于示例的C程序代码,其文件名为`a.c`,这段代码中有一个内存错误和内存泄露问题.    

    #include <stdio.h>
    void f()
    {
        int * x = malloc(10 * sizeof(int));
        x[10] = 0;  //problem 1: heap block overrun
                    //problem 2: memory leak -- x not freed
    }
    int main(){
    f();
    return 0;
    }
下面是使用上述C代码生成程序的命令
`gcc -g a.c`  
使用下述命令检查程序中的内存错误:  
`valgrind --leak-check=yes ./a.out`  
大多数的错误信息和下面的一致,下面展示了内存越界的错误:  
> liang.liang@ubuntu:~/code/Algorithms$ valgrind --leak-check=yes ./a.out   
> ==32196== Memcheck, a memory error detector  
> ==32196== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.  
> ==32196== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info  
> ==32196== Command: ./a.out  
> ==32196==   
> ==32196== Invalid write of size 4  
> ==32196==    at 0x400544: f (a.c:5)  
> ==32196==    by 0x40055A: main (a.c:9)  
> ==32196==  Address 0x5204068 is 0 bytes after a block of size 40 alloc'd  
> ==32196==    at 0x4C2DB8F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)  
> ==32196==    **by 0x400537: f (a.c:4)**  
> ==32196==    **by 0x40055A: main (a.c:9)**  
> ==32196==   
> ==32196==   
> ==32196== **HEAP SUMMARY**:  
> ==32196==     in use at exit: 40 bytes in 1 blocks  
> ==32196==   total heap usage: 1 allocs, 0 frees, 40 bytes allocated  
> ==32196==   
> ==32196== 40 bytes in 1 blocks are definitely lost in loss record 1 of 1  
> ==32196==    at 0x4C2DB8F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)  
> ==32196==   by 0x400537: f (a.c:4)
> ==32196==   by 0x40055A: main (a.c:9)
> ==32196==   
> ==32196== **LEAK SUMMARY**:  
> ==32196==    definitely lost: 40 bytes in 1 blocks  
> ==32196==    indirectly lost: 0 bytes in 0 blocks  
> ==32196==      possibly lost: 0 bytes in 0 blocks  
> ==32196==    still reachable: 0 bytes in 0 blocks  
> ==32196==         suppressed: 0 bytes in 0 blocks  

