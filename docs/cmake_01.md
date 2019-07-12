## 单个源文件
对于简单的项目，只需要写几行代码就可以了。例如，假设现在我们的项目中只有一个源文件 main.cc ，该程序的用途是计算一个数的指数幂。  
本节对应的源代码所在目录[Demo1](https://github.com/lofty77/Tools/tree/master/cmake/Demo1)
目录结构如下：
```
liang.liang@ubuntu:~/code/Tools/cmake/Demo1$ tree
.
├── CMakeLists.txt
└── main.cc

```

### 编写 CMakeLists.txt
首先编写 CMakeLists.txt 文件，并保存在与 main.cc 源文件同个目录下:  
  
```cmake
# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)
# 项目信息
project (Demo1)
# 指定生成目标
add_executable(Demo main.cc)
```
CMakeLists.txt 的语法比较简单，由命令、注释和空格组成，其中命令是不区分大小写的。符号 `#` 后面的内容被认为是注释。命令由命令名称、小括号和参数组成，参数之间使用空格进行间隔。

对于上面的 CMakeLists.txt 文件，依次出现了几个命令：

- `cmake_minimum_required`：指定运行此配置文件所需的 CMake 的最低版本；  
- `project`：参数值是 Demo1，该命令表示项目的名称是 Demo1 。  
- `add_executable`： 将名为 main.cc 的源文件编译成一个名称为 Demo 的可执行文件。  

### 编译项目
之后，在当前目录执行 `cmake .`，得到 Makefile 后再使用 `make` 命令编译得到 Demo1 可执行文件。

```console
liang.liang@ubuntu:~/code/Tools/cmake/Demo1$ ls
CMakeLists.txt	main.cc
liang.liang@ubuntu:~/code/Tools/cmake/Demo1$ mkdir build
liang.liang@ubuntu:~/code/Tools/cmake/Demo1$ cd build/
liang.liang@ubuntu:~/code/Tools/cmake/Demo1/build$ cmake ..
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
-- Build files have been written to: /home/liang.liang/code/Tools/cmake/Demo1/build
liang.liang@ubuntu:~/code/Tools/cmake/Demo1/build$ ls
CMakeCache.txt	CMakeFiles  cmake_install.cmake  Makefile
liang.liang@ubuntu:~/code/Tools/cmake/Demo1/build$ make
Scanning dependencies of target Demo
[ 50%] Building CXX object CMakeFiles/Demo.dir/main.cc.o
[100%] Linking CXX executable Demo
[100%] Built target Demo
liang.liang@ubuntu:~/code/Tools/cmake/Demo1/build$ ls
CMakeCache.txt	CMakeFiles  cmake_install.cmake  Demo  Makefile
liang.liang@ubuntu:~/code/Tools/cmake/Demo1/build$ ./Demo 
Usage: ./Demo base exponent 
liang.liang@ubuntu:~/code/Tools/cmake/Demo1/build$ ./Demo 3 4
3 ^ 4 is 81
```
