cmake_minimum_required (VERSION 2.6)
project (travis_cmake_gcc_cpp14)

# The normal executable
add_executable(travis_cmake_gcc_cpp14_boost_test main.cpp my_functions.cpp)

# The executable that runs the tests
add_executable(travis_cmake_gcc_cpp14_boost_test_test main_test.cpp my_functions.cpp my_functions_test.cpp)

# C++14
set_property(TARGET travis_cmake_gcc_cpp14_boost_test PROPERTY CXX_STANDARD 14)
set_property(TARGET travis_cmake_gcc_cpp14_boost_test PROPERTY CXX_STANDARD_REQUIRED ON)
set_property(TARGET travis_cmake_gcc_cpp14_boost_test_test PROPERTY CXX_STANDARD 14)
set_property(TARGET travis_cmake_gcc_cpp14_boost_test_test PROPERTY CXX_STANDARD_REQUIRED ON)

# Boost with Boost.Test
find_package(Boost REQUIRED COMPONENTS unit_test_framework) 
include_directories(${Boost_INCLUDE_DIRS}) 

# Only test needs Boost.Test
target_link_libraries(travis_cmake_gcc_cpp14_boost_test_test ${Boost_LIBRARIES})
