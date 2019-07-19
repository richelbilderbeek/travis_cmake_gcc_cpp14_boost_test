cmake_minimum_required (VERSION 2.6)
project (travis_cmake_gcc_cpp14)
add_executable(travis_cmake_gcc_cpp14 main.cpp)

# C++14
set_property(TARGET travis_cmake_gcc_cpp14 PROPERTY CXX_STANDARD 14)
set_property(TARGET travis_cmake_gcc_cpp14 PROPERTY CXX_STANDARD_REQUIRED ON)

# Boost with Boost.Test
find_package(Boost REQUIRED COMPONENTS unit_test_framework) 
include_directories(${Boost_INCLUDE_DIRS}) 
