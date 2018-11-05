# CMake 最低版本号要求


# 查找目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
#  aux_source_directory(./src DIR_SRCS)


# 指定生成目标
#add_executable(Demo ${DIR_SRCS})





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
target_include_directories(Demo3
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)
