## 代码结构
本小节对应的源代码所在目录[Demo3](https://github.com/lofty77/Tools/tree/master/cmake/Demo3)  
大多数情况，源文件和头文件会放在不同的目录下。现在假如把 power 函数单独写进一个名为 MathFunctions.c 的源文件里，使得这个工程变成如下的形式：  
```console
liang.liang@ubuntu:~/code/Tools/cmake/Demo3$ tree
.
├── CMakeLists.txt
├── include
│   └── MathFunctions.h
└── src
    ├── main.cc
    └── MathFunctions.cc

2 directories, 4 files
```
## CMakeLists
这个时候，CMakeLists.txt 可以改成如下的形式：

```cmake
# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)

# Set the project name
project (Demo3)

# Create a sources variable with a link to all cpp files to compile
set(SOURCES
    src/MathFunctions.cc
    src/main.cc
)

# Add an executable with the above sources
add_executable(Demo3 ${SOURCES})

# Set the directories that should be included in the build command for this target
# when running g++ these will be included as -I/directory/path/
# PROJECT_SOURCE_DIR : root directory of the project
target_include_directories(Demo3
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)
```
这里存在如下问题：
* 目前只src 文件只有两个源文件，如果以后新增了若干个，就得针对`CMakeLists.txt`做修改。
修改后的CMakeLists.txt：
```cmake
# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)

# Set the project name
project (Demo3)

aux_source_directory(./src SOURCES)

# Add an executable with the above sources
add_executable(Demo3 ${SOURCES})

# Set the directories that should be included in the build command for this target
# when running g++ these will be included as -I/directory/path/
target_include_directories(Demo3
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)
```
## Building
```console
liang.liang@ubuntu:~/code/Tools/cmake/Demo3$ ls
CMakeLists.txt	CMakeLists.txt.bak  include  src
liang.liang@ubuntu:~/code/Tools/cmake/Demo3$ mkdir build
liang.liang@ubuntu:~/code/Tools/cmake/Demo3$ cd build/
liang.liang@ubuntu:~/code/Tools/cmake/Demo3/build$ cmake ..
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
-- Build files have been written to: /home/liang.liang/code/Tools/cmake/Demo3/build
liang.liang@ubuntu:~/code/Tools/cmake/Demo3/build$ make
Scanning dependencies of target Demo3
[ 33%] Building CXX object CMakeFiles/Demo3.dir/src/MathFunctions.cc.o
[ 66%] Building CXX object CMakeFiles/Demo3.dir/src/main.cc.o
[100%] Linking CXX executable Demo3
[100%] Built target Demo3
liang.liang@ubuntu:~/code/Tools/cmake/Demo3/build$ ./Demo3 3 3
3 ^ 3 is 27
liang.liang@ubuntu:~/code/Tools/cmake/Demo3/build$ 

```
## Note
如果新增文件（source files in /src，head files in /include），No need to modify CMakeLists.txt
