## 源文件&头文件，都放在一个目录下
本小节对应的源代码所在目录[Demo2](https://github.com/lofty77/Tools/tree/master/cmake/Demo2)  
上面的例子只有单个源文件。现在假如把 power 函数单独写进一个名为 MathFunctions.c 的源文件里，使得这个工程变成如下的形式：  
```console
liang.liang@ubuntu:~/code/Tools/cmake/Demo2$ tree
.
├── CMakeLists.txt
├── main.cc
├── MathFunctions.cc
└── MathFunctions.h
```
这个时候，CMakeLists.txt 可以改成如下的形式：
```cmake
# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)
# 项目信息
project (Demo2)
# 指定生成目标
add_executable(Demo main.cc MathFunctions.cc)
````
唯一的改动只是在 `add_executable `命令中增加了一个 MathFunctions.cc 源文件。这样写当然没什么问题，但是如果源文件很多，把所有源文件的名字都加进去将是一件烦人的工作。更省事的方法是使用 `aux_source_directory `命令，该命令会查找指定目录下的所有源文件，然后将结果存进指定变量名。其语法如下：
    
    aux_source_directory(<dir> <variable>)
因此，可以修改 CMakeLists.txt 如下：
```cmake
# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)
# 项目信息
project (Demo2)
# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)
# 指定生成目标
add_executable(Demo ${DIR_SRCS})
```
这样，CMake 会将当前目录所有源文件的文件名赋值给变量 `DIR_SRCS`，再指示变量 `DIR_SRCS`中的源文件需要编译成一个名称为 Demo 的可执行文件。

## Building
``` console
liang.liang@ubuntu:~/code/Tools/cmake/Demo2$ mkdir build
liang.liang@ubuntu:~/code/Tools/cmake/Demo2$ cd build/
liang.liang@ubuntu:~/code/Tools/cmake/Demo2/build$ ls
liang.liang@ubuntu:~/code/Tools/cmake/Demo2/build$ cmake ..
-- The C compiler identification is GNU 5.4.0
-- The CXX compiler identification is GNU 5.4.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/liang.liang/code/Tools/cmake/Demo2/build
liang.liang@ubuntu:~/code/Tools/cmake/Demo2/build$ ls
CMakeCache.txt	CMakeFiles  cmake_install.cmake  Makefile
liang.liang@ubuntu:~/code/Tools/cmake/Demo2/build$ make
Scanning dependencies of target Demo
[ 33%] Building CXX object CMakeFiles/Demo.dir/MathFunctions.cc.o
[ 66%] Building CXX object CMakeFiles/Demo.dir/main.cc.o
[100%] Linking CXX executable Demo
[100%] Built target Demo
liang.liang@ubuntu:~/code/Tools/cmake/Demo2/build$ ./Demo 3 2
3 ^ 2 is 9
```
