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
