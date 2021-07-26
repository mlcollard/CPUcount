# @file CMakeLists.txt
# 
# CMake files for CPUCount

# Can be run by any version of CMake >= this
cmake_minimum_required(VERSION 3.16)

# project info
project(CPUCount)

# C++17 standard
set(CMAKE_CXX_STANDARD 11)

# Source files for the main program CPUCount
set(SOURCE CPUCount_u.cpp CPUCount.cpp)

# CPUCount application
add_executable(CPUCount ${SOURCE})
target_include_directories(CPUCount PRIVATE .)

# Turn on warnings
if (MSVC)
    # warning level 4
    add_compile_options(/W4)
else()
    # standard warnings
    add_compile_options(-Wall)
endif()

# Demo run command
add_custom_target(run
        COMMENT "Run demo"
        COMMAND ./CPUCount 
        DEPENDS CPUCount
        USES_TERMINAL
        WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)
